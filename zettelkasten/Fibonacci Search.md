created:: 2024-04-14 09:40
status:: #zettel/permanent 
tags:: #algorithm 
## O que é Fibonacci Search?

É um algoritmo de busca que se baseia no [[Binary Search]], mas ao invés de sempre reduzir o arranjo pela metade, ele usa a sequencia de Fibonacci para determinar o inicio e fim do arranjo que vai ser analisado para aquele ciclo no loop. 
### Exemplo de código de Fibonacci search:
```python
def fibonacciSearch(arr, x):
	fibMMm2 = 0 # (m-2)º número Fibonacci
	fibMMm1 = 1 # (m-1)º número Fibonacci
	fibM = fibMMm2 + fibMMm1 # mº número Fibonacci
	while (fibM < len(arr)):
		fibMMm2 = fibMMm1
		fibMMm1 = fibM
		fibM = fibMMm2 + fibMMm1
	offset = -1

	while (fibM > 1):
		i = min(offset + fibMMm2, len(arr) - 1)
		if (arr[i] < x):
			fibM = fibMMm1
			fibMMm1 = fibMMm2
			fibMMm2 = fibM - fibMMm1
			offset = i
		elif (arr[i] > x):
			fibM = fibMMm2
			fibMMm1 = fibMMm1 - fibMMm2
			fibMMm2 = fibM - fibMMm1
		else:
			return i
		if(fibMMm1 and arr[offset+1] == x):
			return offset+1
		return -1

arr = [10, 22, 35, 40, 45, 50, 80, 82, 85, 90, 100]
x = 85
print("Encontrado em índice:", fibonacciSearch(arr, x))
```

### Qual a classificação desse algoritmo segundo o [[Big-oh notation]]?

A complexidade temporal do algoritmo de Pesquisa Fibonacci é O(log n).

**Divisão do Problema**: A cada passo do algoritmo, ele reduz o tamanho do espaço de busca. Similar à [[Binary Search]], que divide o espaço de busca pela metade, a pesquisa Fibonacci divide o espaço de busca de uma maneira que está aproximadamente de acordo com a proporção áurea ([[Fibonacci sequence]]). Embora o ponto exato de divisão possa variar, ele ainda reduz significativamente o tamanho do problema a cada passo.
   
**Número de Passos**: O número de passos necessários para encontrar um elemento (ou concluir que ele não está presente) cresce logaritmicamente([[Logaritmo]]) em relação ao tamanho do array. Isso significa que mesmo que o tamanho do array dobre, o número de passos necessário cresce apenas por uma quantidade constante.

**Constantes e Fatores Menores**: Embora o algoritmo de Pesquisa Fibonacci possa ter diferentes constantes ou fatores menores quando comparado à pesquisa binária, isso não afeta a classificação Big O, que se concentra no crescimento relativo do tempo de execução em relação ao tamanho do input.
### Possíveis vantagens em relação ao [[Binary Search]]
**Menos Comparação em Certo Casos**: Em alguns casos, a pesquisa Fibonacci pode realizar menos comparações do que a pesquisa binária padrão. Isso acontece porque, ao invés de dividir o conjunto de dados pela metade a cada passo, o algoritmo divide os dados em seções que podem ser desproporcionais, potencialmente levando a uma busca mais rápida pelo elemento desejado.
   
**Uso Eficiente da Memória**: O algoritmo de pesquisa Fibonacci pode ser ligeiramente mais eficiente em termos de uso de memória. Em pesquisa binária, o rastreamento dos limites da subseção atual requer o armazenamento de dois índices. Já na pesquisa Fibonacci, você pode gerenciar com menos informações de estado, pois o tamanho das seções é determinado pelos números de Fibonacci.
   
**Manipulação de Tamanhos Desconhecidos ou Indefinidos**: A pesquisa Fibonacci pode ser útil em situações onde o tamanho do conjunto de dados não é conhecido antecipadamente ou é indefinido. Como o algoritmo ajusta dinamicamente os pontos de divisão com base nos números de Fibonacci, ele pode se adaptar a conjuntos de dados de tamanhos variáveis mais facilmente do que a pesquisa binária padrão.
   
**Aplicações em Sistemas Distribuídos**: Em sistemas distribuídos onde os dados estão distribuídos entre vários nodos, a pesquisa Fibonacci pode ser usada para reduzir o número de chamadas de rede necessárias para localizar um item.
   
**Divisões de Dados Não Uniformes**: Em estruturas de dados onde os elementos não são uniformemente distribuídos, a pesquisa Fibonacci pode oferecer uma melhor performance em comparação com a pesquisa binária padrão, especialmente se os elementos mais frequentemente acessados estiverem mais perto do início do conjunto de dados.   

Apesar dessas vantagens teóricas, na prática, a pesquisa binária padrão é frequentemente mais simples de implementar e entender, e é muito eficiente para a maioria dos conjuntos de dados, especialmente se eles são uniformemente distribuídos. A escolha entre pesquisa Fibonacci e pesquisa binária padrão depende do contexto específico e dos requisitos do problema em questão.
