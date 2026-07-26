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

Os principais algoritmos apresentados aqui são:

* Bubble Sort
* Selection Sort
* Insertion Sort
* Merge Sort

Os três primeiros são especialmente úteis para construir intuição, porque
mostram estratégias simples de comparação e reorganização de elementos.
Já o **Merge Sort** amplia o repertório ao introduzir uma abordagem mais
eficiente baseada em **divisão e conquista**.

Em outras palavras:

* **Bubble Sort, Selection Sort e Insertion Sort** são ótimos para ensino e raciocínio inicial
* **Merge Sort** é importante para mostrar como surgem algoritmos mais sofisticados e eficientes

Mesmo que nem todos sejam trabalhados com o mesmo nível de profundidade em aula,
é valioso que o aluno conheça o panorama.

### Ideia geral dos algoritmos de ordenação

Apesar das diferenças, todos os algoritmos de ordenação:

* comparam elementos
* verificam se estão na ordem correta
* trocam elementos de posição quando necessário
* repetem o processo até que a lista esteja ordenada

O que muda entre eles é **a estratégia usada para fazer isso**.

Vale observar que nem todo algoritmo de ordenação trabalha apenas trocando
elementos vizinhos ou escolhendo posições locais. Alguns, como o Merge Sort,
primeiro **quebram o problema em partes menores** para só depois reconstruir a
lista ordenada.

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

### Merge Sort

#### Funcionamento

O **Merge Sort** segue a ideia de **dividir para conquistar**:

1. divide a lista em duas metades
2. ordena cada metade separadamente
3. intercala as duas metades ordenadas em uma única lista final

Em vez de ir resolvendo o problema apenas com trocas locais, ele quebra o
problema original em subproblemas menores, resolve esses subproblemas e depois
combina os resultados.

#### Exemplo conceitual

Imagine a lista:

```text
[8, 3, 5, 1, 7, 2]
```

O Merge Sort faz algo assim:

```text
[8, 3, 5, 1, 7, 2]
-> divide em [8, 3, 5] e [1, 7, 2]
-> divide novamente até sobrar listas com 1 elemento
-> intercala as partes em ordem
-> resultado final: [1, 2, 3, 5, 7, 8]
```

A ideia importante é:

* listas de 1 elemento já estão ordenadas
* o trabalho pesado passa a ser **intercalar corretamente** duas partes já ordenadas

#### Intercalação (merge)

A etapa de **merge** compara os primeiros elementos de duas listas ordenadas e
vai escolhendo o menor deles até formar uma nova sequência ordenada.

Exemplo:

```text
[3, 8] e [1, 5, 7]
```

Intercalando:

```text
[1, 3, 5, 7, 8]
```

Essa etapa é o coração do algoritmo.

#### Exemplo em Python

```python
def merge_sort(lista):
    if len(lista) <= 1:
        return lista

    meio = len(lista) // 2
    esquerda = merge_sort(lista[:meio])
    direita = merge_sort(lista[meio:])

    return merge(esquerda, direita)


def merge(esquerda, direita):
    resultado = []
    i = 0
    j = 0

    while i < len(esquerda) and j < len(direita):
        if esquerda[i] <= direita[j]:
            resultado.append(esquerda[i])
            i += 1
        else:
            resultado.append(direita[j])
            j += 1

    resultado.extend(esquerda[i:])
    resultado.extend(direita[j:])
    return resultado
```

Esse exemplo retorna uma **nova lista ordenada**, em vez de modificar a lista
original diretamente.

#### Intuição de desempenho

O grande diferencial do Merge Sort é que ele mantém um desempenho mais estável
em listas maiores.

De forma clássica:

* divide a lista em partes menores repetidamente
* realiza intercalações lineares em cada nível da divisão
* alcança complexidade `O(n log n)`

Isso faz dele um salto importante em relação aos algoritmos quadráticos
apresentados antes.

#### Vantagens e limitações

**Vantagens:**

* desempenho melhor em comparação com Bubble, Selection e Insertion em muitos cenários
* estratégia elegante e muito importante na formação algorítmica
* pode ser estável

**Limitações:**

* a implementação é um pouco mais abstrata para iniciantes
* costuma exigir memória extra para a intercalação
* pode ser menos intuitivo em uma primeira aula do que os algoritmos mais simples

### Comparação de desempenho

De forma introdutória, podemos resumir assim:

* **Bubble Sort**: simples, mas costuma fazer muitas comparações e trocas
* **Selection Sort**: reduz o número de trocas, mas ainda percorre bastante a lista
* **Insertion Sort**: costuma se sair melhor quando os dados já estão parcialmente ordenados
* **Merge Sort**: usa divisão e conquista e mantém desempenho melhor em listas maiores

Na análise assintótica clássica:

* Bubble Sort → `O(n²)` no pior caso
* Selection Sort → `O(n²)` no pior caso
* Insertion Sort → `O(n²)` no pior caso, mas pode se aproximar de `O(n)` em cenários favoráveis
* Merge Sort → `O(n log n)` no pior caso

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
* Merge Sort pode ser estável, dependendo da implementação da intercalação

### Comparação conceitual entre os algoritmos

* **Bubble Sort**\
  Compara elementos vizinhos repetidamente.
* **Selection Sort**\
  Seleciona o menor elemento da parte não ordenada.
* **Insertion Sort**\
  Insere cada elemento na posição correta dentro da parte já ordenada.
* **Merge Sort**\
  Divide a lista em partes menores, ordena essas partes e depois intercala os resultados.

Todos resolvem o mesmo problema, mas de formas diferentes.

### Sugestão pedagógica de leitura do tema

Em uma sequência de aula, é perfeitamente razoável:

* trabalhar **Bubble Sort, Selection Sort e Insertion Sort** como núcleo principal
* apresentar **Merge Sort** como expansão de repertório e ponte para algoritmos mais eficientes

Assim, o aluno entende tanto as estratégias mais concretas quanto a transição
para soluções mais sofisticadas.

### Relação com estruturas de dados

Os algoritmos de ordenação dependem diretamente da estrutura usada para armazenar os dados, como:

* listas baseadas em vetor
* listas encadeadas

Por isso, entender bem pilhas, filas e listas é essencial para compreender ordenação.

### Conclusão

Os algoritmos de ordenação são fundamentais para organizar dados e permitir
operações mais eficientes sobre eles. Ao estudar Bubble Sort, Selection Sort,
Insertion Sort e Merge Sort, o aluno desenvolve o raciocínio necessário para
comparar estratégias, perceber custos diferentes e entender como a ideia de
divisão e conquista amplia o repertório algorítmico. Esse conhecimento serve
como base para o estudo de algoritmos ainda mais eficientes e para a
compreensão de conceitos avançados da computação.
