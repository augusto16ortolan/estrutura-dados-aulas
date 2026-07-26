---
description: >-
  Criação e utilização de classes, objetos, atributos e métodos em Python,
  aplicando conceitos básicos de POO para modelar problemas de forma mais clara.
---

# POO: classes, objetos e métodos em Python

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Nesta parte, a ideia é sair do “conceito” e **ver como a POO aparece no Python**: você cria **classes** (moldes), instancia **objetos** (coisas concretas) e define **métodos** (ações). O ponto principal é que, em POO, a gente tenta manter **dados + comportamentos juntos**, para o código ficar mais organizado e mais fácil de manter.

#### Um paralelo com a disciplina

Em POO é muito útil pensar que um objeto possui:

* um **estado interno** (atributos)
* um conjunto de **operações** (métodos)
* e, muitas vezes, **regras** que precisam continuar verdadeiras

Essa forma de pensar conversa diretamente com estruturas de dados, que também
possuem estado e invariantes.

### O que é uma classe em Python

Uma **classe** é um “molde” que descreve:

* quais **informações** um objeto vai guardar (**atributos**)
* quais **ações** ele sabe fazer (**métodos**)

No Python, uma classe é declarada com `class Nome:`.

### O que é um objeto (instância)

Um **objeto** é uma “versão concreta” da classe.

Exemplo:

* Classe: `Aluno`
* Objetos: `aluno1`, `aluno2`, `aluno3` (cada um com nome e matrícula próprios)

### Atributos: o estado interno do objeto

Atributos são as variáveis “do objeto”. Eles guardam o **estado interno**.

Exemplo:

* `Aluno` pode ter `nome`, `matricula`, `curso`
* `Carro` pode ter `modelo`, `cor`, `velocidade_atual`

### Métodos: o que o objeto sabe fazer

Métodos são funções **dentro** da classe. Eles representam as ações do objeto.

Exemplo:

* `ContaBancaria.depositar(valor)`
* `ContaBancaria.sacar(valor)`

### `self`: “este objeto aqui”

O `self` é como o Python diz:

> “Estou falando deste objeto específico.”

Quando você escreve `self.saldo`, você está acessando o saldo **daquele objeto**, não uma variável solta no programa.

### `__init__`: construindo o objeto

O método `__init__` roda quando você cria um objeto. Ele normalmente define os atributos iniciais.

#### Exemplo 1 — Classe simples: Aluno

```python
class Aluno:
    def __init__(self, nome, matricula):
        self.nome = nome
        self.matricula = matricula

    def apresentar(self):
        return f"Oi! Eu sou {self.nome} e minha matrícula é {self.matricula}."


aluno1 = Aluno("Ana", "2026001")
aluno2 = Aluno("João", "2026002")

print(aluno1.apresentar())
print(aluno2.apresentar())
```

O que observar:

* `aluno1` e `aluno2` são objetos diferentes
* ambos têm os mesmos “campos” (atributos), mas valores diferentes

### Um exemplo com “estado + regra”: Conta bancária

Aqui entra muito a ideia de **invariantes**: por exemplo, “saldo não pode ficar negativo” (se sua regra for essa).

#### Exemplo 2 — ContaBancaria

```python
class ContaBancaria:
    def __init__(self, titular, saldo=0):
        self.titular = titular
        self.saldo = saldo

    def depositar(self, valor):
        if valor <= 0:
            raise ValueError("O valor do deposito deve ser positivo.")
        self.saldo += valor

    def sacar(self, valor):
        if valor <= 0:
            raise ValueError("O valor do saque deve ser positivo.")
        if valor > self.saldo:
            raise ValueError("Saldo insuficiente.")
        self.saldo -= valor

    def consultar_saldo(self):
        return self.saldo


conta = ContaBancaria("Maria", 100)
conta.depositar(50)
conta.sacar(30)

print("Titular:", conta.titular)
print("Saldo:", conta.consultar_saldo())
```

Pontos didáticos:

* o **estado** é `balance`
* as **ações** que mexem no estado são `deposit` e `withdraw`
* existe uma “regra do mundo real” que o código protege (não sacar mais do que tem)

### Exemplo bem “do dia a dia”: Produto e desconto

Aqui entendemos que objeto guarda dados e “sabe operar” sobre eles.

#### Exemplo 3 — Produto

```python
class Produto:
    def __init__(self, nome, preco):
        self.nome = nome
        self.preco = preco

    def aplicar_desconto(self, percentual):
        if percentual < 0 or percentual > 100:
            raise ValueError("O percentual deve estar entre 0 e 100.")
        self.preco = self.preco * (1 - percentual / 100)

    def descrever(self):
        return f"{self.nome} custa R$ {self.preco:.2f}"


produto = Produto("Headphone", 200)
print(produto.descrever())

produto.aplicar_desconto(10)
print(produto.descrever())
```

### Exemplo com lista dentro do objeto: Carrinho de compras

Aqui vemos um objeto que “por dentro” tem uma lista e métodos para mexer nela.

#### Exemplo 4 — CarrinhoDeCompras

```python
class CarrinhoDeCompras:
    def __init__(self):
        self.itens = []

    def adicionar(self, preco):
        if preco <= 0:
            raise ValueError("O preco deve ser positivo.")
        self.itens.append(preco)

    def total(self):
        return sum(self.itens)

    def quantidade(self):
        return len(self.itens)


carrinho = CarrinhoDeCompras()
carrinho.adicionar(10)
carrinho.adicionar(25)
carrinho.adicionar(5)

print("Itens:", carrinho.quantidade())
print("Total:", carrinho.total())
```

### Ligando diretamente com Pilha e Fila

Você já trabalhou com classes `Pilha` e `Fila`. Elas são exemplos perfeitos de POO:

* estado interno: por exemplo, `self._itens`
* métodos: como `push()`, `pop()`, `enqueue()` ou `dequeue()`
* regras: por exemplo, não remover elemento de uma estrutura vazia

Isso ajuda a perceber que POO não é “algo separado”: é só uma forma de **organizar o código**.

### Um primeiro olhar para encapsulamento em Python

Em Python, é comum usar um sublinhado no nome do atributo para indicar que ele
é de uso interno:

```python
class Pilha:
    def __init__(self):
        self._itens = []
```

Esse sublinhado não impede tecnicamente o acesso, mas comunica a intenção de
que o ideal é interagir com o objeto pelos métodos.

### Quando faz sentido criar uma classe

Criar uma classe costuma fazer sentido quando:

* existe um estado que precisa ser preservado
* há várias operações relacionadas sobre esse estado
* o problema representa uma entidade clara
* queremos evitar dados e funções soltas

### Erros comuns de quem está começando

1. Esquecer o `self` dentro dos métodos
2. Confundir classe com objeto
   * `Aluno` (classe) vs `aluno1 = Aluno(...)` (objeto)
3. Criar atributos fora do `__init__` sem querer (bagunça o estado)
4. Não pensar nas regras do domínio (ex.: permitir saldo negativo sem querer)

### Conclusão

Em Python, POO é uma forma prática de modelar problemas criando **classes** (moldes) e **objetos** (instâncias) que guardam **estado (atributos)** e executam **ações (métodos)**. Essa organização deixa o código mais legível e mais fácil de evoluir, e conecta diretamente com o que vocês já viram em estruturas como Pilha e Fila: existe um estado interno e operações bem definidas que alteram esse estado de maneira controlada.
