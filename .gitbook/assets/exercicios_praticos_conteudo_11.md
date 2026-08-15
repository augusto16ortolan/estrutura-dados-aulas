# Exercícios Práticos — Algoritmos de Ordenação

**Nível:** 2º semestre (fundamentos)  
**Objetivo:** entender o que é ordenar, por que ordenar é importante, praticar os
3 algoritmos básicos e reconhecer o Merge Sort como uma estratégia mais
eficiente baseada em divisão e conquista:

- Bubble Sort
- Selection Sort
- Insertion Sort
- Merge Sort (desafio opcional)

---

## Como trabalhar

- Você pode fazer **1 arquivo `.py` por exercício** (`ex01.py`, `ex02.py`, …) ou agrupar por partes.
- Use `print(...)` para testar.
- **Não use** `sorted()` nem `.sort()` nos exercícios de implementação (a ideia é treinar o algoritmo).

---

## Regras do treino

- Pode usar: variáveis, `print`, `if/elif/else`, `for/while`, listas, funções.
- Sem bibliotecas externas.
- Mantenha o código legível e organizado.

---

# Parte 1 — Conceitos e raciocínio

## Exercício 1 — O que significa ordenar?

Em comentário no seu código, responda (2–4 linhas):

1. O que é “ordenar dados”?
2. O que muda e o que não muda quando ordenamos uma lista?

---

## Exercício 2 — Antes e depois

Dada a lista:
`[8, 3, 5, 1]`

1. Escreva (em comentário) como ficaria em **ordem crescente**.
2. Escreva (em comentário) como ficaria em **ordem decrescente**.

---

## Exercício 3 — Por que ordenar é importante?

Em comentário, escreva **3 motivos** (bem curtos) pelos quais ordenar ajuda em sistemas reais.

---

## Exercício 4 — Comparar e trocar

Crie um código que:

1. tenha `a = 10`, `b = 7`
2. se `a > b`, troque os valores (swap)
3. imprima `a` e `b` no final

> Dica: `a, b = b, a`

---

## Exercício 5 — “Já está ordenado?”

Crie uma função `esta_ordenada(lista)` que retorna `True` se a lista estiver em ordem crescente e `False` caso contrário.

Teste com:

- `[1, 2, 3, 4]` (True)
- `[1, 3, 2, 4]` (False)
- `[]` (True)
- `[5]` (True)

---

# Parte 2 — Bubble Sort

## Exercício 6 — Implementar `bubble_sort`

Crie a função `bubble_sort(lista)` que ordena a lista em ordem crescente (pode modificar a lista original).

Teste com:

- `[8, 3, 5, 1]`
- `[4, 1, 3, 2]`
- `[1, 2, 3, 4]`

Imprima a lista antes e depois.

---

## Exercício 7 — Mostrar “passadas” do Bubble

Crie `bubble_sort_mostrando(lista)` que imprime a lista a cada passada completa (cada `i`).

Exemplo (não precisa ser exatamente assim):

- Passada 1: ...
- Passada 2: ...
- ...

Teste com `[8, 3, 5, 1]`.

---

## Exercício 8 — Contar comparações e trocas

Crie `bubble_sort_com_contagem(lista)` que retorna:

- a lista ordenada
- quantidade de comparações
- quantidade de trocas

> Você pode retornar como tupla: `return lista, comparacoes, trocas`

Teste com:

- `[8, 3, 5, 1]`
- `[1, 2, 3, 4]` (compare o número de trocas)

---

## Exercício 9 — Bubble Sort “otimizado” (parar cedo)

Melhore o Bubble Sort usando uma flag `trocou`:

- se em uma passada não houver nenhuma troca, pare o algoritmo.

Crie `bubble_sort_otimizado(lista)` e compare a contagem com o exercício 8 em:

- lista já ordenada
- lista invertida

---

# Parte 3 — Selection Sort

## Exercício 10 — Implementar `selection_sort`

Crie `selection_sort(lista)` para ordenar em ordem crescente.

Teste com:

- `[8, 3, 5, 1]`
- `[29, 10, 14, 37, 13]`

Imprima antes e depois.

---

## Exercício 11 — Mostrar escolha do menor

Crie `selection_sort_mostrando(lista)` que a cada posição `i` imprime:

- qual foi o índice do menor encontrado
- a lista depois da troca

Teste com `[8, 3, 5, 1]`.

---

## Exercício 12 — Contar comparações e trocas no Selection

Crie `selection_sort_com_contagem(lista)` que retorna:

- lista ordenada
- comparações
- trocas

Teste com `[8, 3, 5, 1]` e compare com o Bubble (ex. 8).

---

# Parte 4 — Insertion Sort

## Exercício 13 — Implementar `insertion_sort`

Crie `insertion_sort(lista)` (ordem crescente).

Teste com:

- `[8, 3, 5, 1]`
- `[5, 1, 4, 2, 8]`

Imprima antes e depois.

---

## Exercício 14 — Mostrar inserções (como “cartas na mão”)

Crie `insertion_sort_mostrando(lista)` que imprime a lista a cada inserção do elemento atual.

Teste com `[8, 3, 5, 1]`.

---

## Exercício 15 — Quase ordenada vs bagunçada

Teste o `insertion_sort` em duas listas:

- `A = [1, 2, 3, 5, 4, 6, 7, 8]` (quase ordenada)
- `B = [8, 7, 6, 5, 4, 3, 2, 1]` (invertida)

Em comentário, responda:

- em qual delas você acha que o Insertion Sort tende a “sofrer” mais? por quê?

---

## Exercício 16 — Contar “movimentações”

Crie `insertion_sort_com_contagem(lista)` que conta:

- quantas comparações você fez
- quantas “movimentações” (quantas vezes você fez `lista[j + 1] = lista[j]`)

Teste com:

- lista quase ordenada
- lista invertida
  Compare os números.

---

# Parte 5 — Comparação e escolha do algoritmo

## Exercício 17 — Tabela rápida (teórica)

Crie uma tabela (em comentário) com 3 linhas (Bubble, Selection, Insertion) e responda:

- qual compara vizinhos?
- qual escolhe o menor da parte não ordenada?
- qual “insere” o elemento na posição correta?

---

## Exercício 18 — Qual escolher? (cenários)

Para cada cenário abaixo, escolha o algoritmo mais adequado entre os três e explique em 1–2 linhas:

1. A lista é pequena e você quer algo fácil de implementar/entender.
2. A lista está quase toda ordenada, só alguns itens estão fora do lugar.
3. Você quer minimizar trocas, mas não liga muito para muitas comparações.

---

## Exercício 19 — Mesmo problema, estratégias diferentes

Crie um arquivo que:

1. tenha a mesma lista original (ex.: `[9, 4, 6, 2, 7]`)
2. faça cópias dela (para não “estragar” a original)
3. ordene com Bubble, Selection e Insertion
4. imprima o resultado de cada um

Confirme que os três produzem a mesma lista ordenada.

---

# Parte 6 — Exercícios práticos de aplicação

## Exercício 20 — Ordenar nomes (strings)

Dada a lista:
`nomes = ["bia", "ana", "carlos", "davi"]`

1. Ordene em ordem alfabética usando **um dos seus algoritmos** (crescente).
2. Imprima antes e depois.

> Dica: comparação de strings funciona com `>` e `<`.

---

## Exercício 21 — Ordenar por tamanho da palavra (desafio leve)

Dada a lista:
`palavras = ["python", "if", "lista", "ordenacao", "for"]`

Ordene por **tamanho crescente** (menor palavra primeiro), usando **Bubble Sort** e comparando `len(...)`.

Imprima antes e depois.

---

## Exercício 22 — Ordenar notas junto com nomes (lista de dicionários)

Crie uma lista:

```python
alunos = [
    {"nome": "Ana", "nota": 8},
    {"nome": "João", "nota": 6},
    {"nome": "Bia", "nota": 9},
]
```

Ordene por `nota` crescente usando **Selection Sort** (comparando `alunos[j]["nota"]`).
Imprima a lista final.

---

## Exercício 23 — Ordenar e depois buscar (integração)

Faça:

1. Crie uma lista de números aleatória (fixa no código), ex.: `[12, 3, 7, 4, 10]`
2. Ordene com um dos seus algoritmos
3. Após ordenar, implemente `busca_linear(lista, x)` e procure por um valor

Em comentário, responda:

- por que ordenar pode ajudar a usar buscas mais eficientes depois?

---

# Parte 7 — Mini-desafios (opcionais)

## Exercício 24 — Crescente e decrescente

Escolha um algoritmo (Bubble, Selection ou Insertion) e adapte para:

- ordenar crescente
- ordenar decrescente

> Dica: dá para inverter o sinal da comparação.

---

## Exercício 25 — “Top 3” após ordenar

Dada uma lista de pontuações:
`pontos = [120, 450, 300, 200, 500, 90]`

1. Ordene crescente
2. Imprima os 3 maiores valores (os 3 do final)

---

## Exercício 26 — Relatório de desempenho (conceito)

Com o que você mediu nos exercícios de contagem:

- escreva em comentário um mini-relatório (5–8 linhas) dizendo:
  - qual algoritmo fez mais trocas em uma lista invertida?
  - qual algoritmo foi melhor em uma lista quase ordenada?
  - o que você aprendeu sobre comparar estratégias?

---

## Exercício 27 — Entendendo o Merge Sort (opcional)

Em comentário, explique com suas palavras:

- por que listas com 1 elemento já estão ordenadas
- o que significa dividir a lista em metades
- qual é o papel da etapa de intercalação (`merge`)

---

## Exercício 28 — Implementar `merge_sort` (desafio)

Implemente `merge_sort(lista)` usando duas funções:

- `merge_sort(lista)`, que divide a lista e chama a si mesma
- `merge(esquerda, direita)`, que intercala duas listas já ordenadas

Teste com:

- `[8, 3, 5, 1, 7, 2]`
- `[4, 1, 3, 2]`
- `[]`
- `[5]`

Confira se a função retorna uma nova lista ordenada.

---
