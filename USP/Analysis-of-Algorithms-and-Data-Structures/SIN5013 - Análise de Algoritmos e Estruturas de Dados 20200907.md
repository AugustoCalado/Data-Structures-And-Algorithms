# SIN5013 - Análise de Algoritmos e Estruturas de Dados 2020/09/07

## Consumo de Tempo
Pense no tempo de execução de algoritmo como:
- `uma função do tamanho da sua entrada`
- `quão rapido essa função cresce dado o tamanho da entrada`

Seja `T(n)` o consumo de tempo (no pior caso, ou melhor, ou caso médio) do algoritmo `A`, para instancias de tamanho `n`.

Como pretendemos medir a ordem de grandeza da função de tempo do algoritmo. Precisamos de um modo para comparar funções que considere as suas **velocidade de crescimento**.

- O - comparação com ideia de "<="
	> Definição: Dadas funções assintoticamente não-negativas f e g, dizemos que f  está na ordem Ο de  g e escrevemos f  = Ο(g) se existe um número [positivo](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/dictionary.html#positive)  c tal que f(n)  **≤**  c · g(n) para todo n suficientemente grande. Em outras palavras, se existem números positivos c e n0 tais que f(n) ≤  c · g(n) para todo n maior que n0. 

- Ω -  comparação com ideia de "= "
	> Definição: Dadas funções [assintoticamente não-negativas](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/Oh.html#asymptotically-nonnegative)  f e g, dizemos que f  está na ordem Ômega de  g e escrevemos f  = Ω(g) se existe um número positivo c tal que f(n)  **≥**  c · g(n) para todo n  [suficientemente grande](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/dictionary.html#suficientemente).
	
- Θ -  comparação com ideia de ">=" 
	> Definição: Dizemos que duas funções assintoticamente não negativas f e g  são da mesma ordem e escrevemos f  = Θ(g) se f  = Ο(g)  e  f = Ω(g). Trocando em miúdos, f  = Θ(g) significa que existe números positivos c e d tais que c g(n) ≤  f(n) ≤  d g(n) para todo n  [suficientemente grande](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/dictionary.html#suficientemente). 

fonte: [IME - Comparação assintótica de funções](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/Oh.html)
	
### Instruções Simples x Complexas

### Notação O
`O(f(n))` intuitivamente são funções que não crescem mais rápido que `f(n)`

Exemplo: n^2 + 3n - 3 é  `O(n^2)`

### Propriedades das Notações - Transitividade e Reflexividade
![propriedades-notacoes-omega-teta-oh](https://github.com/AugustoCalado/Data-Structures-And-Algorithms/blob/master/USP/Analysis-of-Algorithms-and-Data-Structures/resources/Imagens/propriedades-notacoes-omega-teta-oh.png)

![propriedades-notacoes-omega-teta-oh-2](https://github.com/AugustoCalado/Data-Structures-And-Algorithms/blob/master/USP/Analysis-of-Algorithms-and-Data-Structures/resources/Imagens/propriedades-notacoes-omega-teta-oh-2.png)

### Operações com Notação `O`
![operacoes-notacao-oh](https://github.com/AugustoCalado/Data-Structures-And-Algorithms/blob/master/USP/Analysis-of-Algorithms-and-Data-Structures/resources/Imagens/operacoes-notacao-oh.png)
operacoes-notacao-oh

### Revisão Matemática
![resivao-matematica](https://github.com/AugustoCalado/Data-Structures-And-Algorithms/blob/master/USP/Analysis-of-Algorithms-and-Data-Structures/resources/Imagens/resivao-matematica.png)

### Exemplo - Ordenação-por-Inserção 
Rearranjar um vetor A[1 .. n] de modo que ele fique em ordem crescente.
```java
//Ordenação-por-Inserção (A, n)
para j := 2 até n    
	x := A[j]
	i := j−1
	//laço
	enquanto i > 0 e A[i] > x
		A[i+1] := A[i]
		i := i−1
	A[i+1] := x
```

#### Invariantes
- o vetor A[1 .. j−1] é crescente. 
	- Esse invariante é trivialmente verdadeiro na primeira repetição do "para" (pois j = 2 nesse caso). Se o invariante for verdadeiro na última repetição do "para" (quando j = n+1) então nosso problema está resolvido.

#### Analise do Tempo - por *atribuição*
```java
//Ordenação-por-Inserção (A, n)
para j := 2 até n                //n   
	x := A[j]					 // n-1
	i := j−1                     // n-1
	//laço
	enquanto i > 0 e A[i] > x    //
		A[i+1] := A[i]           // 1+2+3+ ...+ n-1
		i := i−1                 // 1+2+3+ ...+ n-1
	A[i+1] := x                  // n-1
```

**Somando os tempos temos:** n^2 + 3n -3

#### Analise do Tempo - por *número de execuções de cada linha*
```java
//Ordenação-por-Inserção (A, n)
para j := 2 até n                //n   
	x := A[j]					 // n-1
	i := j−1                     // n-1
	//laço
	enquanto i > 0 e A[i] > x    // 2+3+ ...+ n
		A[i+1] := A[i]           // 1+2+3+ ...+ n-1
		i := i−1                 // 1+2+3+ ...+ n-1
	A[i+1] := x                  // n-1
```

**Somando os tempos temos:** (n^2 + 7n -8) / 2

## Exemplos

![demonstracao-consumo-tempo](https://github.com/AugustoCalado/Data-Structures-And-Algorithms/blob/master/USP/Analysis-of-Algorithms-and-Data-Structures/resources/Imagens/demonstracao-consumo-tempo-1-20200907.png)

![demonstracao-consumo-tempo](https://github.com/AugustoCalado/Data-Structures-And-Algorithms/blob/master/USP/Analysis-of-Algorithms-and-Data-Structures/resources/Imagens/demonstracao-consumo-tempo-2-20200907.png)

![demonstracao-consumo-tempo](https://github.com/AugustoCalado/Data-Structures-And-Algorithms/blob/master/USP/Analysis-of-Algorithms-and-Data-Structures/resources/Imagens/demonstracao-consumo-tempo-3-20200907.png)

![demonstracao-consumo-tempo](https://github.com/AugustoCalado/Data-Structures-And-Algorithms/blob/master/USP/Analysis-of-Algorithms-and-Data-Structures/resources/Imagens/demonstracao-consumo-tempo-4-20200907.png)
