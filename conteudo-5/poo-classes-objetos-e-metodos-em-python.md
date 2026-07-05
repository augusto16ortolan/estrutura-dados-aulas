---
description: >-
  Criação e utilização de classes, objetos, atributos e métodos em Python,
  aplicando conceitos básicos de POO para modelar problemas de forma mais clara.
---

# POO: classes, objetos e métodos em Python

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Nesta parte, a ideia é sair do “conceito” e **ver como a POO aparece no Python**: você cria **classes** (moldes), instancia **objetos** (coisas concretas) e define **métodos** (ações). O ponto principal é que, em POO, a gente tenta manter **dados + comportamentos juntos**, para o código ficar mais organizado e mais fácil de manter.

#### Um paralelo com o que vocês já viram (Pilha e Fila)

Quando vocês estudaram Pilha e Fila, a estrutura tinha:

* um **estado interno** (os elementos guardados) e
* regras que precisam continuar verdadeiras (**invariantes**) Pilha-conteudo

Em POO é muito parecido: um **objeto** também tem um **estado interno** (atributos) e regras do domínio (ex.: saldo não pode ficar negativo). Essa forma de pensar ajuda muito a modelar problemas.

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
class Student:
    def __init__(self, name, registration):
        self.name = name
        self.registration = registration

    def introduce(self):
        return f"Oi! Eu sou {self.name} e minha matrícula é {self.registration}."


s1 = Student("Ana", "2026001")
s2 = Student("João", "2026002")

print(s1.introduce())
print(s2.introduce())
```

O que observar:

* `s1` e `s2` são objetos diferentes
* ambos têm os mesmos “campos” (atributos), mas valores diferentes

### Um exemplo com “estado + regra”: Conta bancária

Aqui entra muito a ideia de **invariantes**: por exemplo, “saldo não pode ficar negativo” (se sua regra for essa).

#### Exemplo 2 — ContaBancaria

```python
class BankAccount:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance

    def deposit(self, amount):
        if amount <= 0:
            raise ValueError("Deposit amount must be positive.")
        self.balance += amount

    def withdraw(self, amount):
        if amount <= 0:
            raise ValueError("Withdraw amount must be positive.")
        if amount > self.balance:
            raise ValueError("Insufficient funds.")
        self.balance -= amount

    def get_balance(self):
        return self.balance


acc = BankAccount("Maria", 100)
acc.deposit(50)
acc.withdraw(30)

print("Owner:", acc.owner)
print("Balance:", acc.get_balance())
```

Pontos didáticos:

* o **estado** é `balance`
* as **ações** que mexem no estado são `deposit` e `withdraw`
* existe uma “regra do mundo real” que o código protege (não sacar mais do que tem)

### Exemplo bem “do dia a dia”: Produto e desconto

Aqui entendemos que objeto guarda dados e “sabe operar” sobre eles.

#### Exemplo 3 — Produto

```python
class Product:
    def __init__(self, name, price):
        self.name = name
        self.price = price

    def apply_discount(self, percent):
        if percent < 0 or percent > 100:
            raise ValueError("Percent must be between 0 and 100.")
        self.price = self.price * (1 - percent / 100)

    def describe(self):
        return f"{self.name} costs R$ {self.price:.2f}"


p = Product("Headphone", 200)
print(p.describe())

p.apply_discount(10)
print(p.describe())
```

### Exemplo com lista dentro do objeto: Carrinho de compras

Aqui vemos um objeto que “por dentro” tem uma lista e métodos para mexer nela.

#### Exemplo 4 — ShoppingCart

```python
class ShoppingCart:
    def __init__(self):
        self.items = []  # state: list of prices

    def add(self, price):
        if price <= 0:
            raise ValueError("Price must be positive.")
        self.items.append(price)

    def total(self):
        return sum(self.items)

    def count(self):
        return len(self.items)


cart = ShoppingCart()
cart.add(10)
cart.add(25)
cart.add(5)

print("Items:", cart.count())
print("Total:", cart.total())
```

### Ligando diretamente com Pilha e Fila

Você já trabalhou com classes `Pilha` e `Fila`. Elas são exemplos perfeitos de POO:

* estado interno: `self._itens`
* métodos: `push/pop/peek` ou `enqueue/dequeue/front` Pilha-conteudo Fila-conteudo
* e dá até para discutir “regras” e “pré/pós-condições” como vocês fizeram nas operações de fila Fila-conteudo

Isso ajuda a perceber que POO não é “algo separado”: é só uma forma de **organizar o código**.

### Erros comuns de quem está começando

1. Esquecer o `self` dentro dos métodos
2. Confundir classe com objeto
   * `Student` (classe) vs `s1 = Student(...)` (objeto)
3. Criar atributos fora do `__init__` sem querer (bagunça o estado)
4. Não pensar nas regras do domínio (ex.: permitir saldo negativo sem querer)

### Conclusão

Em Python, POO é uma forma prática de modelar problemas criando **classes** (moldes) e **objetos** (instâncias) que guardam **estado (atributos)** e executam **ações (métodos)**. Essa organização deixa o código mais legível e mais fácil de evoluir, e conecta diretamente com o que vocês já viram em estruturas como Pilha e Fila: existe um estado interno e operações bem definidas que alteram esse estado de maneira controlada.
