created:: 2024-04-14 09:26
status:: #zettel/permanent 
tags:: #data-structure 
## Introdução
Um *heap* é uma estrutura de [[Data structure]], que é essencialmente uma árvore binária, mas com algumas propriedades especiais. Em um _heap_, todos os nós seguem a propriedade de ordem de heap, que pode ser de dois tipos:

## Os tipos de estrutura heap
**Max Heap**: Em um max heap, o *valor de cada nó é maior ou igual ao valor de seus filhos*. Isso significa que *o valor máximo está na raiz do heap*. Por exemplo, se a raiz é 10, então todos os nós da árvore serão menores ou iguais a 10. Este arranjo é útil quando você precisa acessar repetidamente o maior elemento.
No max heap, Uma forma de encontrar os valores filhos de um valor é usando a seguinte formula, o elemento da posição *i* é maior ou igual aos elementos das posições 2i e 2i + 1

**Min Heap**: Em um min heap, é o contrário. *Cada nó tem um valor menor ou igual ao de seus filhos*. *O valor mínimo*, portanto, *está na raiz*. Por exemplo, se a raiz é 5, então todos os nós da árvore serão maiores ou iguais a 5. Este arranjo é útil quando você precisa acessar repetidamente o menor elemento.
No min heap, Uma forma *de encontrar os indices filhos de um valor* é usando a seguinte formula, o elemento da posição *i* é menor ou igual aos elementos das posições $$2 * indice = 2 * 2 = 4$$ e $$2 * indice + 1 = 2 * 2 + 1 = 5$$
Além disso, um _heap_ é uma árvore binária quase completa, o que significa que todos os níveis da árvore estão completamente preenchidos, exceto talvez o último nível, que é preenchido da esquerda para a direita.


#### Como encontrar o índice do elemento pai numa posição filho

Para encontrar o índice do pai:
```python
def find_father(i):
	return i/2
```

Para encontrar o filho a esquerda:
```python
def find_the_son_on_the_left():
	return 2*i
```

Para encontrar o filho a direita:
```python
def find_the_son_on_the_right():
	return 2*i + 1
```

#### Como inserir um novo dado em uma estrutura max heap
*Ao inserir um novo dado*, é possível que isso *viole as regras* estabelecidas pelo *max heap*([[#^1b98f8]])  e *min heap*([[#^001923]]).
Nas imagens a seguir, ilustra como a gente corrige a estrutura em casos de violação:

Exemplo de código de como verificar se uma estrutura heap foi violada:
```python
def heapify(vetor, n, i): 
	largest = i 
	left = 2 * i + 1 
	right = 2 * i + 2 
	if left < n and vetor[left] > vetor[largest]: 
		largest = left 
	if right < n and vetor[right] > vetor[largest]: 
		largest = right 
	if largest != i: 
		vetor[i], vetor[largest] = vetor[largest], vetor[i] 
		heapify(vetor, n, largest)
```

#### Como organizar um vetor em uma estrutura max heap
Para organizar uma estrutura heap, a gente sempre começa do ultimo pai do vetor. Como na etapa anterior a gente garante sempre que a violação não ocorra de cima para baixo, aqui a gente usará esse mesmo código para garantir a construção do nosso vetor.

Exemplo de código:
```python
def build_max_heap(vetor): 
	vetor_length = len(vetor) 
	for i in range(vetor_length // 2 - 1, -1, -1): 
		heapify(vetor, vetor_length, i)
```
### Outras propriedades da estrutura Heap
**Altura da arvore:** é [[Logaritmo]] de N elementos 
## Aplicações de uma estrutura Heap
- **Ordenação de Heap ([[Heap-sort]])**: Usando as propriedades de um heap, você pode classificar os elementos de maneira eficiente.
- **Implementação de Filas de Prioridade**: Heaps são frequentemente usados para implementar filas de prioridade, que são usadas em algoritmos como Dijkstra para encontrar o caminho mais curto, em sistemas de agendamento de tarefas, etc.
- **Encontrar o K-ésimo maior/menor elemento**: Em um heap, operações como encontrar o maior ou o menor elemento são muito eficientes, o que é útil em muitos cenários de computação.
# References
-  [e-Aulas da USP :: Mod. 1 - Estrutura de dados: Heap](https://eaulas.usp.br/portal/video?idItem=15846)
