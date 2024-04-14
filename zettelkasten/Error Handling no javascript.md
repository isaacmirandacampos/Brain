created:: 2024-04-14 09:51
status:: #zettel/fleeting 
tags:: #performance 
## Não lance erros dentro de callbacks

**Problema:**
```js
import fs from 'node:fs'

try {
	fs.readFile('not-found.txt', (err, result) => { if(err) throw err })
} catch (err) {
	console.log("nunca é chamado", err)
}
```
O Try catch cria um contexto, e os contextos precisam  que os erros ocorram dentro dele. No nosso exemplo, o erro está ocorrendo ainda dentro do callback, o que não permite o try receber esse erro para lidar com ele dentro do catch.

**Solução:**
```js
import fs from 'node:fs'

try {
	await new Promise ((resolve, reject) => {
			fs.readFile('not-found.txt', 
			(err, result) => err ? reject(err) : resolve(result)
			)
		})
} catch (err) {
	console.log("É chamado", err)
}
```
Dessa forma nós estamos retornando o erro para o contexto do try catch, o que permite a gente manipular pelo catch.
## Evite exceções
O *try* é um bloco que pode receber erros, e esses erros são tratados como exceções no bloco *catch*. *Quando usamos try-catch*, nós estamos fazendo uma *estrutura mais custosa*, *a melhor forma para casos de errors previsíveis* é lançar um *throw new Error* e controlar isso através de uma *condicional*.

# References
- [Artigo sobre controle de error handling](https://accreditly.io/articles/a-comprehensive-guide-to-exception-handling-in-javascript)
- [Error Handling - Erick Wendel](https://www.youtube.com/watch?v=iC_tKAyLeag)