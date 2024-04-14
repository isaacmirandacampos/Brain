created:: 2024-04-14 09:12
status:: #zettel/permanent 
tags:: #algorithm 
## What is it?
Na ciência da programação, um "sentinel value" ou "valor sentinela" é um valor especial usado em programação para indicar uma condição específica, geralmente para sinalizar o fim de um conjunto de dados ou para marcar um valor que está fora do escopo normal de valores válidos para um determinado processo ou cálculo.
### Aqui estão algumas características e usos comuns dos valores sentinela:
1. **Marcação de Fim de Dados**: Em muitos casos, um valor sentinela é usado para indicar o fim de uma lista de dados. Por exemplo, em uma lista de números, um valor como -1 (se todos os outros números são positivos) pode ser usado como um valor sentinela para indicar o fim da lista.
2. **Detecção de Condições Especiais**: Em certos algoritmos, um valor sentinela pode ser usado para detectar uma condição especial, como um erro ou uma situação atípica, que necessita de tratamento diferenciado.
3. **Simplicidade no Controle de Loop**: Valores sentinela podem ser usados para simplificar a lógica de loops, eliminando a necessidade de uma condição de verificação separada para o fim do loop.
4. **Segurança e Robustez**: Em alguns contextos, um valor sentinela pode ajudar a prevenir erros, como leituras fora dos limites de um array.
5. **Facilidade de Implementação**: Em algumas situações, a utilização de um valor sentinela pode tornar a implementação de certas funções mais simples e direta.

É importante escolher um valor sentinela que não seja confundido com um valor regular dentro do conjunto de dados. Por exemplo, se estiver trabalhando com números inteiros positivos, um valor negativo pode ser um bom valor sentinela. Em strings, um caractere raro ou uma combinação específica de caracteres pode servir como um valor sentinela.