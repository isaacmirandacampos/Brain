created:: 2024-04-14 09:46
status:: #zettel/permanent 
tags:: #pattern 
## O que é?
É um padrão avançado em React para reutilizar a lógica de componentes. Eles são uma técnica derivada do conceito de funções de ordem superior em JavaScript. Um HOC é uma função que recebe um componente e retorna um novo componente com funcionalidades adicionais ou alteradas.
### Conceitos Chave dos HOCs
- **Função de Ordem Superior**: Em JavaScript, funções de ordem superior são funções que podem receber outras funções como argumentos ou retorná-las como resultado. HOCs são um exemplo disso, pois recebem componentes (que são essencialmente funções) e retornam novos componentes
- **Reutilização de Lógica**: HOCs são usados principalmente para adicionar funcionalidades compartilhadas entre diferentes componentes, promovendo a reutilização de código e a separação de interesses.
- **Composição sobre Herança**: HOCs oferecem uma alternativa à herança, permitindo que você estenda a funcionalidade de um componente sem a necessidade de herdar diretamente dele.
### Exemplo Básico de HOC
Vamos considerar um exemplo simples de um HOC que adiciona funcionalidades de rastreamento a um componente:

```jsx
// Um HOC simples que adiciona funcionalidades de rastreamento
const withTracking = WrappedComponent => {
	return class extends React.Component {
		componentDidMount() {
			// Lógica de rastreamento
			console.log(`Componente ${WrappedComponent.name} montado.`);
		}
		render() {
			return <WrappedComponent {...this.props} />;
		}
	};

};
// Um componente qualquer
const MyComponent = () => <div>Olá, Mundo!</div>;

// Aprimorando MyComponent com o HOC
const TrackedMyComponent = withTracking(MyComponent);
```

Neste exemplo, `withTracking` é um HOC que envolve `MyComponent`. O novo componente `TrackedMyComponent` agora tem funcionalidades adicionais de rastreamento, sem modificar o componente original.
### Pontos Importantes ao Usar HOCs
- **Propagação de Props**: É importante garantir que todos os props sejam passados ao componente envolvido, o que é feito usando `{...this.props}`.
- **Não Modifique o Componente Original**: HOCs devem criar um novo componente sem alterar o componente original.
- **Convenções de Nomenclatura**: Normalmente, HOCs começam com `with`, indicando que estão adicionando algo ao componente, como `withRouter`, `withStyles`, etc.

## Conclusão
HOCs são uma ferramenta poderosa no arsenal do React, permitindo que desenvolvedores criem componentes altamente reutilizáveis e mantenham seu código DRY ("Don't Repeat Yourself"). No entanto, eles podem adicionar complexidade e devem ser usados com discernimento.