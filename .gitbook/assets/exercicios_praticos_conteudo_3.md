# Exercícios Práticos — Python: Estruturas de Dados e Modularização

Material baseado no conteúdo do PDF **“Python: estruturas de dados e modularização”**.

**Nível:** 2º semestre (fundamentos)  
**Conteúdos:** `list`, `tuple`, `set`, `dict`, percorrer estruturas, estruturas aninhadas e modularização (módulos e imports).

---

## Regras do treino (importante)

- Use apenas: variáveis, `print`, operadores, `if/elif/else`, `for/while`, `break/continue`,
  estruturas nativas (`list`, `tuple`, `set`, `dict`) e funções (`def`, `return`).
- Para modularização: pode criar **mais de um arquivo** `.py` (módulos) e importar.
- Não use bibliotecas externas.
- Capriche em nomes claros e organização (boa prática).

---

## Parte 1 — Listas (`list`)

### Exercício 1 — Lista inicial e operações básicas

Crie a lista: `numeros = [1, 2, 3, 4]`

1. Adicione `5` usando `append`.
2. Remova o `2` usando `remove`.
3. Imprima a lista final.

---

### Exercício 2 — Acesso por índice

Com a lista `numeros = [10, 20, 30, 40]`:

1. Imprima o primeiro elemento (índice 0).
2. Imprima o último elemento usando índice (dica: tamanho - 1).
3. Imprima a soma do primeiro com o último.

---

### Exercício 3 — Elementos repetidos

Crie `valores = [1, 2, 2, 3, 3, 3]`.

1. Imprima a lista.
2. Explique em um comentário (no seu `.py`) se lista permite repetição e por quê.

---

### Exercício 4 — Lista com tipos diferentes

Crie uma lista com: um `int`, um `float`, uma `str` e um `bool`.  
Imprima a lista e depois imprima cada item em uma linha usando `for`.

---

### Exercício 5 — Contando ocorrências “na mão”

Dada a lista `dados = [1, 3, 3, 3, 5, 3, 2]`:

1. Conte quantas vezes o número `3` aparece usando `for` e um contador.
2. Imprima o total.

---

### Exercício 6 — Maior e menor (sem usar `max`/`min`)

Dada a lista `nums = [8, 2, 10, 4, 7]`:

1. Encontre o maior valor usando `for`.
2. Encontre o menor valor usando `for`.
3. Imprima ambos.

---

### Exercício 7 — Filtrando pares

Dada a lista `nums = [1, 2, 3, 4, 5, 6, 7, 8]`:

1. Crie `pares = []`.
2. Percorra `nums` e adicione em `pares` apenas os valores pares.
3. Imprima `pares`.

---

### Exercício 8 — “Pilha” simples usando lista (opcional)

Use uma lista como pilha:

1. Comece com `pilha = []`.
2. Adicione 3 itens com `append`.
3. Remova 1 item do final (dica: pode usar `pop()` **ou** controlar removendo pelo índice final).
4. Imprima a pilha final.

> Objetivo: entender como listas servem de base para estruturas como pilhas/filas.

---

## Parte 2 — Tuplas (`tuple`)

### Exercício 9 — Coordenadas imutáveis

Crie `coordenadas = (10, 20)`.

1. Imprima `coordenadas`.
2. Imprima `coordenadas[0]` e `coordenadas[1]`.
3. Tente alterar um valor e veja o erro. Explique em comentário por que acontece.

---

### Exercício 10 — Função retornando múltiplos valores

Crie uma função `divisao_com_resto(a, b)` que retorna **dois valores**: quociente inteiro e resto.

- No final, chame a função com `a=17` e `b=5` e imprima os dois retornos.

> Dica: retorne como tupla (ex.: `return x, y`).

---

### Exercício 11 — Configuração fixa

Crie uma tupla `config = ("localhost", 5432, True)`.

1. Imprima cada item com `for`.
2. Escreva em comentário: “Por que tupla é boa para esse caso?”

---

## Parte 3 — Conjuntos (`set`)

### Exercício 12 — Removendo duplicatas

Dada a lista `itens = [1, 2, 2, 3, 3, 3, 4]`:

1. Converta para conjunto.
2. Imprima o conjunto.
3. Explique em comentário o que aconteceu com os repetidos.

---

### Exercício 13 — Verificação de existência (membership)

Crie `visitados = {"home", "perfil", "config"}`.

1. Verifique se `"perfil"` está no conjunto e imprima um texto dizendo o resultado.
2. Verifique se `"login"` está no conjunto e imprima o resultado.

---

### Exercício 14 — União e interseção (conceito)

Crie:

- `a = {1, 2, 3}`
- `b = {3, 4, 5}`

1. Crie `uniao` (elementos de `a` e `b`).
2. Crie `intersecao` (elementos comuns).
3. Imprima os dois.

> Se você não lembrar o operador/método, faça “na mão” com `for` e `if`.

---

## Parte 4 — Dicionários (`dict`)

### Exercício 15 — Dicionário de “aluno”

Crie um dicionário `aluno` com:

- `"nome"` (string)
- `"idade"` (int)
- `"curso"` (string)

1. Imprima o dicionário inteiro.
2. Imprima apenas o nome acessando por chave.

---

### Exercício 16 — Atualizando valor por chave

Dado:

- `produto = {"nome": "Mouse", "preco": 80}`

1. Atualize o preço para `90`.
2. Imprima o dicionário final.

---

### Exercício 17 — Percorrendo com `.items()`

Com o dicionário:

- `pessoa = {"nome": "Ana", "idade": 20, "cidade": "POA"}`

Percorra usando `.items()` e imprima no formato:

- `chave: valor`

---

### Exercício 18 — Contagem de letras (bem básico)

Dada a string `texto = "banana"`:

1. Crie um dicionário `contagem = {}`.
2. Conte quantas vezes cada letra aparece.
3. Imprima o dicionário.

> Dica: se a letra ainda não existir no dicionário, comece com 1; senão, some 1.

---

### Exercício 19 — “Objeto simples” (ponte para POO)

Crie um dicionário `carro` com:

- `"marca"`, `"modelo"`, `"ano"`

1. Imprima uma frase usando os valores (ex.: “Marca X, Modelo Y, Ano Z”).
2. Em comentário: por que dicionário é útil para representar “objetos simples”?

---

## Parte 5 — Percorrendo estruturas (listas, sets e dicts)

### Exercício 20 — Soma em lista

Dada `nums = [2, 4, 6, 8]`:

1. Some tudo com `for` (sem `sum`).
2. Imprima o total.

---

### Exercício 21 — Filtrando palavras por tamanho

Dada `palavras = ["py", "python", "lista", "if", "modulo"]`:

1. Crie `longas = []`.
2. Adicione em `longas` apenas palavras com 5 ou mais letras.
3. Imprima `longas`.

---

### Exercício 22 — Percorrendo set

Crie `tags = {"backend", "python", "api"}` e imprima cada tag em uma linha.

> Em comentário: conjuntos têm ordem fixa?

---

### Exercício 23 — Percorrendo dict (somente chaves)

Dado `dados = {"a": 1, "b": 2, "c": 3}`:

1. Percorra o dicionário e imprima apenas as chaves.
2. Depois, imprima apenas os valores (acessando `dados[chave]`).

---

## Parte 6 — Estruturas aninhadas (listas com dicionários)

### Exercício 24 — Turma com notas

Crie a estrutura:

```python
turma = [
    {"nome": "Ana", "nota": 8},
    {"nome": "João", "nota": 6},
    {"nome": "Bia", "nota": 9},
]
```

1. Imprima o nome de cada aluno com sua nota.
2. Calcule a média da turma e imprima.

> Essa ideia aparece como exemplo de estruturas aninhadas.

---

### Exercício 25 — Aprovados

Usando a `turma` do exercício 24:

1. Crie `aprovados = []`.
2. Adicione em `aprovados` apenas alunos com nota >= 7 (guarde só o nome).
3. Imprima `aprovados`.

---

### Exercício 26 — Melhor aluno

Usando a `turma`:

1. Descubra quem tem a maior nota.
2. Imprima: `Melhor aluno: <nome> (<nota>)`.

---

### Exercício 27 — Buscar aluno por nome

Crie uma função `buscar_aluno(turma, nome)` que:

- retorna o dicionário do aluno se encontrar
- retorna `None` se não encontrar

Teste com um nome que existe e um que não existe.

---

### Exercício 28 — Atualizar nota

Crie uma função `atualizar_nota(turma, nome, nova_nota)` que:

1. Procura o aluno pelo nome
2. Se achar, atualiza a nota e retorna `True`
3. Se não achar, retorna `False`

---

## Parte 7 — Modularização (módulos e imports)

> Modularização: dividir o programa em arquivos menores (módulos) com responsabilidades claras.

### Exercício 29 — Criando um módulo de operações

Crie um arquivo **`operacoes.py`** com as funções:

- `soma(a, b)`
- `subtracao(a, b)`

Depois, em um arquivo **`main.py`**:

1. Importe o módulo com `import operacoes`
2. Imprima `operacoes.soma(3, 2)` e `operacoes.subtracao(10, 4)`

> O PDF mostra esse modelo de exemplo.

---

### Exercício 30 — Importando função específica

No `main.py`:

1. Faça `from operacoes import soma`
2. Imprima `soma(5, 4)`
3. Em comentário: qual a diferença (visual) entre importar o módulo inteiro e importar só uma função?

---

### Exercício 31 — Módulo `utils.py`

Crie um arquivo **`utils.py`** com:

- `eh_par(n)` (retorna True/False)
- `media_lista(lista)` (calcula média com `for`)

No `main.py`, use essas funções com uma lista de números e imprima os resultados.

---

### Exercício 32 — Organização sugerida (simulação)

Sem precisar criar classes ainda, simule uma organização básica:

- `main.py` → fluxo principal
- `utils.py` → funções auxiliares
- `dados.py` → onde você deixa listas/dicionários de exemplo (ex.: `turma`)

No `main.py`, importe `turma` do `dados.py` e use funções do `utils.py` para calcular a média.

> Essa ideia de separar responsabilidades aparece como boa prática.

---

## Mini-projeto (opcional) — “Boletim modularizado”

Crie três arquivos:

### 1) `dados.py`

- Deve ter a estrutura `turma` (lista de dicionários com `nome` e `nota`).

### 2) `boletim.py`

Crie funções:

- `media_turma(turma)`
- `aprovados(turma)` → retorna lista de nomes com nota >= 7
- `melhor_aluno(turma)` → retorna `(nome, nota)` como tupla

### 3) `main.py`

- Importa `turma` de `dados.py`
- Importa funções de `boletim.py`
- Imprime:
  - média da turma
  - aprovados
  - melhor aluno

**Regras:** nada de bibliotecas externas; use `for`, `if`, listas e dicionários.

---
