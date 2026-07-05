# Exercícios Práticos — Pilhas (Stack) em Python

**Nível:** 2º semestre (fundamentos)  
**Conteúdo:** conceito de pilha (TAD), topo, regra **LIFO**, operações **push/pop/peek/is_empty/size**, invariantes, pré/pós-condições, aplicações.

---

## Como trabalhar

- Você pode fazer **1 arquivo `.py` por exercício** (`ex01.py`, `ex02.py`, …) **ou** agrupar por partes (`parte1.py`, `parte2.py`).
- Em todos os exercícios, use `print(...)` para testar.
- **Não use bibliotecas externas.**

---

## Regras do treino

- Pode usar: variáveis, `print`, `if/elif/else`, `for/while`, listas.
- Para a pilha: você pode implementar usando **lista** (`append` e `pop`).
- Quando for operação inválida (ex.: `pop` em pilha vazia), você pode:
  - imprimir uma mensagem e não fazer nada, **ou**
  - lançar `IndexError` com uma mensagem.

---

# Parte 1 — Conceito, topo e LIFO

## Exercício 1 — LIFO na prática (mental)

Imagine uma pilha vazia e execute mentalmente a sequência:

1. push(10)
2. push(20)
3. push(30)
4. pop()
5. push(40)

**Perguntas:**

- Qual é o topo no final?
- Quais valores foram removidos (em ordem)?

---

## Exercício 2 — Topo após cada operação

Para a sequência abaixo, escreva em comentários qual é o topo após cada linha:

- push("A")
- push("B")
- peek()
- pop()
- push("C")
- peek()

---

## Exercício 3 — Pilha no mundo real

Escolha **2 exemplos do mundo real** onde a lógica é LIFO (tipo “pratos”, “desfazer”, “voltar” etc.).  
Explique em 2–3 linhas para cada exemplo por que é LIFO.

---

## Exercício 4 — Quando NÃO é pilha?

Dê um exemplo de situação do mundo real onde **não** faz sentido usar pilha e explique por quê.

---

# Parte 2 — Operações e especificação (pré/pós-condições)

## Exercício 5 — Pré e pós-condição

Complete (em comentário no seu código) as pré/pós-condições de cada operação:

- `push(x)`
- `pop()`
- `peek()`
- `is_empty()`
- `size()`

> Dica: pré-condição é o que precisa ser verdade antes; pós-condição é o que será verdade depois.

---

## Exercício 6 — Invariantes

Escreva (em comentário) **3 invariantes** que sempre devem ser verdade numa pilha.

---

## Exercício 7 — Mostre o “estado interno”

Explique (em comentário) o que seria o “estado interno” de uma pilha implementada com lista.

---

# Parte 3 — Implementando a classe `Pilha`

## Exercício 8 — Classe Pilha (só push e is_empty)

Implemente uma classe `Pilha` com:

- atributo interno `_itens` (lista)
- métodos:
  - `push(item)`
  - `is_empty()`

Teste:

- crie uma pilha
- verifique se está vazia
- faça `push` de 3 itens
- verifique se está vazia de novo

---

## Exercício 9 — Adicione `size()`

Implemente `size()` que retorna quantos itens existem na pilha.
Teste imprimindo o tamanho antes e depois de vários `push`.

---

## Exercício 10 — Adicione `peek()`

Implemente `peek()` que retorna o topo **sem remover**.

- Se estiver vazia, trate o erro (mensagem ou `IndexError`).

Teste:

- empilhe 2 valores
- veja o topo
- veja o topo de novo (deve ser o mesmo)
- imprima o tamanho (deve permanecer igual)

---

## Exercício 11 — Adicione `pop()`

Implemente `pop()` que remove e retorna o topo.

- Se estiver vazia, trate o erro (mensagem ou `IndexError`).

Teste:

- empilhe 3 valores
- faça `pop()` duas vezes
- imprima o topo atual
- imprima o tamanho atual

---

## Exercício 12 — Método `__str__` (opcional, bem simples)

Implemente `__str__(self)` para imprimir a pilha de um jeito amigável, por exemplo:

- `Pilha([10, 20, 30])`

---

## Exercício 13 — Teste de “história da pilha”

Rode este cenário e imprima após cada operação:

1. push(10)
2. push(20)
3. pop()
4. push(30)

Mostre:

- conteúdo interno
- topo
- tamanho

> Objetivo: perceber que “o topo é sempre resultado da última operação que mexeu na pilha”.

---

# Parte 4 — Exercícios de raciocínio com sequência de operações

## Exercício 14 — Previsão do resultado

Sem rodar o código, responda em comentários:

- O que será impresso?

```python
p = Pilha()
p.push(1)
p.push(2)
p.push(3)
print(p.pop())
p.push(4)
print(p.peek())
print(p.size())
```

Depois rode e confira se acertou.

---

## Exercício 15 — Quantos pops são possíveis?

Crie um programa que:

1. empilha 5 números
2. faz pops até a pilha ficar vazia
3. conta quantos pops aconteceram

Imprima a contagem no final.

---

# Parte 5 — Aplicações simples de pilha

## Exercício 16 — Inverter uma palavra

Crie uma função `inverter_string(texto)` que:

1. empilha cada caractere do texto
2. depois desempilha para montar o texto invertido
3. retorna a string invertida

Teste com:

- `"python"`
- `"estrutura"`

---

## Exercício 17 — “Desfazer” (Ctrl+Z) simplificado

Simule um editor bem simples:

- Você terá uma variável `texto = ""`
- Cada ação é adicionar uma palavra no final (ex.: `"oi"`, `"tudo"`, `"bem"`)

Crie uma pilha `historico` onde você empilha o **estado anterior** de `texto` antes de modificar.

Crie funções:

- `digitar(palavra)` → atualiza `texto` (guarde o estado anterior na pilha)
- `desfazer()` → volta para o estado anterior usando `pop` do histórico

Teste:

- digitar 3 palavras
- desfazer 2 vezes
- imprima o texto final

---

## Exercício 18 — Botão “Voltar” do navegador (histórico)

Simule navegação com pilha:

- `historico = Pilha()`
- `pagina_atual = "home"`

Crie:

- `visitar(pagina)`:
  - empilha a página atual
  - muda para a nova página
- `voltar()`:
  - se o histórico estiver vazio, não faz nada
  - senão, volta para a última página (pop)

Teste:

- visitar: "produtos" → "detalhes" → "carrinho"
- voltar 2x
- imprima a página atual

---

## Exercício 19 — Verificador de parênteses (bem básico)

Crie uma função `parenteses_ok(texto)` que retorna `True` se os parênteses `(` e `)` estiverem balanceados, `False` caso contrário.

Regras:

- Ao ver `(`, faça `push`
- Ao ver `)`, precisa existir um `(` para desempilhar; se não existir, falha
- No final, a pilha deve estar vazia

Teste com:

- `"(a+b)"`
- `"((a+b)"`
- `")(a+b)("`

---

# Parte 6 — Mini-desafios (opcionais)

## Exercício 20 — Pilha com limite (capacidade máxima)

Crie `PilhaLimitada(capacidade)`:

- `push` só funciona se `size() < capacidade`
- se estiver cheia, mostre mensagem e não empilhe

Teste com capacidade 3.

---

## Exercício 21 — Duas pilhas: Undo/Redo (opcional)

Crie duas pilhas:

- `undo_stack`
- `redo_stack`

Quando “digitar”, empilhe estado anterior no `undo_stack` e **limpe** o `redo_stack`.  
Quando “desfazer”, mova estado atual para `redo_stack` e recupere do `undo_stack`.  
Quando “refazer”, faça o inverso.

Teste com algumas operações e imprima o texto final.

---

## Extra (reflexão curta)

Em 3–5 linhas, responda: por que “a ordem das operações” é tão importante em pilha?
