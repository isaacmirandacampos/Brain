# Atomic Design
created:: 2024-04-14 09:25
status:: #zettel/permanent 
tags:: #pattern
## O que é Atomic Design?
Desenvolvido por *Brad Frost*, é uma metodologia para criar sistemas de design. Ela divide os componentes em cinco níveis:
- **Átomos**: São os elementos básicos, como botões, títulos, inputs.
- **Moléculas**: Conjuntos de átomos que funcionam juntos, como um formulário de busca (input + botão).
- **Organismos**: Conjuntos de moléculas que formam uma parte da interface, como um cabeçalho (logo + navegação + formulário de busca).
- **Templates**: Layouts que mostram como os organismos são distribuídos, mas ainda sem conteúdo real.
- **Páginas**: Templates com conteúdo real para representar o design final.

### Como funciona o [[Composition Pattern]] quando usamos Atomic Design?
Ao combinar Atomic Design com Composition Pattern em um projeto React, você pode:
**Criação de Componentes Modulares (Atomic Design)**: Comece definindo seus componentes mais básicos, como botões, ícones e campos de entrada (*átomos*). Em seguida, combine-os para formar componentes mais complexos (*moléculas e organismos*). 
**Composição de Componentes (Composition Pattern)**: Use a composição para combinar esses componentes menores de maneira flexível e reutilizável. Por exemplo, um componente de formulário (organismo) pode ser composto por vários componentes de entrada e botões (moléculas e átomos).

```js

// ArticlePreview.js
import Heading from './Heading';
import Text from './Text';
import Button from './Button';
const ArticlePreview = ({ title, summary, onReadMore }) => (
	<div>
		<Heading level={3}>{title}</Heading>
		<Text>{summary}</Text>
		<Button onClick={onReadMore}>Read More</Button>
	</div>
);

// Header.js - Agora aceita children para flexibilidade
const Header = ({ children }) => (
	<header>
		<h1>News Site</h1>
		<nav>{children}</nav>
	</header>
);

// NewsSection.js - Permite a passagem de um render prop para customização
const NewsSection = ({ articles, renderArticle }) => (
	<section>
		{articles.map(article => renderArticle(article))}
	</section>
);

// App.js
import React from 'react';
import Header from './Header';
import NewsSection from './NewsSection';
import Button from './Button';
import ArticlePreview from './ArticlePreview';
const App = () => {
	const articles = [
		{ id: 1, title: 'Article 1', summary: 'Summary of article 1' },
		{ id: 2, title: 'Article 2', summary: 'Summary of article 2' },
	];
	return (
		<div>
			<Header>
				<Button 
					onClick={() => console.log('Login')}>
					Login
				</Button>
				<Button 
					onClick={() => console.log('Register')}>
					Register
				</Button>
			</Header>
			<NewsSection
				articles={articles}
				renderArticle={(article) => (
					<ArticlePreview
						key={article.id}
						title={article.title}
						summary={article.summary}
						onReadMore={
							() => 
								console.log(`Reading ${article.title}`)
						}
					/>)}
			/>
		</div>
	);
};
export default App;
```
#### Quais os benefícios?
- **Flexibilidade e Reutilização**: A combinação dessas abordagens permite que você construa interfaces complexas a partir de componentes menores e reutilizáveis, melhorando a manutenção e escalabilidade do código.
- **Encapsulamento e Abstração**: Atomic Design ajuda a encapsular a complexidade de cada componente, enquanto o Composition Pattern permite abstrair essa complexidade ao combinar componentes de maneira lógica e funcional.
- **Melhoria na Manutenção**: Ambos os métodos contribuem para uma base de código mais organizada, o que facilita a manutenção e a atualização dos componentes.
## Conclusão
Para que faça sentido o uso do atomic design, é preciso ter definido um [[Design System]]

