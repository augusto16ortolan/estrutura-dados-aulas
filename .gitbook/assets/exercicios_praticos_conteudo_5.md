# Exercícios Práticos — POO em Python (Classes, Objetos e Métodos)

**Nível:** 2º semestre (fundamentos)  
**Conteúdo:** classes, objetos (instâncias), atributos, métodos, `self`, `__init__`, regras/invariantes, e objetos com listas internas (ex.: carrinho).  
**Objetivo:** praticar como a POO aparece no Python para organizar melhor o código.

---

## Como trabalhar

- Você pode fazer:
  - **1 arquivo por exercício** (`ex01.py`, `ex02.py`, ...), ou
  - **um arquivo só** por parte (ex.: `parte1.py`, `parte2.py`).
- Use `print(...)` para testar tudo.
- Não use bibliotecas externas.

---

## Regras do treino (para ficar no básico)

- Pode usar: variáveis, `print`, `if/elif/else`, `for/while`, listas, e funções.
- Em POO: `class`, métodos, `self`, `__init__`, atributos e validações simples.
- Evite “mágica”: **não use** `@dataclass` (por enquanto).

---

# Parte 1 — Classe e objeto (o básico)

## Exercício 1 — Primeira classe

Crie uma classe `Aluno` com atributos:

- `nome`
- `matricula`

Crie dois objetos (`aluno1`, `aluno2`) com valores diferentes e imprima:

- o nome e a matrícula de cada um.

> **Dica:** use `__init__`.

---

## Exercício 2 — Método simples

Na classe `Aluno`, crie um método `introduzir()` que **retorna** uma string:

- `Oi! Eu sou <nome> e minha matrícula é <matricula>.`

Teste imprimindo o retorno para `aluno1` e `aluno2`.

---

## Exercício 3 — Classe vs Objeto (fixação)

Responda com comentários no código:

1. O que é **classe**?
2. O que é **objeto/instância**?
3. `Aluno` é classe ou objeto? E `aluno1`?

---

## Exercício 4 — Atributos diferentes em objetos diferentes

Crie três alunos com a mesma classe, mas com valores diferentes.
Imprima os três usando `introduzir()`.

> Objetivo: perceber que o “molde” é o mesmo, mas os dados mudam por objeto.

---

# Parte 2 — `self` e `__init__`

## Exercício 5 — O que é `self` na prática

Crie uma classe `Contador` com atributo `valor` (começa em 0).
Crie método `incrementar()` que soma 1 no `valor`.

Crie **dois** contadores diferentes e:

- incremente o primeiro 3 vezes
- incremente o segundo 1 vez
- imprima os dois valores

> Objetivo: ver que `self.valor` é de **cada objeto**, não uma variável solta.

---

## Exercício 6 — `__init__` com valor padrão

Crie uma classe `Produto` com atributos:

- `nome`
- `preco` (padrão: 0)

Crie:

- um produto passando nome e preço
- um produto passando só nome
  Imprima os dois.

---

## Exercício 7 — Atributos “bagunçados” (erro comum)

Crie uma classe `Pessoa` com `__init__(self, nome)`.

1. Instancie `p = Pessoa("Ana")`
2. Depois faça `p.idade = 20` (fora do `__init__`)
3. Imprima `p.nome` e `p.idade`

Agora responda em comentário:

- Por que isso “funciona”, mas pode virar bagunça no sistema?

---

# Parte 3 — Métodos que mexem no estado + regras (invariantes)

## Exercício 8 — Conta bancária (versão simples)

Crie uma classe `ContaBancaria` com:

- `titular`
- `saldo` (padrão: 0)

Crie métodos:

- `depositar(valor)`
- `sacar(valor)`
- `get_saldo()` (retorna saldo)

Regras mínimas:

- depósito só aceita valor > 0
- saque só aceita valor > 0
- não pode sacar mais do que o saldo

> Se a regra falhar, você pode:  
> (a) imprimir uma mensagem e não alterar o saldo, **ou**  
> (b) lançar `ValueError`.

---

## Exercício 9 — Testes de cenário (Conta)

Com a `ContaBancaria`:

1. crie uma conta com saldo inicial 100
2. deposite 50
3. saque 30
4. tente sacar 1000 (tem que falhar)
5. imprima titular e saldo final

---

## Exercício 10 — Registro de operações (lista dentro do objeto)

Melhore a `ContaBancaria`:

- crie `self.operacoes = []` no `__init__`
- quando depositar, adicione `"DEP +<valor>"`
- quando sacar, adicione `"SAQ -<valor>"`

Crie um método `extrato()` que imprime todas as operações, uma por linha.

---

## Exercício 11 — Invariante (explicação curta)

Escreva em comentário:

- O que é uma **regra/invariante** do domínio?
- Dê 1 exemplo de invariante da `ContaBancaria`.

---

# Parte 4 — Produto e desconto (validação simples)

## Exercício 12 — Aplicar desconto

Crie classe `Produto` com:

- `nome`
- `preco`

Crie método `aplicar_desconto(percentual)`:

- percentual deve estar entre 0 e 100
- atualize o preço para o novo valor com desconto

Crie método `descricao()` que retorna:

- `<nome> custa R$ <preco formatado com 2 casas>`

Teste com:

- preço 200 e desconto 10%

---

## Exercício 13 — Descontos inválidos

Teste e garanta que falha (ou imprime mensagem) quando:

- percentual é negativo
- percentual é maior que 100

---

## Exercício 14 — Dois produtos, dois descontos

Crie 2 produtos diferentes e aplique descontos diferentes.
Imprima antes e depois.

---

# Parte 5 — Objeto com lista interna (Carrinho de compras)

## Exercício 15 — Carrinho básico

Crie classe `CarrinhoDeCompras` com:

- `itens` (lista iniciando vazia)

Crie método `adicionar(preco)`:

- preço deve ser > 0
- adicione na lista

Crie métodos:

- `total()` → retorna soma dos preços
- `quantidade()` → retorna quantos itens tem

Teste adicionando 3 preços e imprimindo quantidade e total.

---

## Exercício 16 — Remover item (primeira ocorrência)

Crie método `remover(preco)`:

- se existir, remove uma ocorrência daquele preço
- se não existir, não faz nada (ou imprime mensagem)

Teste removendo um valor que existe e um que não existe.

---

## Exercício 17 — Carrinho “com nomes”

Agora em vez de adicionar só preço, adicione um dicionário:

- `{"nome": "...", "preco": ...}`

Atualize:

- `adicionar(nome, preco)`
- `total()` soma os preços
- `listar_itens()` imprime:
  - `- <nome>: R$ <preco>`

---

## Exercício 18 — Maior item do carrinho

Crie método `mais_caro()` que retorna o item mais caro (nome e preço).
Se o carrinho estiver vazio, retorne `None`.

---

# Parte 6 — Treino de erros comuns (debug)

## Exercício 19 — Esqueci o `self` (corrigir)

O código abaixo está errado. Corrija e faça funcionar:

```python
class Lampada:
    def __init__(self):
        ligada = False

    def ligar():
        ligada = True
```

Requisito: após corrigir, crie uma lâmpada, ligue e imprima o estado.

---

## Exercício 20 — Confundi classe com objeto (corrigir)

Corrija este uso errado:

```python
class Calculadora:
    def somar(self, a, b):
        return a + b

print(Calculadora.somar(2, 3))
```

> Dica: falta instanciar.

---

## Exercício 21 — Atributo fora do `__init__` sem querer (identificar)

Analise:

```python
class Pessoa:
    def set_idade(self, idade):
        self.idade = idade
```

1. Isso está “errado” ou “aceitável”?
2. O que acontece se você esquecer de chamar `set_idade` e tentar usar `p.idade`?

Responda em comentário e teste criando um objeto.

---

# Parte 7 — Pequenos desafios (bem acessíveis)

## Exercício 22 — “Placar” (estado + método)

Crie classe `Placar` com:

- `time_a`
- `time_b`

Métodos:

- `ponto_a()` soma 1 em `time_a`
- `ponto_b()` soma 1 em `time_b`
- `resultado()` retorna `"A <time_a> x <time_b> B"`

Simule alguns pontos e imprima o resultado.

---

## Exercício 23 — “Termômetro”

Crie classe `Termometro` com atributo `celsius`.
Métodos:

- `aumentar(x)` soma `x`
- `diminuir(x)` subtrai `x`
- `fahrenheit()` retorna a conversão

Regras:

- `x` deve ser positivo

---

## Exercício 24 — “Agenda” simples

Crie classe `Agenda` com lista `contatos` (strings).
Métodos:

- `adicionar(nome)` (não permite vazio)
- `listar()` imprime todos
- `buscar(nome)` retorna `True/False` se existe

---

# Mini-projeto (opcional) — Sistema de Conta + Carrinho

## Exercício 25 — Sistema integrado

Crie:

- `ContaBancaria` (com regras)
- `CarrinhoDeCompras` (com itens e total)

Agora simule:

1. uma conta com saldo inicial
2. um carrinho com 3 itens
3. tente “pagar” o carrinho sacando da conta o valor do total
   - se tiver saldo: sucesso e saldo diminui
   - se não tiver: falha e saldo não muda

Imprima:

- total do carrinho
- se o pagamento foi aprovado
- saldo final

---
