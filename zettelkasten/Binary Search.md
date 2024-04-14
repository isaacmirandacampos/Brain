# Binary search
created:: 2024-04-14 09:41
status:: #zettel/permanent 
tags:: #performance #algorithm 
## O que é?
É um [[Search algorithm]] de listas **ordenadas** muito utilizado em diversos sistemas.
### Como funciona?
Em cada passo da busca binária, o algoritmo divide o conjunto de dados (lista) pela metade. Isso significa que, a cada iteração, o número de elementos restantes para procurar é reduzido pela metade.
```python
def binary_search(list, item):
	low = 0
	high = len(list) - 1
	while(low <= high):
		middle = (low + high) // 2
		if list[middle] == item:
			return middle
		elif list[middle] > item:
			high = middle - 1
		elif list[middle] < item:
			low = middle + 1
	return None

ordered_list = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
result = binary_search(ordered_list, 19)
print("The index of the item is: ", result)
```

#### Uma breve explicação do algoritmo:
as variáveis *low* e *high* vão ser os ponteiros que vão guardar o índice conforme cada interação no loop ocorrer. Enquanto o *high* for maior do que *low*, o loop vai continuar ocorrendo, ou vai parar quando achar o *item* alvo. A cada interação o alvo é o meio da lista. Caso o valor do meio da lista seja maior do que o alvo *item*, *high* vai receber o valor do *middle* + 1 (precisa somar + 1, pois o valor do *middle* sozinho já foi validado), caso o valor do meio da lista seja menor que o *item* alvo, *low* vai receber o valor de *middle* - 1 (-1 porque o valor índice de *middle* já foi validado).

dessa forma, os valores esperados a cada interação no loop vão ser respectivamente:
```bash
Lista = [ 1, 3, 5, 7, 9, 11, 13, 15, 17, 19 ]
Alvo = 19

low=0,middle=4,high=9
low=5,middle=7,high=9
low=8,middle=8,high=9
low=9,middle=9,high=9
The index of the item is:  9
```

