# Exercícios Práticos — Listas Simplesmente Encadeadas (LSE) em Python

**Nível:** 2º semestre (fundamentos)  
**Conteúdo:** nodos, `head`, referências para o próximo, último apontando para `None`, percurso sequencial, inserção/remoção e impacto no desempenho.

---

## Como trabalhar

- Você pode fazer **1 arquivo `.py` por exercício** (`ex01.py`, `ex02.py`, ...) ou agrupar por partes.
- Use `print(...)` para testar tudo.
- Não use bibliotecas externas.

---

## Regras do treino

- Pode usar: variáveis, `print`, `if/elif/else`, `for/while`, listas (para testes), funções e POO básica (`class`, `__init__`, `self`).
- A lista encadeada deve funcionar **por referências**, não por índices.

---

# Parte 1 — Nodo, head e encadeamento

## Exercício 1 — Classe `Nodo`

Crie uma classe `Nodo` com:

- `valor`
- `proximo` (inicia como `None`)

Teste:

- crie `n1 = Nodo(10)`
- imprima `n1.valor` e `n1.proximo`

---

## Exercício 2 — Encadeamento manual

Crie `n1 = Nodo(10)` e `n2 = Nodo(20)` e faça `n1.proximo = n2`.

Imprima:

- `n1.valor`
- `n1.proximo.valor`

---

## Exercício 3 — Cadeia de 3 nodos

Crie `10 -> 20 -> 30 -> None` e imprima os valores acessando:

- `head.valor`
- `head.proximo.valor`
- `head.proximo.proximo.valor`

Depois imprima `head.proximo.proximo.proximo` (deve ser `None`).

---

## Exercício 4 — Por que não tem índice?

Responda em comentário (3–5 linhas):

- Por que em LSE não faz sentido falar “pega o elemento do índice 7” sem percorrer?

---

# Parte 2 — Percurso (base de tudo)

## Exercício 5 — Função `imprimir_lista(head)`

Crie uma função que percorre a lista e imprime assim:
`10 -> 20 -> 30 -> None`

Requisito:

- use um ponteiro `atual = head`
- enquanto `atual != None`, imprima e avance `atual = atual.proximo`

---

## Exercício 6 — Contar elementos

Crie `contar(head)` que retorna quantos nodos existem.

Teste:

- `head = None` → 0
- `10 -> 20 -> 30` → 3

---

## Exercício 7 — Somar valores

Crie `somar(head)` que retorna a soma de todos os valores da lista.

Teste com `10 -> 20 -> 30` (esperado: 60).

---

## Exercício 8 — Buscar (True/False)

Crie `contem(head, valor)` que retorna `True` se existir, senão `False`.

Teste com:

- valor que existe
- valor que não existe

---

## Exercício 9 — Encontrar último nodo

Crie `ultimo(head)` que retorna o último nodo (ou `None` se lista vazia).

Teste com:

- lista vazia
- lista com 1 elemento
- lista com 3 elementos

---

# Parte 3 — Criando uma classe `ListaEncadeada`

## Exercício 10 — Estrutura básica

Crie uma classe `ListaEncadeada` com:

- atributo `head` (começa como `None`)
- método `is_empty()` (retorna True se `head` for `None`)

Teste:

- crie a lista
- imprima `is_empty()` (deve ser True)

---

## Exercício 11 — Inserir no início (rápido)

Implemente `inserir_inicio(valor)`:

1. cria `novo = Nodo(valor)`
2. `novo.proximo = self.head`
3. `self.head = novo`

Teste inserindo: 30, 20, 10 (nessa ordem)  
Imprima a lista e confirme: `10 -> 20 -> 30 -> None`

---

## Exercício 12 — Imprimir como método

Crie `imprimir()` dentro da classe para mostrar:
`10 -> 20 -> 30 -> None`

---

## Exercício 13 — Tamanho como método

Crie `tamanho()` na classe para retornar o número de nodos.

---

# Parte 4 — Inserção no final e impacto

## Exercício 14 — Inserir no final (precisa percorrer)

Implemente `inserir_final(valor)`:

- Se a lista estiver vazia, o `head` vira o novo nodo.
- Senão, percorra até o último e faça `ultimo.proximo = novo`.

Teste:

- Comece vazio
- Inserir no final: 10, 20, 30
- Imprima e confirme a ordem

---

## Exercício 15 — Comparação de custo (teórico)

Responda em comentário:

- Por que inserir no início é “rápido” e inserir no final fica mais “custoso” conforme cresce?

---

# Parte 5 — Remoções

## Exercício 16 — Remover do início (rápido)

Implemente `remover_inicio()`:

- Se estiver vazia, trate (retorne `None` ou mostre mensagem)
- Senão:
  - guarde o valor do `head`
  - atualize `self.head = self.head.proximo`
  - retorne o valor removido

Teste:

- crie `10 -> 20 -> 30`
- remova início uma vez
- imprima lista (deve virar `20 -> 30 -> None`)

---

## Exercício 17 — Remover por valor (meio/final)

Implemente `remover_valor(valor)` que remove a **primeira ocorrência**:

- Se lista vazia: retorna False
- Se o `head.valor == valor`: atualize o head e retorne True
- Senão:
  - percorra mantendo `anterior` e `atual`
  - ao achar, faça `anterior.proximo = atual.proximo`
  - retorne True
- Se não achar: retorne False

Teste:

- remova 20 de `10 -> 20 -> 30`
- remova 30 de `10 -> 20 -> 30`
- tente remover 99 (não existe)

---

## Exercício 18 — Remover no final (usando remover_valor)

Crie `remover_final()`:

- Se vazia: trate
- Se só tiver 1 nodo: head vira None
- Senão, percorra até o penúltimo e ajuste para `None`

Teste com listas de tamanho 1, 2 e 3.

---

## Exercício 19 — “Quebrei a lista” (debug)

Monte `10 -> 20 -> 30 -> None`.  
Agora faça propositalmente: `head.proximo = None`

1. Imprima a lista
2. Responda em comentário: o que aconteceu com os nodos 20 e 30 “a partir do head”?

---

# Parte 6 — Operações clássicas usando percurso

## Exercício 20 — Pegar por posição (sequencial)

Implemente `get(pos)` na classe:

- `pos` começa em 0
- percorra avançando um contador
- quando contador == pos, retorna o valor
- se `pos` for inválida, retorne `None`

Teste:

- `get(0)`, `get(1)`, `get(2)` em `10 -> 20 -> 30`
- `get(5)` deve retornar `None`

---

## Exercício 21 — Inserir em posição

Implemente `inserir_em(pos, valor)`:

- Se `pos == 0`, use inserir_inicio
- Senão, percorra até o nodo anterior à posição
- Ajuste ponteiros:
  - `novo.proximo = atual.proximo`
  - `atual.proximo = novo`
- Se `pos` for inválida (maior que o tamanho), retorne False

Teste:

- inserir 15 na posição 1 em `10 -> 20 -> 30`
- deve virar `10 -> 15 -> 20 -> 30`

---

## Exercício 22 — Inverter a lista (desafio acessível)

Crie `inverter()` que inverte a LSE ajustando ponteiros.

Dica de raciocínio:

- use 3 ponteiros: `anterior`, `atual`, `proximo`
- vá “virando” a seta de cada nodo

Teste com:

- lista vazia
- lista com 1
- lista com 3

---

# Parte 7 — Convertendo (ajuda para testar)

## Exercício 23 — `from_list(lista_python)`

Crie uma função (ou método) que recebe `[10, 20, 30]` e monta a LSE equivalente.

Requisito:

- manter a ordem

---

## Exercício 24 — `to_list()`

Crie um método `to_list()` que transforma a LSE em lista do Python, por exemplo:
`[10, 20, 30]`

Use para testar seus outros métodos.

---

# Parte 8 — Mini-projeto (opcional)

## Exercício 25 — Playlist encadeada

Crie uma `ListaEncadeada` de músicas (strings).

Implemente:

- `adicionar_musica(nome)` (no final)
- `pular()` (remove do início e retorna a música atual removida)
- `musica_atual()` (peek do início sem remover)

Simule:

1. adiciona 3 músicas
2. imprime a música atual
3. pula 1 vez
4. imprime a música atual
5. imprime a lista completa

---
