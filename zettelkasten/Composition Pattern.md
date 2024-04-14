# Composition pattern
created:: 2024-04-14 10:02
status:: #zettel/fleeting
tags:: #pattern 
## O que é?
É um princípio de design que enfatiza a composição de componentes para criar funcionalidades complexas, ao invés de herdar de classes ou componentes existentes. 
### Principais Pontos deste padrão:
1. **Composição sobre Herança**: Este é o cerne do Composition Pattern. Em vez de criar componentes derivados através de herança (estendendo classes), você constrói componentes maiores e mais complexos combinando componentes menores e mais simples. (*Normalmente não usamos mais classes no React*)
2. **Reutilização de Código**: A composição permite reutilizar componentes em diferentes partes da aplicação. Isso não só economiza tempo e esforço, mas também mantém a consistência e facilita a manutenção.
3. **Flexibilidade e Customização**: Com a composição, é fácil alterar o comportamento ou a aparência de um componente, simplesmente substituindo ou adicionando novos componentes a ele, sem modificar o código existente.
4. **Encapsulamento e Abstração**: Componentes compostos podem encapsular complexidades internas e expor uma interface simples. Isso permite aos desenvolvedores trabalhar com um alto nível de abstração.
5. **Props e Children em React**: No React, a composição é frequentemente realizada passando componentes como `props` ou através de `children`. Isso permite que os componentes filhos sejam renderizados dentro de um componente pai de maneira flexível.
6. **[[Higher-Order Components (HOCs)]] e Render Props**: São técnicas em React que utilizam o Composition Pattern para compartilhar funcionalidades entre componentes ou para modificar o comportamento de um componente existente.
7. **Simplicidade e Manutenibilidade**: A composição frequentemente resulta em um código mais limpo e fácil de entender, o que torna a manutenção e a expansão do código mais gerenciáveis.
## Conclusão
O Composition Pattern é uma abordagem poderosa no desenvolvimento de interfaces de usuário, especialmente em bibliotecas e frameworks baseados em componentes, como React, pois oferece um grande poder de modularidade e reutilização de código.