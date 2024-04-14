created:: 2024-04-14 10:00
status:: #zettel/permanent 
tags::  #clean-architecture #solid
## Introdução
Em resumo, esse principio descreve que um *artefato de software deve estar aberto para extensão e fechados para modificação.* Quando uma extensão simples no comportamento do software trás uma mudança massiva no código, é porque esse principio foi provavelmente violado.
## Como funciona
Para projetar em nível arquitetural esse principio, uma forma de organizar os componentes é entender primeiro, como, por que e quando da mudança, para assim organizarmos os componentes seguindo uma hierarquia de componentes. *Os componentes de nível mais alto são protegidos de mudanças na hierarquia mais baixa*.

Para conseguir respeitar bem esse principio é importante aplicar [[Inversão de Dependência]] para que o código siga um controle direcional, sem uma camada inferior depender diretamente de uma camada superior.

As dependências transitivas violam o principio de que as entidades de software não devem depender diretamente de coisas que não são usadas diretamente.

### Explicação com código
**Exemplo 1:** Esse primeiro exemplo de demonstração mostra como a violação desse princípio ocorre:
```js
class Footballer {
  constructor(name, age, role) {
    this.name = name;
    this.age = age;
    this.role = role;
  }
  getFootballerRole() {
    switch (this.role) {
      case 'goalkeeper':
        console.log(`The footballer, ${this.name} is a goalkeeper`);
        break;
      case 'defender':
        console.log(`The footballer, ${this.name} is a defender`);
        break;
      case 'midfielder':
        console.log(`The footballer, ${this.name} is a midfielder`);
        break;
      case 'forward':
        console.log(`The footballer, ${this.name} plays in the forward line`);
        break;
      default:
        throw new Error(`Unsupported animal type: ${this.type}`);
    }
  }
}

const kante = new Footballer('Ngolo Kante', 31, 'midfielder');
const hazard = new Footballer('Eden Hazard', 32, 'forward');

kante.getFootballerRole();
hazard.getFootballerRole();
```
Para que possamos extender a função `getFootballerRole()`, precisamos modifica-la, o que já viola o *OCP*.

Para que essa violação não ocorra, é preciso quebrar essa classe em novas sub classes. Onde a classe de menor nível é a que possui maior nível de abstração, segue o código de como ficaria essa classe:
```js
class Footballer {
  constructor(name, age, role) {
    this.name = name;
    this.age = age;
    this.role = role;
  }
  getRole() {
    return this.role;
  }
}
```

Agora, cada *role* vai possuir sua classe:

```js
class GoalkeeperRole extends Footballer {
  getRole() {
    return 'goalkeeper';
  }
}

class DefenderRole extends Footballer {
  getRole() {
    return 'defender';
  }
}

class MidfieldRole extends Footballer {
  getRole() {
    return 'midfielder';
  }
}

class ForwardRole extends Footballer {
  getRole() {
    return 'forward';
  }
}
```

**Exemplo 2:** Um outro exemplo mais simples, seria esse:
```js
function calculatePrice(price, discount) {
  if (discount === '10%') {
    return price * 0.9;
  } else if (discount === '20%') {
    return price * 0.8;
  } else if (discount === '30%') {
    return price * 0.7;
  } else {
    throw new Error('Invalid discount');
  }
}

const discountedPrice = calculatePrice(100, '10%');
console.log(`Your discounted price is ${discountedPrice}`); //  The discount you get is 90
```
Repare que o OCP está sendo violado, uma vez que o desconto aplicado está diretamente implementado na classe que calcula o valor. 
*Vamos refatorar esse código:*
```js
const discounts = {
  '10%': 0.9,
  '20%': 0.8,
  '30%': 0.7,
};
function calculatePrice(price, discountType) {
  const discount = discounts[discountType];
  if (discount === undefined) {
    throw new Error('Invalid discount');
  }
  return price * discount;
}
const discountedPrice = calculatePrice(100, '30%');
console.log(`Your discounted price is $${discountedPrice}`);
```
Repare que nesse momento, somos capazes de extender a função `calculatePrice()` sem precisar modifica-la, só precisamos adicionar novos valores na própria constante *discounts*.
# References 
- [[Clean Architecture]]