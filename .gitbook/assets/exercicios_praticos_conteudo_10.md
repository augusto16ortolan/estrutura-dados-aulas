# Exercícios Práticos — Listas Duplamente Encadeadas (LDE) em Python

**Nível:** 2º semestre (fundamentos)  
**Conteúdo:** nodos com `valor`, `proximo`, `anterior`, referência `head` e (opcional) `tail`, percurso para frente e para trás, inserções/remoções, invariantes e cuidados com ponteiros.

---

## Como trabalhar

- Você pode fazer **1 arquivo `.py` por exercício** (`ex01.py`, `ex02.py`, …) ou agrupar por partes.
- Use `print(...)` para testar tudo.
- Não use bibliotecas externas.

---

## Regras do treino

- Pode usar: variáveis, `print`, `if/elif/else`, `for/while`, funções e POO básica (`class`, `__init__`, `self`).
- Estruturas encadeadas devem funcionar **por referências** (ponteiros), não por índice.
- Em operações inválidas (ex.: remover em lista vazia), você pode:
  - retornar `None`/`False` e imprimir mensagem, **ou**
  - lançar erro (`IndexError` / `ValueError`).

---

# Parte 1 — Conceito e estrutura do nodo

## Exercício 1 — Classe `NodoDuplo`

Crie uma classe `NodoDuplo` com:

- `valor`
- `proximo` (inicia `None`)
- `anterior` (inicia `None`)

Teste:

- crie `n1 = NodoDuplo(10)`
- imprima `n1.valor`, `n1.proximo` e `n1.anterior`

---

## Exercício 2 — Ligação manual (2 nodos)

Crie `n1 = NodoDuplo(10)` e `n2 = NodoDuplo(20)` e ligue corretamente:

- `n1.proximo = n2`
- `n2.anterior = n1`

Imprima:

- `n1.valor`, `n1.proximo.valor`
- `n2.valor`, `n2.anterior.valor`

---

## Exercício 3 — Cadeia de 3 nodos (ida e volta)

Monte manualmente:
`None <- [10] <-> [20] <-> [30] -> None`

Imprima:

1. indo para frente a partir do 10: 10, 20, 30
2. voltando a partir do 30: 30, 20, 10

---

## Exercício 4 — Erro comum: esqueci de ligar o `anterior`

Monte 3 nodos com `proximo` correto, mas **não** preencha `anterior`.
Tente percorrer de trás para frente e responda em comentário:

- Por que não funciona?
- O que faltou manter como invariante?

---

# Parte 2 — Invariantes (regras que não podem quebrar)

## Exercício 5 — Escreva invariantes

Escreva em comentário **4 invariantes** de uma LDE válida.

Sugestões (não copie pronto — escreva com suas palavras):

- `head.anterior` deve ser `None`
- `tail.proximo` deve ser `None`
- se `x.proximo = y`, então `y.anterior = x`
- se a lista estiver vazia, `head == None` e `tail == None`

---

## Exercício 6 — Verificador de consistência (bem simples)

Crie uma função `consistente(head)` que percorre do `head` até o final e verifica:

- se existe `atual.proximo`, então `atual.proximo.anterior` deve ser `atual`

Retorne `True` se estiver tudo certo, senão `False`.

Teste:

- em uma lista correta
- em uma lista “quebrada” de propósito (mexa em um ponteiro)

---

# Parte 3 — Criando a classe `ListaDuplamenteEncadeada`

## Exercício 7 — Estrutura básica

Crie `ListaDuplamenteEncadeada` com:

- `head` (inicia `None`)
- `tail` (inicia `None`)
- `is_empty()` retorna True/False

Teste imprimindo `is_empty()` em uma lista nova.

---

## Exercício 8 — Inserir no início (head)

Implemente `inserir_inicio(valor)` considerando:

- se a lista estiver vazia, `head` e `tail` viram o novo nodo
- senão:
  - `novo.proximo = head`
  - `head.anterior = novo`
  - `head = novo`

Teste inserindo: 30, 20, 10 (nessa ordem)  
A lista deve ficar: `10 <-> 20 <-> 30`

---

## Exercício 9 — Inserir no final (tail)

Implemente `inserir_final(valor)` considerando:

- se vazia, `head` e `tail` viram o novo nodo
- senão:
  - `novo.anterior = tail`
  - `tail.proximo = novo`
  - `tail = novo`

Teste inserindo no final: 10, 20, 30  
A lista deve ficar: `10 <-> 20 <-> 30`

---

## Exercício 10 — Percorrer para frente e para trás

Implemente:

- `imprimir_frente()` → do `head` até `None`
- `imprimir_tras()` → do `tail` até `None`

Mostre no formato:

- `None <- 10 <-> 20 <-> 30 -> None`

---

## Exercício 11 — Tamanho (size)

Implemente `size()` que retorna quantos nodos existem.

Teste:

- vazia (0)
- com 1 elemento (1)
- com 3 elementos (3)

---

# Parte 4 — Remoções (onde LDE brilha mais)

## Exercício 12 — Remover do início

Implemente `remover_inicio()`:

- se vazia: trate
- se tem 1 elemento: `head = tail = None`
- senão:
  - `head = head.proximo`
  - `head.anterior = None`

Retorne o valor removido (se remover).

Teste removendo de `10 <-> 20 <-> 30`:

- remove 10, sobra `20 <-> 30`

---

## Exercício 13 — Remover do final

Implemente `remover_final()`:

- se vazia: trate
- se tem 1 elemento: `head = tail = None`
- senão:
  - `tail = tail.anterior`
  - `tail.proximo = None`

Retorne o valor removido.

Teste removendo de `10 <-> 20 <-> 30`:

- remove 30, sobra `10 <-> 20`

---

## Exercício 14 — Remover um valor (primeira ocorrência)

Implemente `remover_valor(valor)` que remove a primeira ocorrência:

- se lista vazia: retorna False
- se for o `head`: use `remover_inicio`
- se for o `tail`: use `remover_final`
- se estiver no meio, ajuste os dois lados:
  - `anterior.proximo = proximo`
  - `proximo.anterior = anterior`

Retorne True/False.

Teste removendo:

- 20 de `10 <-> 20 <-> 30`
- 10 (head)
- 30 (tail)
- 99 (não existe)

---

## Exercício 15 — Remoção no meio sem “achar o anterior” (reflexão)

Responda em comentário:

- Por que na LDE é mais fácil remover no meio do que na lista simplesmente encadeada?

---

# Parte 5 — Busca e navegação bidirecional

## Exercício 16 — Buscar nodo por valor

Implemente `buscar(valor)` que retorna o **nodo** (ou `None`).

Teste:

- buscando valor existente
- buscando valor inexistente

---

## Exercício 17 — “Avançar” e “Voltar”

Crie uma função `navegar()` (ou código de teste) que:

- pegue um ponteiro `atual = head`
- avance 2 vezes usando `atual = atual.proximo`
- depois volte 1 vez usando `atual = atual.anterior`
  Imprima o valor em cada passo.

> Objetivo: sentir na prática o “ir e voltar” na lista.

---

# Parte 6 — Conversões (facilitam testar)

## Exercício 18 — `from_list(lista_python)`

Implemente um método `from_list(valores)` que:

- recebe uma lista do Python, ex.: `[10, 20, 30]`
- monta a LDE na mesma ordem
- atualiza `head` e `tail`

Teste imprimindo para frente e para trás.

---

## Exercício 19 — `to_list_frente()` e `to_list_tras()`

Implemente:

- `to_list_frente()` retorna `[10, 20, 30]`
- `to_list_tras()` retorna `[30, 20, 10]`

Use isso para validar se seus ponteiros estão corretos.

---

# Parte 7 — Debug: erros clássicos de ponteiro

## Exercício 20 — Bug: `head.anterior` não virou None

Crie uma lista com 2 elementos e remova o início.
Propositalmente, **não** ajuste `head.anterior = None`.

1. Percorra para trás e observe o que acontece (pode dar comportamento estranho).
2. Responda em comentário por que isso quebra a lista.

---

## Exercício 21 — Bug: “perdi” a cauda (tail)

Crie uma lista com 3 elementos.
Ao inserir no final, propositalmente **não** atualize `tail`.

1. Imprima para frente e compare com `tail`.
2. Responda em comentário: por que `tail` fica incorreta e como isso afeta `imprimir_tras()`?

---

## Exercício 22 — Checagem final de consistência

Use sua função `consistente(head)` (do Exercício 6) depois de:

- várias inserções (início e fim)
- várias remoções (início, fim, meio)

Imprima “OK” ou “QUEBRADA” conforme o resultado.

---

# Mini-projeto (opcional) — Histórico de páginas (Voltar/Avançar)

Modele um navegador usando LDE:

- cada nodo é uma página (string)
- você tem um ponteiro `atual` (nodo atual)

Regras sugeridas:

1. `visitar(pagina)`:
   - se você estiver no meio do histórico (ou seja, existe “próximo”),
     você deve **descartar** o que está à frente antes de visitar a nova página.
   - crie nodo novo depois do atual e mova `atual` para ele.
2. `voltar()`:
   - se existir `atual.anterior`, volte
3. `avancar()`:
   - se existir `atual.proximo`, avance

Teste:

- visitar "home" -> "produtos" -> "detalhes"
- voltar 1x
- visitar "carrinho" (isso deve apagar o “avançar” antigo)
- tente avançar (não deve ir)
- imprima a página atual a cada passo

---
