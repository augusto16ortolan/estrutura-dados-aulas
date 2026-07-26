---
description: >-
  Introdução ao conceito de nodo e sua importância na construção de estruturas
  lineares, preparando a base para listas encadeadas.
---

# Nodos e conceitos de listas lineares

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

Um **nodo** é uma estrutura básica que representa um **elemento de uma lista**, mas que, além de guardar um valor, também guarda uma **referência para outro elemento**.\
Diferente de uma lista comum (como uma lista do Python), onde os elementos estão organizados automaticamente, aqui cada nodo “sabe” quem vem depois dele.

De forma simples, um nodo é composto por:

* **Um valor (dado)**: a informação que queremos armazenar
* **Uma referência (ponteiro)**: que indica o próximo nodo da sequência

O nodo é a base para a construção de várias estruturas de dados, como **listas encadeadas**, **pilhas encadeadas**, **filas encadeadas**, entre outras.

<figure><img src="../.gitbook/assets/image (2).png" alt="" width="563"><figcaption></figcaption></figure>

### O que são listas lineares

Uma **lista linear** é uma estrutura de dados em que os elementos estão organizados em **uma sequência**, um após o outro, seguindo uma ordem bem definida.

Características principais de uma lista linear:

* Existe um **primeiro elemento**
* Existe um **último elemento**
* Cada elemento (exceto o último) possui um **sucessor**
* Cada elemento (exceto o primeiro) possui um **antecessor**

A ideia de linearidade é justamente essa: os elementos formam uma **linha**, sem ramificações.

### Por que nodos são importantes em listas lineares

Os nodos permitem que a lista:

* **Cresça dinamicamente**, sem precisar realocar tudo
* Não dependa de posições fixas de memória
* Seja construída “ligando” um elemento ao outro

Em vez de acessar um elemento pelo índice (como em uma lista comum), o acesso acontece seguindo os **encadeamentos entre os nodos**.

Isso muda completamente a forma de pensar a estrutura:

* Você não “pula” direto para uma posição
* Você percorre a lista, nodo por nodo

### Diferença entre valor e referência

Esse é um ponto conceitual muito importante:

* o **valor** é a informação útil do nodo
* a **referência** é a ligação que mantém a estrutura conectada

Se o valor muda, o conteúdo do nodo muda.
Se a referência muda, a organização da estrutura pode mudar.

Por isso, ao estudar nodos, não estamos lidando apenas com dados, mas também
com **relações entre dados**.

### Exemplos de listas lineares no mundo real

* **Fila de pessoas**: cada pessoa sabe quem está logo atrás dela.
* **Vagões de um trem**: cada vagão está ligado ao próximo.
* **Lista de músicas em execução**: cada música leva à próxima da sequência.
* **Passos de uma receita**: cada passo aponta para o próximo.

Em todos esses exemplos, existe uma **ordem linear** e uma relação direta entre um elemento e o seguinte.

<figure><img src="../.gitbook/assets/image (3).png" alt="" width="563"><figcaption></figcaption></figure>

### Estado e invariantes em listas lineares

Assim como em pilhas e filas, listas lineares também possuem **estado** e **invariantes**.

O **estado** de uma lista linear é:

* O conjunto de nodos existentes
* As ligações entre eles

Invariantes típicas:

* Existe um nodo inicial (ou a lista está vazia)
* Cada nodo aponta corretamente para o próximo
* O último nodo aponta para `None`
* A sequência de nodos não pode ser “quebrada”

Essas regras garantem que a lista continue válida e navegável.

### Relação entre nodos e listas encadeadas

As **listas encadeadas** surgem diretamente a partir do conceito de nodo.\
Uma lista encadeada nada mais é do que:

* Um nodo inicial (chamado de **head**)
* Vários nodos ligados em sequência
* Cada nodo apontando para o próximo

Sem entender nodos, o aluno não consegue entender:

* Inserções no meio da lista
* Remoções de elementos
* Percursos sequenciais
* Diferença entre listas encadeadas e listas baseadas em vetor

### Exemplo simples de nodo em Python

```python
class Nodo:
    def __init__(self, valor):
        self.valor = valor
        self.proximo = None
```

Criando nodos e ligando manualmente:

```python
n1 = Nodo(10)
n2 = Nodo(20)
n3 = Nodo(30)

n1.proximo = n2
n2.proximo = n3
```

Visualmente, isso representa:

```
10 -> 20 -> 30 -> None
```

Cada nodo guarda seu valor e sabe quem vem depois dele.

### Relação com memória e acesso

Em estruturas baseadas em vetor, normalmente imaginamos elementos em posições
contíguas e acessíveis por índice. Em estruturas baseadas em nodos, a lógica é
diferente:

* cada nodo pode estar em uma região distinta de memória
* o acesso acontece seguindo referências
* o custo de percorrer cresce com o número de nodos visitados

Essa diferença prepara o terreno para entender por que listas encadeadas têm
vantagens em algumas operações e limitações em outras.

### A importância da ordem em listas lineares

Em listas lineares, **a ordem dos nodos define completamente a estrutura**.\
Trocar um ponteiro muda toda a lista.

Por isso, operações como inserir ou remover exigem cuidado:

* Um erro de referência pode “quebrar” a lista
* Um nodo pode se tornar inacessível
* Parte da lista pode ser perdida

> “Em listas encadeadas, o que mantém a estrutura viva são as ligações entre os nodos.”

### Preparação para o próximo passo

Ao dominar nodos, o aluno já tem a base para compreender:

* listas simplesmente encadeadas
* listas duplamente encadeadas
* pilhas e filas implementadas com encadeamento
* árvores, em que um nodo pode apontar para mais de um próximo elemento

### Conclusão

Os nodos são a base conceitual das listas lineares e de várias outras estruturas de dados. Ao compreender que cada elemento carrega não apenas um valor, mas também uma referência para o próximo, o aluno passa a enxergar as estruturas de dados de forma mais abstrata e próxima do funcionamento real da memória. Esse entendimento é fundamental para avançar no estudo de listas encadeadas, pilhas e filas encadeadas, além de reforçar conceitos essenciais como sequência, ligação e organização dos dados.
