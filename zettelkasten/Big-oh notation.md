created:: 2024-04-14 10:04
status:: #zettel/permanent 
tags:: #performance #algorithm #mathematics 
## Introdução
A notação Big O é uma [[Asymptotic Analysis]], usado para descrever a eficiência de um algoritmo em termos de tempo de execução ou espaço necessário (memória), em função do tamanho da entrada de dados. Ela fornece uma *medida abstrata* para entender como o *tempo de execução ou o espaço necessário cresce à medida que o tamanho da entrada aumenta*.
### Big O vs benchmark
O Benchmark é uma forma de analisar a performance de uma aplicação, e embora ela tenha suas aplicações, é preciso ter alguns pilares para que seja possível realizar um benchmark, que são:
- Ter o código implementado
- Ter uma forma de metrificar
O primeiro pilar para realizar o benchmark (*Ter o código implementado*) é um grande limitador e que sugere sempre que tenhamos uma solução implementada e rodando para que possamos fazer comparativos, dito isso, o Big O soluciona esse problema, uma vez que através da estrutura de código você consegue entender como será o aumento de tempo de execução e/ou necessidade de hardware do seu sistema sem executar o código, isso possibilita você comparar diferentes soluções antes da implementação. 
O benchmark embora seja mais preciso e te der dados reais, ele não vai representar todos os cenários, enquanto o Big O tenta representar sempre o pior cenário.
## Aqui estão alguns pontos-chave sobre a notação Big O:

**Descrição de Eficiência**: Big O **descreve o pior cenário** de eficiência de um algoritmo, ajudando a entender como o algoritmo se comporta em situações extremas.

**Crescimento Assintótico**: Ela se concentra no crescimento a longo prazo do tempo de execução ou do uso de espaço, ignorando constantes e termos de menor ordem. Por exemplo, O(n) e O(2n) são considerados equivalentes na notação Big O, pois ambos crescem linearmente com o tamanho da entrada.

**Classificação de Algoritmos**: Algoritmos são frequentemente classificados com base em sua eficiência usando a notação Big O. Por exemplo, um algoritmo com tempo de execução O(n²) é considerado menos eficiente do que um com tempo de execução O(n) para grandes entradas.

### Uso Prático: 
A notação Big O é usada para comparar algoritmos, otimizar programas e tomar decisões informadas sobre qual algoritmo usar com base no tamanho esperado da entrada e nos recursos disponíveis.

Entender a notação Big O é crucial para o desenvolvimento de software eficiente e para a análise de algoritmos.

### Formula

- Somar cada passo do algoritmo
- Ignorar as constantes
- Ignorar os fatores multiplicadores

### **Exemplos Comuns:**
**O(1) (Constante):** Tempo constante. O tempo de execução não muda com o tamanho da entrada.
```python
def operacao(valor):
	result = 5 * valor / 3
	return result
operacao(200)
```
O valor da entrada não afeta o tempo da operação.

##### **O(log n) (Logaritmo):** 
Tempo logarítmico. O tempo de execução cresce logaritmicamente([[Logaritmo]]) em relação ao tamanho da entrada.
Um exemplo de algoritmo que tem esse comportamento é [[Binary Search]] ou o [[Fibonacci Search]] que é uma derivação do binary search. 
*OBS.: Recursividade geralmente é exponencial ou logarítmica*
##### **O(n) (Linear):** 
Tempo linear. O tempo de execução cresce linearmente com o tamanho da entrada.
```python
count = 0;
total = 200
while(total >= count):
	print(f"encontrou {count}")
	count += 1
```
Quanto maior a lista, maior o tempo de execução e isso cresce linearmente.
##### **O(n log n)** (Log linear):  
Tempo log-linear. Comum em algoritmos de ordenação eficientes, como Heap-sort, você consegue se aprofundar mais nesse algoritmo no arquivo [[Heap-sort]].
##### **O(n²)**(quadrática): 
Tempo quadrático. O tempo de execução cresce proporcionalmente ao quadrado do tamanho da entrada.
Um exemplo de código nessa ordem pode ser visto aqui: [[how to improve performance by avoiding notation in quadratic time order]]
Geralmente um loop dentro de outro loop causam esse cenário, e isso é bom ser evitado se possível. No link citado acima é possível visualizar como um mesmo código em escala O(n²) *(quadrática)* é menos performático que um algoritmo com 2 loops O(n) *(linear)*.
##### **O(2^n) (exponencial):**
Ordem de tempo exponencial. O tempo de execução cresce exponencialmente com o tamanho da entrada.
```python
def generate_subsequences(arr):
    def backtrack(start, current):
        print(start, current)
        if start == len(arr):
            # current é uma subsequência completa
            subsequences.append(list(current))
            return
        # Inclui o elemento atual na subsequência
        current.append(arr[start])
        backtrack(start + 1, current)
        # Exclui o elemento atual da subsequência
        current.pop()
        backtrack(start + 1, current)
	subsequences = []
	backtrack(0, [])
	return subsequences
```
É bom ser evitado pois rapidamente o algoritmo pode torna-se ineficiente com o aumento da entrada.
Para ilustrar matematicamente, segue exemplo de fatorial:
$$2⁵ = 2 * 2 * 2 * 2 * 2 = 25$$
##### **O(n!) (Fatorial):**
Ordem de tempo fatorial. O tempo de execução cresce exponencialmente com o tamanho da entrada.
```python
def factorial(n):
	if n == 0:
		return 1
	else:
		return n * factorial(n - 1)
```
Esse é o pior cenário possível no quesito performance, e é bom evitar.
Para ilustrar matematicamente, segue um exemplo de fatorial:
$$5! = 5 * 4 * 3 * 2 * 1 = 120$$
## É possível um algoritmo ter mais de uma ordem de tempo de execução?
Como foi citado anteriormente, os algoritmos podem ser representados de forma assintóticas com o big oh notation, e alguns algoritmos possuem mais performance que outros nos piores casos. Também podemos analisar como o algoritmo se comporta nos melhores cenários, mas na maioria das vezes a gente procura os piores. Segue uma tabela descrevendo alguns algoritmos famosos e suas classificações de pior e melhor caso:

**Conteúdo complementar:**
https://www.youtube.com/watch?v=ugDAPN3rhIE
https://kmcompsci.weebly.com/big-o-notation.html
