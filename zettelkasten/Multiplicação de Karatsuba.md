**Target:**# Multiplicação de Karatsuba
created:: 2024-04-14 09:06
status:: #zettel/permanent 
tags:: #mathematics #performance 
## Introdução
é um algoritmo eficiente para *multiplicar grandes números, desenvolvido por Anatolii Alexeevitch Karatsuba em 1960*. Ele se baseia no princípio de *dividir para conquistar*, o que o torna mais rápido do que o método de multiplicação tradicional para números suficientemente grandes.
## Como funciona:
1. **Divisão dos Números:** Primeiro, *dividimos cada número em duas partes*. Por exemplo, se tivermos dois números com várias dígitos, podemos dividi-los pela metade. Se estamos multiplicando *1234 por 5678*, dividimos esses números em *12 e 34, e 56 e 78*, respectivamente.
	1. Resultado de *1234 * 5678* é *7006652*
2. **Três Multiplicações ao Invés de Quatro:** Em vez de realizar quatro multiplicações (como seria no método tradicional), o método de *Karatsuba realiza apenas três*.
3. **Combinação dos Resultados:** Finalmente, combinamos esses três resultados para obter o produto final. Este passo envolve adicionar zeros (de acordo com a posição dos dígitos) e somar os resultados. Por exemplo, no nosso caso, o resultado da primeira multiplicação é deslocado para a esquerda (equivalente a multiplicar por 10 elevado ao número de dígitos), o resultado da terceira multiplicação é somado diretamente, e o resultado da segunda multiplicação é deslocado para a esquerda pela metade do número de dígitos.
### Passo a passo de como funciona o algoritmo
**A formula é o seguinte:** 
*(10^n)× ac + (10^n/2) ×((a+b)×(c+d)−ac−bd)+bd*
Vamos explicar essa formula contextualizando com a nossa multiplicação de 1234 * 5678.
- N é o número de dígitos, *4*.
- a = *12*, b = *34*, c = *56*, d = *78*
**Agora vamos resolver o algoritmo em partes:**
Vamos primeiro resolver a parte *(a+b)×(c+d) = (12+34)×(56+78)*
- a + b = *46*
- c + d = *134*
- 134 x 46 = 804 + 5360 = *6164*
- o resultado de (a+b)×(c+d) = (12+34)×(56+78) é 6174
A próxima etapa é calcular os resultados de *ac e bd*
- a * c é *672*
- b * d é *2652*
Agora *subtraímos* a soma de *ac* e *bd* por *(a+b)×(c+d)*
- 6164 - 672 - 2652 = *2840*
Se substituirmos os valores da formula *(10^n)× ac + (10^n/2) ×((a+b)×(c+d)−ac−bd)+bd*, temos o seguinte cenário: *10⁴ x 672 + 10² x 2840 + 2652*, para chegarmos em um resultado concreto, vamos continuar com as operações.
- 10⁴ é *10000*, e 10000 x 672 = *6720000*
- 10² é *100*, e 100 x 2840 = *284000*
- 6720000 + 284000 = *7004000*
- 7004000 + 2652 = *7006652*
### Como é feito o calculo se os números não tiverem bases iguais?
Se a gente for trabalhar com a *multiplicação de bases diferentes*, vamos precisar *igualar o número de dígitos nas duas bases*, e podemos fazer isso *adicionando 0 a esquerda* dos números. Se formos trabalhar com a multiplicação de *1234 por 123*, a gente precisaria adicionar 0 a esquerda de 123, o que ficaria *1234 x 0123*
### Como é feito o calculo caso a gente tenha mais de 4 dígitos?
Se a gente for trabalhar com *multiplicação de bases maiores que 4 dígitos,* precisamos dividir o número em duas metades, sempre mantendo a primeira metade com quantidade igual ou maior de dígitos comparado a segunda meta. Vamos exemplificar com a multiplicação de 654321 por 7654321, a as metades seriam *A = 0654, b = 321* e *c = 7654, d = 321*. 

## Seguindo o big o notation, qual ordem de tempo esse algoritmo segue?
Aqui temos um exemplo de código que:
```python
def karatsuba(x, y): 
	# Caso base para a recursão 
	if x < 10 or y < 10: 
		return x * y # 
		
	Tornando o comprimento dos números igual 
	n = max(len(str(x)), len(str(y))) 
	m = n // 2 
	
	# Dividindo os números em duas partes 
	high_x, low_x = divmod(x, 10**m) 
	high_y, low_y = divmod(y, 10**m) 
	
	# Três multiplicações de Karatsuba 
	z0 = karatsuba(low_x, low_y) 
	z1 = karatsuba((low_x + high_x), (low_y + high_y)) 
	z2 = karatsuba(high_x, high_y) 
	
	# Combinando os resultados 
	return (z2 * 10**(2 * m)) + ((z1 - z2 - z0) * 10**m) + z0 
# Exemplo de uso 
result = karatsuba(123456, 7654321) print(result)
```

  
O algoritmo de multiplicação de Karatsuba tem uma complexidade temporal de O(n log2³), que é aproximadamente O(n^1.585). Portanto, entre as opções, a mais próxima seria *O(n log n)* [[Big-oh notation#^6020c0]], mas é importante notar que isso *não é uma correspondência exata*. A complexidade temporal do algoritmo de Karatsuba *não corresponde exatamente a nenhuma* das opções comuns listadas como *O(1), O(log n), O(n log n), O(n), O(n²), ou O(2n)*, mas é mais eficiente do que a multiplicação tradicional (longa multiplicação), que tem uma complexidade de *O(n²)* [[Big-oh notation#^a2b1b7]].
*imagem ilustrando*: [[Big-oh notation#^97d704]]