# Inversão de array
created:: 2024-04-14 09:31
status:: #zettel/permanent 
tags:: #performance 
## Introdução
Inversões em um array são pares de elementos que estão fora de ordem. *Vamos exemplificar:* Para um array de 6 elementos, o número máximo de inversões acontece quando o array está em ordem decrescente, pois cada elemento estará fora de ordem com todos os elementos que vieram antes dele.
## Calculo
Para calcular o número máximo de inversões em um array de tamanho n, você considera que o primeiro elemento pode estar fora de ordem com n−1 elementos após ele, o segundo elemento pode estar fora de ordem com n−2 elementos após ele, e assim por diante, até o penúltimo elemento, que pode estar fora de ordem com apenas 1 elemento, e o último elemento não pode estar fora de ordem com nenhum outro, pois não há elementos após ele.
### Formula
A fórmula para calcular o número máximo de inversões é então:
*Número máximo de inversões=(n−1)+(n−2)+(n−3)+2+1*.
Esta é a soma de uma série aritmética. A fórmula para a soma dos primeiros k inteiros é:
 
$$\frac{k * (k+1)}{2}$$
No caso de um array de 6 elementos $$ar = [6,5,4,3,2,1]$$k seria 5, porque você não conta o último elemento:
$$\frac{5*(5+1)}{2}=\frac{5*6}{2}=\frac{30}{2}=15$$

Portanto, o número máximo de inversões que um array de 6 elementos pode ter é 15, o que corresponde à opção selecionada na pergunta.
## Importância
A contagem de inversões está intimamente relacionada à eficiência de certos algoritmos de ordenação e pode nos oferecer insights valiosos sobre o comportamento e a performance desses algoritmos, incluindo o mergesort. Entender a contagem de inversões pode ajudar no entendimento do mergesort de várias maneiras:
1. **Complexidade do Pior Caso**: Para algoritmos de ordenação baseados em comparação, como o mergesort, a contagem de inversões no pior caso oferece uma medida direta da complexidade do tempo. No pior caso, um array com o máximo número de inversões (ou seja, um array em ordem decrescente) precisará de mais comparações para ser ordenado do que um array com menos inversões.
2. **Adaptação para Contagem de Inversões**: O mergesort pode ser adaptado para contar o número de inversões em um array enquanto o ordena. Durante o processo de fusão do mergesort, sempre que um elemento do subarray direito é movido antes de um elemento do subarray esquerdo, uma inversão é contada. Isso significa que o número de inversões é igual ao número de vezes que um elemento precisa "pular" sobre outros elementos durante a fusão. Assim, o algoritmo não só ordena o array, mas também calcula quantos passos seriam necessários para ordenar um array utilizando um algoritmo de ordenação baseado em trocas, como o bubble sort.
3. **Análise de Melhor Caso**: Um array sem inversões é um array já ordenado. Se um algoritmo de mergesort detecta durante a fusão que os elementos estão todos em ordem (ou seja, cada elemento do subarray esquerdo é menor que todos os elementos do subarray direito), o restante do processo de fusão pode ser acelerado, pois não são necessárias mais comparações.
4. **Análise de Desempenho de Ordenação**: A quantidade de inversões em um array também pode ser usada para estimar o quão distante um conjunto de dados está de estar completamente ordenado. Isso pode ser útil para escolher a estratégia de ordenação mais eficiente. Por exemplo, se um array já estiver "quase ordenado", com poucas inversões, algoritmos como insertion sort ou um mergesort adaptado podem ser mais eficientes.
5. **Ensino e Compreensão de Algoritmos**: Do ponto de vista educacional, entender a contagem de inversões e como o mergesort as lida ajuda os estudantes a entenderem melhor conceitos como a complexidade assintótica e a eficiência dos algoritmos. Isso constrói uma base para o aprendizado avançado de estruturas de dados e algoritmos.

### Exemplo de uso em código
```python
def smart_sort(arr):
  length_of_arr = len(arr)
  num_inversions = count_inversions(length_of_arr)
  if num_inversions < len(arr) * 0.1:
	return insertion_sort(arr)
  else:
	sorted_arr, _ = mergesort(arr)
	return sorted_arr

original_array = [2, 1, 3, 5, 4]
sorted_array = smart_sort(original_array)
```
No código acima, usamos a contagem de inversões para otimizar o melhor algoritmo de ordenação usado. O mergesort por ser um algoritmo que sempre segue O(n log n), usar outro algoritmo nos da vantagem em performance.
Essa técnica é provavelmente bem similar a que foi usada pelo *google chrome* no método da função *Array.sort()* como citada no artigo [[Method Sort on Javascript]].