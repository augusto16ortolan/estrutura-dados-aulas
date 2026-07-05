# Exercícios Práticos — Filas (Queue) em Python

**Nível:** 2º semestre (fundamentos)  
**Conteúdo:** conceito de fila (TAD), **frente/início** e **fim/final**, regra **FIFO**, operações `enqueue`, `dequeue`, `front`, `is_empty`, `size`, invariantes e aplicações.

---

## Como trabalhar

- Você pode fazer **1 arquivo `.py` por exercício** (`ex01.py`, `ex02.py`, ...) ou agrupar por partes.
- Use `print(...)` para testar cada etapa.
- Não use bibliotecas externas.

---

## Regras do treino

- Pode usar: variáveis, `print`, `if/elif/else`, `for/while`, listas.
- Para implementar a fila, pode usar lista com `append` e `pop(0)`.
- Quando uma operação não puder ser feita (ex.: `dequeue` em fila vazia), você pode:
  - imprimir uma mensagem e não alterar nada, **ou**
  - lançar `IndexError` com uma mensagem.

---

# Parte 1 — Conceitos: FIFO, frente e fim

## Exercício 1 — FIFO na prática (mental)

Imagine uma fila vazia e execute mentalmente:

1. enqueue(10)
2. enqueue(20)
3. enqueue(30)
4. dequeue()
5. enqueue(40)

**Perguntas:**

- Quem está na **frente** no final?
- Quem está no **fim** no final?
- Qual valor saiu no `dequeue()`?

---

## Exercício 2 — Frente após cada operação

Complete em comentários qual é o valor retornado por `front()` após cada passo:

- enqueue("A")
- enqueue("B")
- front()
- dequeue()
- enqueue("C")
- front()

---

## Exercício 3 — Fila no mundo real

Dê **2 exemplos** do mundo real que seguem FIFO e explique em 2–3 linhas cada.

---

## Exercício 4 — Quando NÃO é FIFO?

Dê 1 exemplo onde FIFO não funciona bem e explique por quê.

---

# Parte 2 — Estado, invariantes e especificação (pré/pós-condições)

## Exercício 5 — Estado interno

Escreva em comentário:

- O que é o “estado interno” de uma fila implementada com lista?

---

## Exercício 6 — Invariantes

Escreva em comentário **4 invariantes** de uma fila (regras que sempre devem ser verdade).

---

## Exercício 7 — Pré e pós-condições (complete)

Complete em comentários as pré/pós-condições de:

- `enqueue(x)`
- `dequeue()`
- `front()`
- `is_empty()`
- `size()`

---

# Parte 3 — Implementando a classe `Fila`

## Exercício 8 — Comece a classe (enqueue + is_empty)

Crie uma classe `Fila` com:

- atributo interno `_itens` (lista)
- métodos:
  - `enqueue(item)` (adiciona no final)
  - `is_empty()` (retorna True/False)

Teste:

- crie uma fila
- confira se está vazia
- faça `enqueue` de 3 itens
- confira se está vazia novamente

---

## Exercício 9 — Implemente `size()`

Adicione `size()` que retorna a quantidade de itens na fila.
Teste imprimindo antes e depois de enqueues.

---

## Exercício 10 — Implemente `front()`

Adicione `front()` que retorna o item do início **sem remover**.

- Se estiver vazia, trate o erro (mensagem ou `IndexError`).

Teste:

- enqueue 2 valores
- `front()` duas vezes (deve retornar o mesmo)
- `size()` (deve continuar igual)

---

## Exercício 11 — Implemente `dequeue()`

Adicione `dequeue()` que remove e retorna o item do início.

- Se estiver vazia, trate o erro.

Teste:

- enqueue 3 valores
- dequeue 2 vezes
- imprima `front()` e `size()`

---

## Exercício 12 — Método `__str__` (opcional)

Implemente `__str__(self)` para imprimir algo como:

- `Fila([10, 20, 30])`

---

## Exercício 13 — “História” da fila (print após cada operação)

Execute e imprima após cada operação:

1. enqueue(10)
2. enqueue(20)
3. enqueue(30)
4. dequeue()
5. enqueue(40)

Mostre:

- conteúdo interno
- frente (front)
- tamanho

---

# Parte 4 — Raciocínio com sequência de operações

## Exercício 14 — Previsão do resultado

Sem rodar o código, escreva em comentários: **o que será impresso?**

```python
f = Fila()
f.enqueue(1)
f.enqueue(2)
f.enqueue(3)
print(f.front())
print(f.dequeue())
f.enqueue(4)
print(f.front())
print(f.size())
```

Depois rode e confira.

---

## Exercício 15 — Quantos dequeues são possíveis?

Crie um programa que:

1. enqueue 5 números
2. faz `dequeue()` até a fila ficar vazia
3. conta quantos `dequeue()` aconteceram

Imprima a contagem.

---

## Exercício 16 — “Dequeue” seguro

Crie um método `dequeue_seguro()` que:

- se estiver vazia, retorna `None`
- senão, faz o dequeue normal

Teste chamando quando a fila está vazia e quando tem itens.

---

# Parte 5 — Aplicações simples (bem “vida real”)

## Exercício 17 — Fila de impressão

Simule uma fila de impressão:

- cada `enqueue` é um documento (string)
- cada `dequeue` é “imprimir” o documento

Crie um programa que:

1. adiciona 4 documentos
2. imprime (dequeue) 2 documentos
3. adiciona mais 1 documento
4. imprime todos até esvaziar

---

## Exercício 18 — Fila de atendimento (senhas)

Simule um atendimento por senha:

- `enqueue("A001")`, `enqueue("A002")`, etc.
- `dequeue()` atende a próxima senha

Regras:

- se tentar atender quando a fila está vazia, mostre uma mensagem “Sem clientes”.

---

## Exercício 19 — Fila de tarefas (processamento)

Simule uma fila de tarefas (strings):

- `"enviar_email"`, `"gerar_relatorio"`, `"backup"`, etc.

Crie uma função `processar_tarefas(fila)` que:

- enquanto a fila não estiver vazia, faz dequeue e imprime:
  - `Processando: <tarefa>`

---

## Exercício 20 — Mensagens (FIFO)

Dada a lista de mensagens (na ordem que chegaram):

```python
mensagens = ["oi", "tudo bem?", "vamos estudar", "ok"]
```

1. Enfileire todas na fila.
2. Remova uma por uma, imprimindo:

- `Entregando: <mensagem>`

---

# Parte 6 — Desempenho e alternativa simples (opcional)

## Exercício 21 — Observação de desempenho (conceito)

Responda em comentário:

- Por que `pop(0)` pode ficar mais lento quando a fila cresce muito?

> (Dica: o que acontece com os índices quando removemos o item 0?)

---

## Exercício 22 — Fila com “ponteiro de início” (opcional)

Implemente uma fila alternativa `FilaComIndice` com:

- `_itens` (lista)
- `_inicio` (inteiro começando em 0)

Ideia:

- `enqueue(x)` → append normal
- `front()` → `_itens[_inicio]`
- `dequeue()` → pega `_itens[_inicio]` e faz `_inicio += 1` (sem `pop(0)`)

Regras:

- `is_empty()` deve considerar `_inicio` e o tamanho da lista.
- (Opcional) quando `_inicio` ficar grande, você pode “limpar” a lista para economizar memória.

---

# Mini-projeto (opcional) — Simulador de caixa de supermercado

Crie uma fila de clientes, onde cada cliente é um dicionário:

```python
{"nome": "Ana", "itens": 5}
```

Regras:

1. `enqueue(cliente)` adiciona ao final.
2. `dequeue()` atende o próximo.
3. Um atendimento reduz `itens` do cliente até 0 (pode ser por “rodadas”).
4. Quando `itens` chegar a 0, o cliente sai da fila definitivamente.

Imprima o passo a passo do atendimento.

---
