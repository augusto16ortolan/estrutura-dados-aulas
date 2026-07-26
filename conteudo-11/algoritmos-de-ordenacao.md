---
description: >-
  Apresentação dos principais algoritmos de ordenação, análise de complexidade e
  comparação de eficiência entre diferentes abordagens.
---

# Algoritmos de ordenação

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

Algoritmos de ordenação são procedimentos utilizados para **organizar os elementos de uma lista seguindo um critério**, normalmente em **ordem crescente ou decrescente**.\
Ordenar dados é uma tarefa fundamental na computação, pois facilita a **busca**, a **análise**, a **visualização** e o **processamento eficiente** das informações.

A ordenação aparece em diversos contextos do dia a dia, como:

* listas de nomes em ordem alfabética
* resultados classificados por pontuação
* dados organizados por data, preço ou prioridade

### O que significa ordenar dados

Ordenar significa **reorganizar os elementos**, sem alterar os valores armazenados, apenas suas posições.

Exemplo:

```
Antes:  [8, 3, 5, 1]
Depois: [1, 3, 5, 8]
```

Os mesmos valores continuam existindo, mas agora seguem uma ordem lógica.

### Por que a ordenação é importante

A ordenação é importante porque:

* torna os dados mais fáceis de entender
* melhora a experiência do usuário
* permite o uso de algoritmos mais eficientes (como busca binária)
* é base para muitos sistemas reais, como bancos de dados e relatórios

Em muitos casos, **ordenar os dados é o primeiro passo antes de processá-los**.

### Algoritmos de ordenação estudados

Existem diversos algoritmos de ordenação, mas neste momento do curso o foco está nos algoritmos **mais simples**, que ajudam a desenvolver o raciocínio lógico.

Os principais algoritmos estudados aqui são:

* Bubble Sort
* Selection Sort
* Insertion Sort

Esses algoritmos não são os mais rápidos, mas são excelentes para **entender o funcionamento da ordenação**.

### Ideia geral dos algoritmos de ordenação

Apesar das diferenças, todos os algoritmos de ordenação:

* comparam elementos
* verificam se estão na ordem correta
* trocam elementos de posição quando necessário
* repetem o processo até que a lista esteja ordenada

O que muda entre eles é **a estratégia usada para fazer isso**.

### Critérios para comparar algoritmos de ordenação

Ao estudar ordenação, não basta perguntar “funciona?”.
Também vale comparar:

* quantas comparações o algoritmo realiza
* quantas trocas ou deslocamentos acontecem
* como ele se comporta com listas pequenas ou quase ordenadas
* se ele preserva ou não a ordem relativa de elementos iguais

Esses critérios ajudam a construir maturidade algorítmica.

### Bubble Sort

#### Funcionamento

O **Bubble Sort** compara **elementos vizinhos** da lista e troca suas posições quando estão fora de ordem.\
A cada passagem completa pela lista, o maior elemento “sobe” para o final, como uma bolha na água.

#### Exemplo teórico

Imagine uma fila de pessoas organizada por altura, mas fora de ordem.

* O algoritmo compara duas pessoas lado a lado.
* Se a pessoa da esquerda for mais alta que a da direita, elas trocam de lugar.
* Esse processo continua até o final da fila.
* Ao final da primeira rodada, a pessoa mais alta já estará no final.

Esse processo se repete até que não seja mais necessário trocar ninguém.

> “O Bubble Sort resolve o problema aos poucos, empurrando os maiores valores para o final.”

#### Exemplo em Python

```python
def bubble_sort(lista):
    n = len(lista)
    for i in range(n):
        houve_troca = False
        for j in range(0, n - i - 1):
            if lista[j] > lista[j + 1]:
                lista[j], lista[j + 1] = lista[j + 1], lista[j]
                houve_troca = True
        if not houve_troca:
            break
```

Essa pequena otimização faz o algoritmo parar antes se a lista já estiver
ordenada.

### Selection Sort

#### Funcionamento

O **Selection Sort** procura o **menor elemento da lista** e o coloca na primeira posição.\
Depois, repete o processo com o restante da lista, ignorando a parte já ordenada.

#### Exemplo teórico

Imagine uma prateleira com livros fora de ordem pelo tamanho.

* Você olha todos os livros e encontra o menor.
* Coloca esse livro na primeira posição.
* Depois olha apenas os livros restantes e encontra o próximo menor.
* Repete o processo até organizar tudo.

O algoritmo sempre escolhe **quem merece ocupar a próxima posição correta**.

> “O Selection Sort escolhe, a cada passo, o elemento certo para a posição certa.”

#### Exemplo em Python

```python
def selection_sort(lista):
    n = len(lista)
    for i in range(n):
        menor = i
        for j in range(i + 1, n):
            if lista[j] < lista[menor]:
                menor = j
        lista[i], lista[menor] = lista[menor], lista[i]
```

### Insertion Sort

#### Funcionamento

O **Insertion Sort** constrói a lista ordenada **aos poucos**, inserindo cada novo elemento na posição correta dentro da parte já ordenada.

#### Exemplo teórico (sem código)

Imagine organizar cartas na mão durante um jogo:

* Você começa com uma carta (que já está ordenada).
* Ao receber uma nova carta, encontra o lugar certo entre as que já tem.
* Insere a carta ali, empurrando as outras se necessário.
* Repete isso até todas as cartas estarem organizadas.

Esse algoritmo funciona muito bem quando a lista já está quase ordenada.

> “O Insertion Sort organiza os dados do mesmo jeito que a gente organiza cartas na mão.”

#### Exemplo em Python

```python
def insertion_sort(lista):
    for i in range(1, len(lista)):
        atual = lista[i]
        j = i - 1
        while j >= 0 and lista[j] > atual:
            lista[j + 1] = lista[j]
            j -= 1
        lista[j + 1] = atual
```

### Comparação de desempenho

De forma introdutória, podemos resumir assim:

* **Bubble Sort**: simples, mas costuma fazer muitas comparações e trocas
* **Selection Sort**: reduz o número de trocas, mas ainda percorre bastante a lista
* **Insertion Sort**: costuma se sair melhor quando os dados já estão parcialmente ordenados

Na análise assintótica clássica:

* Bubble Sort → `O(n²)` no pior caso
* Selection Sort → `O(n²)` no pior caso
* Insertion Sort → `O(n²)` no pior caso, mas pode se aproximar de `O(n)` em cenários favoráveis

### Estabilidade de ordenação

Outro conceito útil é a **estabilidade**.
Um algoritmo estável preserva a ordem relativa de elementos iguais.

Isso pode ser importante quando:

* os dados possuem mais de um critério de ordenação
* dois elementos têm a mesma chave principal

De forma geral:

* Bubble Sort pode ser estável
* Insertion Sort pode ser estável
* Selection Sort geralmente não é estável na forma mais simples

### Comparação conceitual entre os algoritmos

* **Bubble Sort**\
  Compara elementos vizinhos repetidamente.
* **Selection Sort**\
  Seleciona o menor elemento da parte não ordenada.
* **Insertion Sort**\
  Insere cada elemento na posição correta dentro da parte já ordenada.

Todos resolvem o mesmo problema, mas de formas diferentes.

### Relação com estruturas de dados

Os algoritmos de ordenação dependem diretamente da estrutura usada para armazenar os dados, como:

* listas baseadas em vetor
* listas encadeadas

Por isso, entender bem pilhas, filas e listas é essencial para compreender ordenação.

### Conclusão

Os algoritmos de ordenação são fundamentais para organizar dados e permitir operações mais eficientes sobre eles. Ao estudar Bubble Sort, Selection Sort e Insertion Sort, o aluno desenvolve o raciocínio lógico necessário para comparar estratégias, entender diferentes formas de resolver o mesmo problema e perceber como escolhas algorítmicas impactam o desempenho de um sistema. Esse conhecimento serve como base para o estudo de algoritmos mais eficientes e para a compreensão de conceitos avançados da computação.
