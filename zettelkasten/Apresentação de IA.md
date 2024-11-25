# Apresentação de IA
created:: 2024-11-25 10:30
status:: #zettel/permanent 
tags:: #machine-learning 

## O que é uma Ia?
Existem diversos tipos de IA. A mais famosa delas é o que chamamos de IA generativa. Diferente de outras IAs que normalmente retornam uma unica resposta, a ia generativa gera diversas respostas que constituem um texto legível para um humano.

### Por que chamar de IA?
O termo surgiu por volta dos anos 1910+, e foi usado para meio de marketing já que na época era bem embrionário os computadores e existia uma barreira tecnologica imensa, e para chamar atenção, o termo foi criado. Naquele tempo a ciência não tinha uma boa definição do que seria inteligência. Anos depois foi decidido que a melhor definição para IA, era: "Uma ferramenta capaz de realizar atividades que faz ela parecer um humano". Para meios de marketing e captação de investimento, o termo continuo sendo usado.

### O que de fato uma ia generativa faz?
De forma bem superficial e breve, uma ia generativa é um modelo probabilistico. A IA consiste em um modelo gigante de palavras que estão distribuidas em um modelo cartesiano. 
![Modelo cartesiano](https://github.com/isaacmirandacampos/Brain/blob/master/attachments/modelo-cartesiano.png?raw=true")

Cada ponto no modelo cartesiano vai representar uma palavra, as palavras possuem pesos e os pesos determinam a aproximação de uma palavra com outra. Por exemplo, provavelmente a palavra maçã tem um peso mais prõximo de uva do que a palavra pneu.
#### Onde entra a probabilidade nisso?
Com base na pergunta que você fez, a ia generativa vai aplicar um calculo probabilistico de qual palavra tem um peso mais similar para completar o texto a qual você enviou, esse calculo pode errar. E preste muita atenção aqui: a ia tenta acertar a próxima palavra, a cada palavra ela tentara descobrir a prõxima com base na ultima que ela devolveu, ou seja, a cada palavra, existe uma probabilidade de ela se perder com base na ultima palavra que ela retornou.

## Como funciona o modelo de IA no chatgpt?
Quando enviamos uma pergunta para o chatgpt ou outros modelos, em geral, vai acontecer um fluxo similar há:
```
"Seu texto" -> "um texto que o modelo gerou que parece completar o seu"
```
### Não existe mágia
Talvez até aqui você já tenha entendido que existe uma limitação no nosso modelo de ia generativa. Todo esse modelo só é capaz de completar um texto, não de fato é capaz de entender o que ta sendo feito, não tem o que chamamos de inteligência, mas sim um grande modelo matemático e probabislitico. Em resumo, se você acredita em um apocalipse cibernético dominado pelas IAs, até que a gente descubra uma nova forma de criar modelos de IAs, que provavelmente dependem de avanços da neurociência, matemática, química, física e computacional, não seremos capaz de criar algo que de fato tenha um mínimo de inteligência.
## Técnicas de IA
Existem 3 formas de fazer uso de IA hoje em dia:
### Uso de prompts:
Ao criar uma pergunta para o modelo, você já está criando um prompt. Esse prompt pode ser melhorado usando engenharia de prompt. Engenharia de prompt é uma técnica basica que todos podem usar sem muita dificuldade. Você pode usar um modelo como base para realizar perguntas sempre, exemplo de modelo:
```Readme
**Persona**: Como profissional de marketing, Tarefa: crie dez slogans para um café orgânico 

**Etapas**: direcionado a agências de marketing. 

**Contexto**: O principal ponto de venda do produto é que ele é orgânico, saboroso e aumenta o poder da criatividade de maneira natural. 

**Restrições**: O slogan deve ter de duas a seis palavras. Não use a palavra "verde". 

**Objetivo**: O objetivo é encapsular o espírito inovador da nossa marca em um slogan curto e ágil. 

**Saída**: Gere ao menos 10 slogans diferentes em uma lista de marcadores.
```

Ao usar prompts, você aumenta as chances de receber uma resposta mais satisfatória.

#### Prós e contras
Prós: 
- Fácil de usar.
- Rapido de usar.
- Atende a maioria dos casos simples.
- Barato dependendo do caso de uso.
Contras:
- O modelo não consegue trabalhar um contexto muito grande. Caso precise usar PDFs para alimentar uma base, dependendo da ia, até consegue dar uma resposta, porém, as chances de ser satisfatórias são menores do que outras técnicas, como ainda sim terá um limite.
##### exemplos:
Usos comuns: pedir resumo de livro, resumo de vídeo no youtube, dũvida abrangente sobre algo...

### Uso de RAG's
Rag é uma técnica de alimentar e colocar dados disponiveis para uma IA generativa, onde você usa uma base de dados, PDFs e outros tipos de arquivos, quebra esse conteudo em chunks (partes), e usa um banco de dados vetorial com cada chunk (parte) gerada. Assim a ia consegue localizar dentro de uma base grande de dados, os dados que atendem o contexto da pergunta.
#### Prós e contras
Prós:
- Mais complicado que o prompt, mas ainda fácil de usar.
- A ia fica mais especifica para o casos de uso implementado.
- Capacidade de regular a capacidade criativa(temperatura) da ia.
- O modelo de IA continua genérico, sendo possível usar o mesmo modelo em diferentes sistemas de RAGs.
Contras:
- Demora mais para implementar.
- Precisa montar uma base de dados consistente.
- Alguns testes serão necessários para melhorar as respostas.
- Pode ficar um pouco mais caro, já que toda pergunta para IA vai tentar buscar uma base maior de dados para gerar uma resposta.
##### Exemplos:
Chatbot em ferramentas de comunicação, ia para auxiliar na identificação de problemas de máquinas, ia que auxilia o time de vendas a entender as funcionalidades que são suportadas pelo produto.
### Uso de fine tunning
Essa técnica consiste em usar um modelo de IA, na maioria das vezes open source, para realizar um treinamento em cima dela. Diferente de outras técnicas, os dados que forem usados para o fine tunning, serão embutidos dentro do modelo de IA. É como quebrar um modelo muito genérico em um modelo mais especifico que realiza uma determinada tarefa.
#### Prós e contras
Prós:
- O modelo acerta mais para casos especificos do que os comparados as RAGs.
- Fica mais barato por uso, já que o modelo foi treinado com base nos dados, ele consulta uma base menor a cada pergunta.
Contras:
- Muito mais complexo de implementar.
- Um final tunning bem feito é bem provável que precisa de um técnico em Data Science para implementar. O que torna bem mais caro o projeto comparado aos outros.
- O modelo não é tão mais reutilizável, sendo preciso ter outros modelos para atender outros casos.
- Demora implementar.
##### Exemplos:
IA para advogados que tem conhecimento da legislação brasileira, ia para contadores que ajuda no calculo de tributação...