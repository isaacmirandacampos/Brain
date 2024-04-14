created:: 2024-04-14 09:43
status:: #zettel/permanent 
tags:: #performance #database
## Introdução
O DynamoDB é um banco de dados NoSQL e totalmente gerenciável, o que implica em não precisar de intervenção do desenvolvedor para escalabilidade, backup e segurança dos dados. A escalabilidade e a performance são pontos fortes, além disso é um banco que permite trabalhar com *chave-valor*  e *documento*
## Vantagens do DynamoDB
**Escalabilidade Automática**: Uma das principais características do DynamoDB é sua capacidade de escalar automaticamente para atender às demandas de leitura e escrita, sem a necessidade de intervenção manual. Isso é particularmente útil para aplicações que experimentam padrões de tráfego variáveis. 
**Desempenho e Latência Baixa**: O DynamoDB é projetado para oferecer latência muito baixa nas operações de leitura e escrita, tornando-o adequado para aplicações que requerem tempos de resposta rápidos, como jogos, tecnologias de publicidade em tempo real e outros.
**Totalmente Gerenciado**: Como um serviço totalmente gerenciado, o DynamoDB elimina a necessidade de se preocupar com tarefas como provisionamento de hardware, configuração, replicação, atualizações de software e escalonamento.
**Modelo de Consistência Flexível**: O DynamoDB oferece a opção de consistência eventual ou forte, permitindo aos desenvolvedores escolher o modelo que melhor se adapta às suas necessidades específicas.
## Quando usar
É projetado para garantir escalabilidade, desempenho e confiabilidade. É mais adequado para aplicações que *necessitam de leitura e escrita de dados com latência baixa*, independentemente da escala, como aplicações *web, jogos e IoT*.