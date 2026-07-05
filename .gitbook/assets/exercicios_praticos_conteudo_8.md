# Exercícios Práticos — Nodos e Conceitos de Listas Lineares

**Nível:** 2º semestre (fundamentos)  
**Conteúdo:** nodo (valor + referência), lista linear (sequência), percurso nodo-a-nodo, estado e invariantes, impacto de “quebrar” ligações.

---

## Como trabalhar

- Faça **1 arquivo `.py` por exercício** (`ex01.py`, `ex02.py`, …) ou agrupe por partes.
- Use `print(...)` para testar tudo.
- Não use bibliotecas externas.

---

## Regras do treino

- Use apenas: variáveis, `print`, `if/elif/else`, `for/while`, funções, e POO básica (`class`, `__init__`, `self`).
- Você pode usar `None` para indicar “sem próximo nodo”.
- Foque em **entender ligações** entre nodos (ponteiros/referências).

---

# Parte 1 — O que é um nodo (valor + referência)

## Exercício 1 — Classe Nodo (base)

Crie uma classe `Nodo` com:

- `valor`
- `proximo` (começa como `None`)

Teste criando:

- `n1 = Nodo(10)`
- imprima `n1.valor` e `n1.proximo`

---

## Exercício 2 — Ligação manual (2 nodos)

Crie `n1 = Nodo(10)` e `n2 = Nodo(20)`.  
Ligue `n1` ao `n2` (ou seja, faça `n1.proximo = n2`).

Imprima:

- `n1.valor`
- `n1.proximo.valor`

---

## Exercício 3 — Cadeia de 3 nodos

Crie `n1(10)`, `n2(20)`, `n3(30)` e ligue para formar:
`10 -> 20 -> 30 -> None`

Imprima:

- o valor de cada nodo acessando “na mão” (`n1`, `n1.proximo`, `n1.proximo.proximo`)
- o `proximo` do último (deve ser `None`)

---

## Exercício 4 — Debug de indentação

O código abaixo está errado. Corrija, rode e teste com 3 nodos encadeados:

```python
class Nodo:
def __init__(self, valor):
self.valor = valor
self.proximo = None
```

---

# Parte 2 — Lista linear (sequência e percurso)

## Exercício 5 — Percorrer e imprimir (travessia)

Crie uma função `imprimir_lista(head)` que:

- recebe o primeiro nodo (`head`)
- percorre do início até `None`
- imprime os valores em uma linha, por exemplo:
  `10 -> 20 -> 30 -> None`

**Requisito:** use um ponteiro auxiliar, por exemplo `atual = head`, e caminhe com `atual = atual.proximo`.

---

## Exercício 6 — Contar nodos

Crie `contar_nodos(head)` que retorna quantos nodos existem na lista.

Teste com:

- lista vazia (`head = None`) → deve retornar 0
- lista com 3 nodos → deve retornar 3

---

## Exercício 7 — Somar valores

Crie `somar_valores(head)` que retorna a soma de todos os valores.

Teste com `10 -> 20 -> 30 -> None` (esperado: 60).

---

## Exercício 8 — Buscar valor (retornar True/False)

Crie `contem(head, valor)`:

- retorna `True` se existir um nodo com aquele valor
- senão retorna `False`

Teste com valores que existem e não existem.

---

## Exercício 9 — Encontrar o último nodo

Crie `ultimo(head)` que retorna o **último nodo** (ou `None` se lista vazia).

Teste:

- em lista vazia
- em lista com 1 nodo
- em lista com 3 nodos

---

# Parte 3 — Estado e invariantes (lista “válida”)

## Exercício 10 — Entendendo invariantes (teórico)

Responda em comentário (no seu `.py`):

1. O que é “estado” de uma lista linear?
2. Cite **3 invariantes** que fazem uma lista encadeada simples ser considerada válida.

---

## Exercício 11 — Verificar invariante “último aponta para None”

Crie uma função `ultimo_aponta_para_none(head)` que retorna:

- `True` se a lista estiver vazia **ou** se o último nodo tiver `proximo == None`
- `False` caso contrário

> Dica: percorra até o final.

---

## Exercício 12 — Detectar “quebra” por None no meio (caso simples)

Crie a lista `10 -> 20 -> 30 -> None`.  
Agora faça de propósito: `n2.proximo = None`.

1. Use `imprimir_lista(head)` e veja o que acontece.
2. Responda em comentário: qual parte da lista foi “perdida”? Por quê?

---

# Parte 4 — Como a ordem muda tudo (mexendo em ponteiros)

## Exercício 13 — Inserir após um valor (inserção no meio)

Crie uma função `inserir_depois(head, valor_alvo, novo_valor)` que:

- procura o primeiro nodo com `valor == valor_alvo`
- insere um novo nodo **depois** dele (ajustando referências)
- retorna `True` se inseriu, `False` se não encontrou

Teste:

- Inserir 25 depois do 20 em `10 -> 20 -> 30 -> None`
- A lista deve virar `10 -> 20 -> 25 -> 30 -> None`

---

## Exercício 14 — Remover “o próximo” (remoção no meio)

Crie `remover_proximo(head, valor_alvo)` que:

- encontra o nodo com `valor == valor_alvo`
- remove o nodo **logo depois** dele (se existir)
- retorna `True` se removeu, `False` caso não exista “próximo” ou não encontrou alvo

Teste:

- Em `10 -> 20 -> 30 -> None`, remova o próximo do 20 (remove 30)
- Resultado: `10 -> 20 -> None`

---

## Exercício 15 — Trocar ligações (experimento)

Crie `10 -> 20 -> 30 -> None`.  
Agora mude para `10 -> 30 -> None` (pulando o 20) **sem apagar o 20**.

1. Imprima a lista a partir do head.
2. Responda em comentário:
   - O nodo 20 ainda existe?
   - Por que ele fica “inacessível” a partir do head?

---

# Parte 5 — Funções utilitárias e construção de lista

## Exercício 16 — Converter lista do Python em lista de nodos

Crie `from_list(valores)` que recebe uma lista do Python, por exemplo `[10, 20, 30]` e retorna o `head` encadeado:
`10 -> 20 -> 30 -> None`

Teste imprimindo com `imprimir_lista`.

---

## Exercício 17 — Converter lista de nodos para lista do Python

Crie `to_list(head)` que percorre a lista encadeada e retorna uma lista do Python com os valores.

Teste:

- construa com `from_list([1,2,3])`
- converta com `to_list(head)` e imprima o resultado

---

## Exercício 18 — Tamanho e soma usando `to_list` (comparação)

Usando `to_list(head)`, calcule:

- tamanho (usando `len`)
- soma (usando um `for`, sem `sum`)

Depois responda em comentário:

- Qual abordagem você achou mais clara: percorrer nodos direto ou converter para list?

---

# Parte 6 — Mini-desafios (opcionais, bem acessíveis)

## Exercício 19 — Representação “bonita”

Melhore `imprimir_lista(head)` para que:

- se `head` for `None`, imprima: `Lista vazia`

---

## Exercício 20 — Concatenar duas listas (juntar no final)

Crie `concatenar(head1, head2)` que:

- se `head1` for `None`, retorna `head2`
- senão, encontra o último de `head1` e liga ao `head2`
- retorna o head final

Teste:

- `head1 = from_list([1,2])`
- `head2 = from_list([3,4])`
- resultado deve ser `1 -> 2 -> 3 -> 4 -> None`

---

## Exercício 21 — Fila de músicas (exemplo de lista linear)

Modele uma “fila de músicas” como lista de nodos:

- cada nodo guarda o nome da música (string)
- `head` é a música atual

Faça:

1. `from_list(["Música A", "Música B", "Música C"])`
2. imprima a sequência
3. “pule para a próxima” (faça `head = head.proximo`)
4. imprima de novo (deve começar da música B)

---

## Exercício 22 — Reflexão final (comentário)

Escreva em 4–6 linhas:

- Por que em estruturas com nodos você não “pula direto por índice” como em listas normais?
- O que pode acontecer se você errar uma referência (ponteiro) ao inserir/remover?

---
