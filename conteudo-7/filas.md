---
description: >-
  Apresentação da estrutura de dados fila, suas operações básicas, variações e
  aplicações, com foco em desempenho e organização de dados.
---

# Filas

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Uma **fila (queue)** é um **Tipo Abstrato de Dados (TAD)** que define o comportamento de inserção e remoção dos elementos, independentemente de como ela é implementada internamente.\
Ela mantém uma coleção de elementos com acesso restrito a **dois pontos**: o início (frente) e o final (fim).\
Os elementos entram sempre pelo **final da fila** e saem sempre pelo **início da fila**.\
A regra de remoção é **FIFO (First In, First Out)**.

Assim como na pilha, o conceito de **TAD** é importante porque uma fila pode ser implementada usando listas, vetores, listas encadeadas, entre outras formas, e ainda assim continuará sendo uma fila se respeitar suas regras de funcionamento.

<figure><img src="../.gitbook/assets/image (23).png" alt="" width="563"><figcaption></figcaption></figure>

### Exemplos de fila no mundo real

* **Fila de banco ou supermercado**: a primeira pessoa que entra na fila é a primeira a ser atendida. Quem chega depois precisa esperar.
* **Fila de espera em atendimento telefônico**: as chamadas são atendidas na ordem em que chegam.
* **Fila de impressão**: os documentos enviados primeiro para a impressora são impressos antes dos demais.
* **Fila de carros em um pedágio**: o primeiro carro que chega é o primeiro a passar pela cancela.
* **Fila de mensagens em aplicativos**: mensagens são processadas e entregues na ordem em que foram enviadas.
* **Fila de tarefas em um sistema**: tarefas aguardam processamento e são executadas conforme a ordem de chegada.

A ideia central é sempre a mesma: **quem entra primeiro, sai primeiro**.

<figure><img src="../.gitbook/assets/image (24).png" alt="" width="563"><figcaption></figcaption></figure>

### Estado e invariantes

Uma fila possui um **estado interno**, que corresponde aos elementos armazenados, e um conjunto de **invariantes**, ou seja, regras que sempre precisam ser verdadeiras para que a estrutura continue correta.

Invariantes típicas de uma fila:

* Existe um **início (frente)** e um **final (fim)** bem definidos, ou a fila está vazia.
* A remoção de elementos acontece **somente no início** da fila.
* A inserção de elementos acontece **somente no final** da fila.
* Depois de um `enqueue(x)`, o elemento `x` passa a ser o último da fila.
* Depois de um `dequeue()`, o elemento removido é sempre o que estava há mais tempo na fila.

### Operações e especificação

Em teoria, as operações de uma fila também podem ser descritas usando **pré-condições** e **pós-condições**.

**enqueue(x)**\
Pré: nenhuma\
Pós: `x` é inserido no final da fila; o tamanho aumenta em 1

**dequeue()**\
Pré: fila não vazia\
Pós: remove e retorna o elemento do início da fila; o tamanho diminui em 1

**front()**\
Pré: fila não vazia\
Pós: retorna o elemento do início sem removê-lo

**is\_empty()**\
Pré: nenhuma\
Pós: retorna verdadeiro se a fila não possui elementos

### Complexidade e observação importante

Em uma fila ideal, as operações principais devem ser eficientes:

* `enqueue()`
* `dequeue()`
* `front()`

No entanto, ao implementar fila com uma lista comum do Python e usar `pop(0)`,
a remoção do primeiro elemento pode custar mais, porque os demais elementos
precisam ser reorganizados.

Por isso, em aplicações mais reais, costuma ser melhor usar estruturas pensadas
para fila, como `collections.deque`.

### Exemplo de classe Fila em Python

```python
class Fila:
    def __init__(self):
        self._itens = []

    def enqueue(self, item):
        """Adiciona um item ao final da fila."""
        self._itens.append(item)

    def dequeue(self):
        """Remove e retorna o item do início da fila."""
        if self.is_empty():
            raise IndexError("Não dá para remover: a fila está vazia.")
        return self._itens.pop(0)

    def front(self):
        """Retorna o item do início sem remover."""
        if self.is_empty():
            raise IndexError("Não dá para acessar: a fila está vazia.")
        return self._itens[0]

    def is_empty(self):
        """Retorna True se a fila estiver vazia."""
        return len(self._itens) == 0

    def size(self):
        """Retorna a quantidade de itens na fila."""
        return len(self._itens)
```

### Implementação mais adequada em Python

Uma alternativa mais eficiente para filas no Python é:

```python
from collections import deque

fila = deque()
fila.append(10)
fila.append(20)
primeiro = fila.popleft()
```

Isso é útil para mostrar que:

* o conceito da estrutura é uma coisa
* a implementação concreta pode ser melhor ou pior

#### Exemplo de uso

```python
f = Fila()
f.enqueue(10)
f.enqueue(20)
f.enqueue(30)

print("Primeiro:", f.front())    # 10
print("Saiu:", f.dequeue())      # 10
print("Tamanho:", f.size())      # 2
print("Vazia?", f.is_empty())    # False
```

### A importância da ordem na fila

Em uma fila, **a ordem de chegada define completamente o comportamento da estrutura**.\
Cada novo elemento entra no final e precisa esperar sua vez.\
O elemento que está há mais tempo na fila sempre será o próximo a sair.

Pensando passo a passo:

```python
f = Fila()
f.enqueue(10)
f.enqueue(20)
f.enqueue(30)

print("Primeiro:", f.front())    # 10
print("Saiu:", f.dequeue())      # 10
print("Tamanho:", f.size())      # 2
print("Vazia?", f.is_empty())    # False
```

Repara que:

* O `enqueue(20)` não tira o `10` da frente.
* O `enqueue(30)` também não muda quem está no início.
* Só quando acontece o `dequeue()` é que o primeiro elemento sai.

Ou seja, **na fila não importa quem chegou por último, e sim quem chegou primeiro**.

> “Em fila, quem chega primeiro é sempre o primeiro a sair.”

### Variações importantes de fila

Além da fila simples, existem outras variações muito usadas:

* **fila circular**
* **fila com prioridade**
* **deque** (fila de duas pontas)

Elas preservam parte da ideia de fila, mas ajustam o comportamento para
problemas específicos.

### Onde filas aparecem na prática

Filas são muito comuns em computação:

* escalonamento de tarefas
* filas de impressão
* sistemas de mensagens
* processamento de eventos
* atendimento concorrente em servidores

### Conclusão

A fila é uma estrutura essencial para representar situações de espera e processamento ordenado, tanto no mundo real quanto na computação. Ao entender a regra FIFO, o papel do início e do final da fila e a importância da ordem de chegada, o aluno passa a compreender como sistemas organizam tarefas, atendimentos e fluxos de dados de forma justa e previsível. Esse conceito serve como base para o estudo de algoritmos de escalonamento, processamento de eventos e outras estruturas mais avançadas, reforçando a importância da abstração e do controle de acesso aos dados.
