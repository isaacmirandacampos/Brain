created:: 2024-01-10 10:36
status:: #zettel/permanent  
tags:: #design 
people::
## Boas práticas de tipografia
### Centralizar a definição das tipografias
Centralizar em um único arquivo a declaração dos tamanhos de fonte, font-family e line-height, ou no mínimo trabalhar com variáveis do css. Isso é uma regra do próprio [[DRY - Don't repeat yourself]].
Nunca mude a font base do navegador:
```css
html {
	font-size: 62.5%
}
```
Isso prejudica:
- O usuário que já tem configurado o seu navegador
- O desenvolvedor que espera x comportamento mas ocorre y.
### Sempre definir o line-height
Está diretamente ligado a leiturabilidade do texto, então sempre devemos definir essa propriedade nós mesmos, se não, cada navegador usara um valor que ele mesmo definiu. Um detalhe importante, é de *nunca usar px para definir o line-height*. Como vamos aprender nos próximos tópicos, não devemos usar o *px* para definir font-size, a melhor abordagem é fazer uso do *rem*, e isso implica em um *line-height* quebrando em diferentes configurações de fontes. Segue um exemplo de [como o line-height pode quebrar caso seja usado com px](https://codepen.io/marcelluscaio/pen/vYvGaGo).
Considere sempre usar o line height com o tamanho da fonte + distância que considere legível. Um exemplo é usar:
```css
h1 {
	font-size: 2rem;
	line-height: 2.25rem;
}
```
## Unidade de medidas relativas
São unidades que não são *estáticas*, ou sejam, dado alguma mudança, a propriedade se adapta.
### Unidade de medida Rem
O *rem* é uma unidade de medida relativa que se baseia no tamanho da fonte definida na tag html, isso significa que:
- *as preferências do usuário alteram diretamente o conteúdo do site*, o que implica também em *maior acessibilidade*, já que o site vai se comportar de uma forma mais adaptada. 
- Diferentes navegadores podem possuir densidades de pixels diferente, o que isso já trás uma vantagem quando comparado a utilização do *px*.
O *px* é útil para precisão *(pixel-perfect)*, importante principalmente quando usado em imagens.
Os navegadores por padrão funcionam com 16px, dito isso, *1rem* é exatamente 16px, caso queiramos trabalhar com especificamente com 18px, uma forma seria usar o *1.125rem*. Aqui vai uma listinha de alguns valores que serão muito usados:
- .25rem = 4px;  
- .5rem = 8px;  
- .75rem = 12px;  
- 1.5rem = 24px
Não se engane, embora muitos locais informem que o Rem é responsivo, ele por si só não entrega responsividade. Você pode tirar a prova [aqui](https://codepen.io/marcelluscaio/pen/NWeGPoq)

**Dica da preguiça:** se não quiser calcular toda vez o valor do REM, uma forma é usar esse [plugin do vscode](https://marketplace.visualstudio.com/items?itemName=sainoba.px-to-rem)
### Unidade de medida Em:
O uso da unidade `em` no CSS é mais apropriado em certas situações, especialmente quando você quer que o tamanho de um elemento seja relativo ao tamanho da fonte de seu elemento pai, ao contrário do `rem` que é sempre relativo ao tamanho da fonte do elemento raiz (`html`). Aqui estão algumas situações em que o uso de `em` é recomendado:
- **Componentes Reutilizáveis e Escaláveis**: Quando você está criando componentes de interface que devem ser facilmente escaláveis e manter suas proporções relativas, `em` é muito útil. Por exemplo, em um botão com ícone e texto, você pode querer que o ícone e o preenchimento (padding) escalonem com o tamanho do texto. Definindo esses valores em `em`, eles se ajustarão automaticamente se você mudar o tamanho da fonte do botão.
- **Media Queries**: Para media queries que se baseiam no tamanho da fonte em vez da largura da viewport, `em` é a unidade preferida. Isso é útil para designs que devem se ajustar não apenas com base no tamanho da tela, mas também com base na preferência de tamanho de fonte do usuário.
- **Tipografia e Hierarquia Visual**: Quando se trabalha com tipografia, especialmente para definir tamanhos de fonte e espaçamento entre linhas (line-height) em um sistema de design tipográfico, `em` pode ser útil para manter uma hierarquia visual coesa que é consistente em relação ao tamanho da fonte pai.
## Uso do Clamp()
O *clamp* é uma função do css que permite que a gente faça manipulação do tamanho da fonte em diferentes telas sem fazer uso de media query, o que torna a percepção no uso da página, mais fluída.
```css
h1 {
	font-size: clamp("valor mínimo", "valor ideal", "valor máximo")
}
```
Para calcular o valor ideal é complexo, e para isso é interessante usar uma [calculadora online que vai nos permitir definir os viewport corretamente](https://utopia.fyi/type/calculator/).
Mas para exemplificar o uso, podemos definir o seguinte:
```css
h1 {
	font-size: clamp(1rem, .8rem + 1vw, 2rem)
}
```
Dessa forma, a chegamos na font minima em telas 320px, e as maiores fontes nas telas 1920px.

*Segue um exemplo de código no codepen que demonstra esse comportamento:* [Responsiveness with Fluid Typography](https://codepen.io/marcelluscaio/pen/VwqpYdO)
## Conclusão
É importante evitar inconsistência e repetição de código desnecessário, centralizar a forma com que você lida com diferentes tamanho de texto é importante. 
O uso do *REM é obrigatório* se o objetivo for ter mais acessibilidade.
O clamp é uma ótima abordagem para conseguir uma responsividade mais fluída para os textos, o que gera uma preocupação a menos para o desenvolvedor ter durante a tratamento da responsividade do projeto.

# References
-  https://dev.to/marcelluscaio/usar-rem-nao-torna-seu-site-responsivo-entenda-por-que-559e
- https://dev.to/marcelluscaio/tipografia-fluida-104n