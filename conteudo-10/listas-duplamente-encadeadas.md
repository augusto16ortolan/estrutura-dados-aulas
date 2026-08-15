---
description: >-
  Estudo das listas duplamente encadeadas, comparando seu desempenho e consumo
  de memória em relação às listas simplesmente encadeadas.
---

# Listas duplamente encadeadas

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

Uma **lista duplamente encadeada** é uma estrutura de dados linear formada por **nodos ligados em sequência**, onde cada nodo guarda:

* um **valor**
* uma **referência para o próximo nodo**
* uma **referência para o nodo anterior**

Ela é uma evolução da lista simplesmente encadeada, permitindo que a navegação pela lista aconteça **nos dois sentidos**: do início para o fim e do fim para o início.

<figure><img src="../.gitbook/assets/image.png" alt="" width="563"><figcaption></figcaption></figure>

### Estrutura básica de uma lista duplamente encadeada

Cada nodo de uma lista duplamente encadeada possui três partes:

* **valor**: o dado armazenado
* **próximo**: referência para o próximo nodo
* **anterior**: referência para o nodo anterior

Visualmente, a ideia é:

```
None ← [10] ⇄ [20] ⇄ [30] → None
```

Diferente da lista simplesmente encadeada, aqui cada nodo “sabe”:

* quem vem depois
* quem veio antes

### Funcionamento geral da lista

* A lista possui um **início (head)** e, em muitos casos, um **fim (tail)**
* É possível percorrer a lista **para frente e para trás**
* As operações ficam mais flexíveis, especialmente remoções e inserções no meio da lista

Essa característica torna a lista duplamente encadeada mais poderosa, porém mais custosa em termos de memória.

### Estado típico da estrutura

Em muitas implementações, a lista duplamente encadeada mantém:

* `head` para o início
* `tail` para o final

Com isso, operações nas extremidades ficam mais eficientes e o percurso pode
começar pelo lado mais conveniente.

### Operações básicas em listas duplamente encadeadas

As operações principais são semelhantes às da lista simplesmente encadeada, mas envolvem **mais ajustes de referências**.

* Inserção de elementos
* Remoção de elementos
* Percurso da lista (ida e volta)
* Busca de valores

### Inserção de elementos

#### Inserção no início

* O novo nodo passa a ser o head
* Ele aponta para o antigo head
* O antigo head passa a apontar de volta para o novo nodo

Essa operação é eficiente e não depende do tamanho da lista.

#### Inserção no final

* O novo nodo passa a ser o último
* Ele aponta para o antigo último
* O antigo último passa a apontar para o novo nodo

Quando existe uma referência para o final da lista (tail), essa operação também é rápida.

### Remoção de elementos

#### Remoção no início

* O segundo nodo passa a ser o novo head
* O ponteiro `anterior` do novo head passa a ser `None`

#### Remoção no meio ou no final

* O nodo anterior passa a apontar para o próximo
* O nodo seguinte passa a apontar para o anterior

Por possuir referência dupla, **não é necessário percorrer a lista para encontrar o nodo anterior**, o que facilita essas operações.

### Complexidade típica

Quando já temos a referência do nodo certo:

* inserção ou remoção no início → `O(1)`
* inserção ou remoção no final (com `tail`) → `O(1)`
* ajuste no meio → `O(1)` para religar os vizinhos

Mas ainda existe um detalhe importante:

* **encontrar** o nodo no meio da lista continua podendo exigir percurso

Ou seja, muitas vezes o custo total depende de duas etapas:

* localizar o ponto de interesse
* ajustar as referências

### Percorrendo a lista

Uma grande vantagem da lista duplamente encadeada é o percurso bidirecional:

* Percurso do início para o fim
* Percurso do fim para o início

Isso é útil em aplicações como:

* navegação entre páginas
* listas que precisam de “voltar” e “avançar”
* históricos de ações

### Comparação com listas simplesmente encadeadas

#### Vantagens

* Navegação nos dois sentidos
* Remoções mais simples no meio da lista
* Maior flexibilidade em algumas operações

#### Desvantagens

* Maior consumo de memória
* Código mais complexo
* Mais cuidado necessário ao ajustar ponteiros

### Impacto no desempenho e uso de memória

* **Desempenho**:\
  As operações continuam eficientes, especialmente quando há referências para o início e o fim da lista.
* **Memória**:\
  Cada nodo armazena uma referência extra (`anterior`), aumentando o consumo de memória em relação à lista simplesmente encadeada.

Ou seja:

* Mais flexibilidade
* Mais custo de memória

### Exemplo simples de implementação em Python

```python
class Nodo:
    def __init__(self, valor):
        self.valor = valor
        self.proximo = None
        self.anterior = None


class ListaDuplamenteEncadeada:
    def __init__(self):
        self.head = None
        self.tail = None

    def inserir_inicio(self, valor):
        novo = Nodo(valor)
        if self.head is None:
            self.head = novo
            self.tail = novo
        else:
            self.head.anterior = novo
            novo.proximo = self.head
            self.head = novo
```

### Quando faz sentido usar essa estrutura

Listas duplamente encadeadas costumam valer a pena quando:

* a navegação precisa acontecer nos dois sentidos
* inserções e remoções nas extremidades são frequentes
* o custo extra de memória é aceitável

Esses casos aparecem em vários sistemas reais, especialmente quando existe a
ideia de item anterior e próximo item.

### Onde listas duplamente encadeadas aparecem na prática

Uma dúvida comum é: se Python já possui `list`, por que estudar lista
duplamente encadeada?

A resposta é que essa estrutura ajuda a entender problemas em que o sistema
precisa **andar para frente e para trás**, mantendo ligações entre elementos
vizinhos.

Alguns cenários típicos são:

* **playlist de músicas**: o usuário pode avançar para a próxima música ou voltar
  para a anterior
* **histórico de navegação**: um navegador precisa representar ações de
  “voltar” e “avançar”
* **editores de texto ou imagem**: estados anteriores e posteriores podem ser
  percorridos em uma linha de tempo
* **carrosséis e galerias**: uma imagem pode apontar para a próxima e para a
  anterior
* **listas de tarefas reordenáveis**: itens podem ser movidos sem reconstruir
  toda a sequência
* **sistemas de atendimento**: registros podem ser consultados em ordem direta
  ou inversa

Um exemplo concreto:

```text
Música anterior ⇄ Música atual ⇄ Próxima música
```

Nesse tipo de situação, guardar apenas o próximo elemento não é suficiente se o
sistema também precisa voltar com facilidade.

### Como escolher essa estrutura em um projeto

Uma lista duplamente encadeada costuma ser uma boa escolha quando:

* o sistema faz muitas inserções e remoções nas extremidades
* a aplicação precisa navegar nos dois sentidos
* existe uma referência direta para o nodo que será removido ou alterado
* o custo extra de memória não é um problema

Ela pode não ser a melhor escolha quando:

* o sistema precisa acessar posições pelo índice o tempo todo
* a busca por elementos é a operação mais frequente
* o volume de dados é grande e a memória precisa ser economizada

Em resumo, a lista duplamente encadeada é útil quando a aplicação precisa
representar uma **sequência navegável**, e não apenas armazenar valores.

### A importância das referências duplas

Em listas duplamente encadeadas:

* cada ajuste precisa manter **duas referências corretas**
* um erro pode quebrar a lista em qualquer direção
* o cuidado com os ponteiros é ainda mais importante

> “Em listas duplamente encadeadas, cada nodo conecta o passado e o futuro da lista.”

### Conclusão

As listas duplamente encadeadas ampliam o conceito das listas encadeadas ao permitir a navegação bidirecional entre os elementos, oferecendo maior flexibilidade em operações de inserção e remoção. Em contrapartida, esse ganho funcional vem acompanhado de um maior consumo de memória e de uma implementação mais complexa. Compreender essas vantagens e desvantagens é essencial para que o aluno saiba escolher a estrutura mais adequada para cada problema, consolidando o entendimento sobre desempenho, uso de memória e organização dos dados.
