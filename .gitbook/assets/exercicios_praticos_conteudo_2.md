# Exercícios Práticos — Python (Revisão: Sintaxe, Controle de Fluxo, Listas e Funções)

**Nível:** 2º semestre (fundamentos)  
**Foco:** sintaxe, tipos, operadores, condicionais, laços, listas e funções.

## Como trabalhar

- Para cada exercício, crie um arquivo `.py` (ex.: `ex01.py`, `ex02.py`, etc.) ou faça todos em um único arquivo (se o professor permitir).
- Execute no terminal:
  ```bash
  python ex01.py
  ```

## Regras (para treinar os fundamentos)

- Use apenas: variáveis, `print`, operadores, `if/elif/else`, `for/while`, `break/continue`, listas (`append`, `remove`) e funções (`def`, `return`).
- Não use bibliotecas externas.
- Indentação correta é obrigatória (4 espaços).

---

## Parte 1 — Sintaxe, variáveis, tipos e operadores

### Exercício 1 — Variáveis básicas

Crie as variáveis abaixo e imprima todas na tela (uma por linha):

- `nome` (string)
- `idade` (inteiro)
- `altura` (float)
- `ativo` (booleano)

> Use valores reais (ex.: seu nome, idade, etc.).

---

### Exercício 2 — Soma e média

Crie três variáveis inteiras `a`, `b`, `c`.

- Imprima a soma `a + b + c`
- Imprima a média `(a + b + c) / 3`

---

### Exercício 3 — Divisão inteira e resto

Você tem `balas = 23` para dividir entre `pessoas = 5`.

- Calcule quantas balas cada pessoa recebe (divisão inteira).
- Calcule quantas balas sobram (resto).
- Imprima os dois resultados com mensagens claras.

> Dica: use `//` e `%`.

---

### Exercício 4 — Comparações (operadores relacionais)

Defina `x = 10` e `y = 3`.  
Imprima o resultado (True/False) de:

- `x == y`
- `x != y`
- `x > y`
- `x <= y`

---

### Exercício 5 — Mini “calculadora” com variáveis

Defina `n1 = 7` e `n2 = 2` e imprima:

- soma
- subtração
- multiplicação
- divisão
- divisão inteira
- resto

**Requisito:** cada resultado deve aparecer com um texto explicando o que é.

---

### Exercício 6 — Strings com f-string

Crie `nome = "Ana"` e `curso = "Computação"` (pode trocar).  
Imprima a frase:

- `Olá, <nome>! Bem-vindo(a) ao curso de <curso>.`

**Requisito:** use f-string.

---

### Exercício 7 — Erro de indentação (debug)

O código abaixo está com indentação errada. Copie, corrija e execute:

```python
idade = 18
if idade >= 18:
print("Maior de idade")
```

Depois, teste com outro valor para `idade` e veja o que muda.

---

### Exercício 8 — Bool na prática

Defina:

- `tem_carteira = True`
- `idade = 17`

Crie uma variável booleana `pode_dirigir` que seja `True` apenas se:

- `tem_carteira` for True **e**
- `idade` for maior ou igual a 18

Imprima `pode_dirigir`.

---

## Parte 2 — Condicionais (if / elif / else)

### Exercício 9 — Aprovado, recuperação ou reprovado

Crie uma variável `nota` (0 a 10) e implemente:

- se `nota >= 7`: imprima `"Aprovado"`
- senão, se `nota >= 5`: imprima `"Recuperação"`
- senão: imprima `"Reprovado"`

**Teste:** rode com `nota = 7`, `nota = 5` e `nota = 4`.

---

### Exercício 10 — Maioridade

Crie uma variável `idade`.

- Se `idade >= 18`, imprima `"Maior de idade"`.
- Caso contrário, imprima `"Menor de idade"`.

---

### Exercício 11 — Par ou ímpar

Crie uma variável `n` (inteiro).

- Se `n % 2 == 0`: imprima `"Par"`
- Senão: imprima `"Ímpar"`

---

### Exercício 12 — O maior de dois números

Crie `a` e `b`.

- Imprima qual é o maior.
- Se forem iguais, imprima `"Iguais"`.

---

### Exercício 13 — Triagem simples (login)

Crie variáveis:

- `usuario_correto = "admin"`
- `senha_correta = "1234"`
- `usuario` e `senha` (valores que você vai testar)

Regras:

- Se `usuario` e `senha` estiverem corretos: `"Acesso liberado"`
- Se `usuario` estiver correto e `senha` errada: `"Senha incorreta"`
- Se `usuario` estiver errado: `"Usuário não encontrado"`

---

### Exercício 14 — Categoria por idade

Crie uma variável `idade` e classifique:

- `0 a 12`: `"Criança"`
- `13 a 17`: `"Adolescente"`
- `18 a 59`: `"Adulto"`
- `60+`: `"Idoso"`

> Dica: use `elif` em ordem.

---

### Exercício 15 — Desconto na compra

Crie `valor = 120` (pode variar).

- Se `valor >= 200`: desconto de 20%
- Elif `valor >= 100`: desconto de 10%
- Else: sem desconto

Imprima:

- valor original
- desconto aplicado (em reais)
- valor final

---

### Exercício 16 — “Semáforo”

Crie `cor = "verde"` (teste também com `"amarelo"` e `"vermelho"`).

- `"verde"` → `"Pode passar"`
- `"amarelo"` → `"Atenção"`
- `"vermelho"` → `"Pare"`
- qualquer outro texto → `"Cor inválida"`

---

## Parte 3 — Laços (while / for) + break / continue

### Exercício 17 — Contando com while

Use `while` para imprimir os números de 0 até 4 (inclusive), um por linha.

---

### Exercício 18 — Contagem regressiva

Use `while` para imprimir: 5, 4, 3, 2, 1, 0

> Dica: comece com `contador = 5` e vá diminuindo.

---

### Exercício 19 — Tabuada do 7

Use `for` com `range(...)` para imprimir a tabuada do 7 (de 1 até 10):

- `7 x 1 = 7`
- ...
- `7 x 10 = 70`

---

### Exercício 20 — Somatório

Use `for` para somar os números de 1 até 100 e imprimir o resultado final.

---

### Exercício 21 — Pares de 0 a 20

Use `for` para imprimir somente os números pares de 0 a 20 (inclusive).

> Dica: use `if` dentro do laço.

---

### Exercício 22 — break (parar no 5)

Use `for i in range(10)` e pare o laço quando `i == 5`.

**Requisito:** use `break`.

---

### Exercício 23 — continue (pular o 2)

Use `for i in range(5)` e não imprima o número 2.

**Requisito:** use `continue`.

---

### Exercício 24 — Percorrendo uma string

Crie `palavra = "python"`.  
Use `for` para imprimir cada letra em uma linha.

**Desafio opcional:** imprima também o índice (posição) de cada letra.

---

## Parte 4 — Listas (append, remove, percorrer)

### Exercício 25 — Lista de números

Crie a lista `numeros = [1, 2, 3, 4]`.

- Adicione o número 5 ao final.
- Remova o número 2.
- Imprima a lista final.

---

### Exercício 26 — Percorrendo a lista

Com a lista do exercício anterior, use `for` para imprimir um número por linha.

---

### Exercício 27 — Soma dos elementos (sem `sum`)

Crie uma lista `valores = [10, 20, 30, 40]`.  
Calcule a soma de todos os elementos usando `for` (sem usar `sum()`).

Imprima a soma no final.

---

### Exercício 28 — Contando positivos

Crie uma lista `dados = [3, -1, 0, 7, -5, 2]`.  
Conte quantos valores são **maiores que zero** e imprima o total.

---

### Exercício 29 — Saudação para cada nome

Crie `nomes = ["Ana", "João", "Carlos"]`.  
Percorra a lista e imprima:

- `Olá, <nome>!`

---

### Exercício 30 — Filtrando com uma nova lista

Crie `numeros = [1, 2, 3, 4, 5, 6]`.  
Crie uma nova lista `pares` e adicione nela apenas os números pares, usando `for` e `append`.

Imprima `pares`.

---

### Exercício 31 — Remoção controlada

Crie `itens = ["arroz", "feijão", "carne", "salada"]`.  
Remova `"carne"` da lista e imprima a lista final.

**Desafio opcional:** faça uma verificação antes de remover (para evitar erro).

---

### Exercício 32 — Mini “catálogo”

Crie uma lista vazia `filmes = []`.

Em seguida:

- `append` 3 títulos (strings).
- Imprima a lista.
- Percorra com `for` e imprima os títulos numerados (1, 2, 3).

> Dica: crie um contador separado e vá incrementando.

---

## Parte 5 — Funções (def, parâmetros, return, valores padrão, escopo)

### Exercício 33 — Saudação simples (função)

Crie uma função `saudacao(nome)` que imprime:

- `Olá, <nome>!`

Chame a função pelo menos 2 vezes com nomes diferentes.

---

### Exercício 34 — Soma com return

Crie uma função `soma(a, b)` que retorna `a + b`.

Faça:

- `resultado = soma(3, 5)`
- imprima `resultado`

---

### Exercício 35 — Dobro

Crie uma função `dobro(n)` que retorna o dobro de `n`.  
Teste com pelo menos 3 valores e imprima os resultados.

---

### Exercício 36 — Média de três números

Crie `media3(a, b, c)` que retorna a média dos três números.  
Imprima o resultado para valores à sua escolha.

---

### Exercício 37 — Função com valor padrão

Crie a função `apresentar(nome, curso="Computação")` que imprime:

- `<nome> - <curso>`

Teste chamando:

- `apresentar("João")`
- `apresentar("Maria", "Engenharia")`

---

### Exercício 38 — Par ou ímpar (função)

Crie `eh_par(n)` que retorna `True` se `n` for par e `False` caso contrário.

Teste imprimindo o resultado para alguns valores.

---

### Exercício 39 — Funções + laços

Crie uma função `imprimir_pares_ate(limite)` que imprime todos os pares de 0 até `limite` (inclusive).

**Requisito:** use `for` e a função `eh_par(n)` do exercício anterior.

---

### Exercício 40 — Escopo (entendendo o erro)

Analise e execute este código:

```python
def teste():
    x = 10
    print(x)

teste()
# print(x)  # por que isso dá erro?
```

Responda no seu arquivo (como comentário) com 2 frases:

1. O que é variável local?
2. Por que `x` não existe fora da função?

**Desafio opcional:** crie uma variável `x` fora da função também e observe a diferença.

---

## Desafio final (opcional) — Integração dos conteúdos

### Exercício 41 — “Boletim” simples

Crie uma lista `notas = [7, 5, 9, 4]`.

Regras:

1. Crie uma função `media(lista)` que calcula a média (usando `for`).
2. Crie uma função `situacao(media_final)` que retorna:
   - `"Aprovado"` se média >= 7
   - `"Recuperação"` se média >= 5
   - `"Reprovado"` caso contrário
3. Calcule a média das notas e imprima:
   - as notas
   - a média final
   - a situação

> Objetivo: juntar lista + laço + função + `if/elif/else`.
