---
description: >-
  Implementação e funcionamento de listas simplesmente encadeadas, analisando
  suas operações e impacto no desempenho.
---

# Listas simplesmente encadeadas

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Uma **lista simplesmente encadeada** é uma estrutura de dados linear formada por **nodos ligados em sequência**, onde cada nodo guarda:

* um **valor**
* uma **referência para o próximo nodo**

Diferente de uma lista comum (como a lista do Python), os elementos **não ficam em posições fixas**, e o acesso aos dados acontece **percorrendo a lista nodo por nodo**, a partir do primeiro elemento.

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="563"><figcaption></figcaption></figure>

### Estrutura básica de uma lista simplesmente encadeada

Uma lista simplesmente encadeada possui:

* um **nodo inicial**, chamado de **head** (ou início da lista)
* vários nodos ligados em sequência
* o último nodo apontando para `None`

Visualmente, a ideia é:

```
head → [10] → [20] → [30] → None
```

Cada nodo sabe apenas **quem vem depois dele**.\
Não existe referência para o nodo anterior.

### Funcionamento geral da lista

* A lista começa sempre pelo **head**
* Para acessar um elemento, é necessário **percorrer a lista**
* Não é possível acessar diretamente uma posição específica (como índice)

Isso faz com que o funcionamento da lista seja mais **sequencial**, e não aleatório.

### Operações básicas em listas simplesmente encadeadas

As operações mais comuns são:

* Inserção de elementos
* Remoção de elementos
* Percurso da lista
* Busca de um valor

Cada uma dessas operações tem um impacto diferente no desempenho.

### Inserção de elementos

#### Inserção no início da lista

É a forma mais simples e rápida.

* O novo nodo passa a ser o head
* Ele aponta para o antigo head

```python
novo.proximo = head
head = novo
```

Essa operação é eficiente porque **não depende do tamanho da lista**.

#### Inserção no final da lista

Para inserir no final:

* É preciso percorrer toda a lista
* Encontrar o último nodo
* Fazer ele apontar para o novo nodo

Isso torna a operação mais custosa conforme a lista cresce.

### Remoção de elementos

#### Remoção no início

* O head passa a ser o próximo nodo
* O nodo antigo é descartado

É uma operação simples e rápida.

#### Remoção no meio ou no final

* É necessário percorrer a lista
* Encontrar o nodo anterior ao que será removido
* Ajustar a referência para “pular” o nodo removido

Se um ponteiro for ajustado de forma incorreta, a lista pode ser quebrada.

### Percorrendo a lista

Como não há índices, o percurso é sempre sequencial:

```python
atual = head
while atual is not None:
    print(atual.valor)
    atual = atual.proximo
```

Esse percurso é a base para:

* busca
* impressão
* contagem de elementos

### Exemplo simples de implementação em Python

```python
class Nodo:
    def __init__(self, valor):
        self.valor = valor
        self.proximo = None


class ListaEncadeada:
    def __init__(self):
        self.head = None

    def inserir_inicio(self, valor):
        novo = Nodo(valor)
        novo.proximo = self.head
        self.head = novo

    def imprimir(self):
        atual = self.head
        while atual is not None:
            print(atual.valor, end=" -> ")
            atual = atual.proximo
        print("None")
```

Exemplo de uso:

```python
lista = ListaEncadeada()
lista.inserir_inicio(30)
lista.inserir_inicio(20)
lista.inserir_inicio(10)

lista.imprimir()
# 10 -> 20 -> 30 -> None
```

### Impacto no desempenho (análise simples)

* Inserir no início: **rápido**
* Remover no início: **rápido**
* Buscar um elemento: precisa percorrer a lista
* Acessar um elemento específico: **não é direto**

Ou seja, listas simplesmente encadeadas são boas quando:

* há muitas inserções e remoções
* o acesso sequencial é suficiente

E não são ideais quando:

* é necessário acessar elementos aleatórios com frequência

### Comparação intuitiva com listas comuns

* Lista comum (array): acesso rápido por índice
* Lista encadeada: acesso sequencial, mais flexível para inserções

Cada estrutura resolve um tipo diferente de problema.

### A importância das referências

Em listas simplesmente encadeadas:

* a estrutura depende totalmente das referências
* um erro em um ponteiro pode perder parte da lista
* entender bem o encadeamento é essencial

> “Em listas encadeadas, os dados só existem enquanto as ligações entre os nodos existirem.”

### Conclusão

As listas simplesmente encadeadas são uma evolução natural do conceito de nodo e listas lineares, permitindo maior flexibilidade na organização dos dados. Ao compreender como os nodos se ligam, como as inserções e remoções funcionam e como o acesso acontece de forma sequencial, o aluno passa a entender melhor o impacto das estruturas de dados no desempenho dos algoritmos. Esse conhecimento é fundamental para avançar para listas duplamente encadeadas, pilhas e filas encadeadas, além de fortalecer o raciocínio sobre memória e referências.
