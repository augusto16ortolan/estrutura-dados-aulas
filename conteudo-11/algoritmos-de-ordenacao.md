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

### Onde algoritmos de ordenação aparecem na prática

Em um primeiro contato, ordenação pode parecer apenas “colocar números em ordem”, mas ela aparece em muitos sistemas reais.

Exemplos comuns:

* **lojas virtuais**: ordenar produtos por preço, avaliação, nome, data de cadastro ou relevância
* **sistemas escolares**: listar alunos por nome, média, frequência ou matrícula
* **rankings**: organizar jogadores por pontuação, tempo, nível ou número de vitórias
* **relatórios administrativos**: ordenar vendas por data, valor, cliente ou região
* **aplicativos de entrega**: ordenar pedidos por horário, distância ou prioridade
* **bancos de dados**: retornar consultas já organizadas para facilitar leitura e análise
* **agenda e calendário**: organizar eventos por data e horário

Um exemplo simples:

```
Produtos desordenados:
Notebook R$ 3200, Mouse R$ 80, Teclado R$ 150

Ordenados por preço:
Mouse R$ 80, Teclado R$ 150, Notebook R$ 3200
```

Nesse caso, ordenar melhora a experiência do usuário, porque facilita comparar opções e tomar decisões.

### Cenários de escolha do algoritmo

Nem todo algoritmo de ordenação é escolhido pelo mesmo motivo. Em uma situação real, a escolha depende do tamanho dos dados, da frequência de uso e do estado inicial da lista.

Alguns cenários:

* **lista pequena em exercício ou demonstração**: Bubble Sort, Selection Sort e Insertion Sort são bons para aprender a lógica
* **lista quase ordenada**: Insertion Sort costuma se comportar bem, porque faz poucos deslocamentos
* **quando se quer reduzir trocas**: Selection Sort pode ser interessante, pois faz no máximo uma troca por posição
* **listas maiores**: Merge Sort é mais adequado que os algoritmos quadráticos, pois mantém `O(n log n)` no pior caso
* **dados com elementos repetidos e múltiplos critérios**: estabilidade pode ser importante para preservar a ordem relativa dos itens iguais

Por exemplo, se um sistema ordena boletins por turma e depois por nome, a estabilidade ajuda a manter uma ordenação anterior quando os valores do novo critério empatam.

### Algoritmos de ordenação estudados

Existem diversos algoritmos de ordenação, mas neste conteúdo o foco está nos algoritmos **mais simples**, que ajudam a desenvolver o raciocínio lógico.

Os principais algoritmos apresentados aqui são:

* Bubble Sort
* Selection Sort
* Insertion Sort
* Merge Sort

Os três primeiros são especialmente úteis para construir intuição, porque mostram estratégias simples de comparação e reorganização de elementos. Já o **Merge Sort** amplia o repertório ao introduzir uma abordagem mais eficiente baseada em **divisão e conquista**.

Em outras palavras:

* **Bubble Sort, Selection Sort e Insertion Sort** são bons para entender o raciocínio inicial
* **Merge Sort** é importante para mostrar como surgem algoritmos mais sofisticados e eficientes

Mesmo que nem todos sejam explorados com o mesmo nível de profundidade, é valioso conhecer esse panorama.

### Analogias da vida real

Para entender melhor a diferença entre os algoritmos, ajuda comparar cada um com uma situação do dia a dia.

<figure><img src="../.gitbook/assets/Imagem do Codex 18 de ago. de 2026, 17_44_00.png" alt="Quatro analogias visuais para algoritmos de ordenação: pessoas em uma fila, cartas sobre uma mesa, cartas na mão e pilhas de provas."><figcaption><p>Analogias visuais para Bubble Sort, Selection Sort, Insertion Sort e Merge Sort.</p></figcaption></figure>

* **Bubble Sort → pessoas trocando de lugar em uma fila.** Você compara duas pessoas vizinhas pela altura e, se estiverem na ordem errada, elas trocam de posição. O processo se repete até a fila ficar ordenada.
* **Selection Sort → escolher sempre a menor carta de uma mesa.** Você olha todas as cartas disponíveis, encontra a menor e coloca na primeira posição. Depois procura a menor entre as que sobraram.
* **Insertion Sort → organizar cartas na mão.** Você pega uma nova carta e encaixa no lugar correto entre as cartas que já estão organizadas. Essa é uma das analogias mais naturais para esse algoritmo.
* **Merge Sort → organizar provas dividindo a pilha.** Você divide uma pilha grande em pilhas menores, organiza cada uma separadamente e depois junta as pilhas já ordenadas.

Essas analogias não substituem o código, mas ajudam a visualizar a estratégia de cada algoritmo antes de analisar os laços, comparações e trocas.

### Ideia geral dos algoritmos de ordenação

Apesar das diferenças, todos os algoritmos de ordenação:

* comparam elementos
* verificam se estão na ordem correta
* trocam, deslocam ou combinam elementos quando necessário
* repetem o processo até que a lista esteja ordenada

O que muda entre eles é **a estratégia usada para fazer isso**.

Vale observar que nem todo algoritmo de ordenação trabalha apenas trocando elementos vizinhos ou escolhendo posições locais. Alguns, como o Merge Sort, primeiro **quebram o problema em partes menores** para só depois reconstruir a lista ordenada.

### Critérios para comparar algoritmos de ordenação

Ao estudar ordenação, não basta perguntar “funciona?”. Também vale comparar:

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

Imagine uma fila de pessoas que precisa ser organizada por altura.

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

Essa pequena otimização faz o algoritmo parar antes se a lista já estiver ordenada.

### Selection Sort

#### Funcionamento

O **Selection Sort** procura o **menor elemento da lista** e o coloca na primeira posição.\
Depois, repete o processo com o restante da lista, ignorando a parte já ordenada.

#### Exemplo teórico

Imagine cartas espalhadas sobre uma mesa.

* Você olha todas as cartas disponíveis e encontra a menor.
* Coloca essa carta na primeira posição.
* Depois olha apenas as cartas restantes e encontra a próxima menor.
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

Em vez de ir resolvendo o problema apenas com trocas locais, ele quebra o problema original em subproblemas menores, resolve esses subproblemas e depois combina os resultados.

#### Exemplo conceitual

Imagine a lista:

```
[8, 3, 5, 1, 7, 2]
```

O Merge Sort faz algo assim:

```
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

A etapa de **merge** compara os primeiros elementos de duas listas ordenadas e vai escolhendo o menor deles até formar uma nova sequência ordenada.

Exemplo:

```
[3, 8] e [1, 5, 7]
```

Intercalando:

```
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

Esse exemplo retorna uma **nova lista ordenada**, em vez de modificar a lista original diretamente.

#### Intuição de desempenho

O grande diferencial do Merge Sort é que ele mantém um desempenho mais estável em listas maiores.

De forma clássica:

* divide a lista em partes menores repetidamente
* realiza intercalações lineares em cada nível da divisão
* alcança complexidade `O(n log n)`

Isso faz dele um salto importante em relação aos algoritmos quadráticos apresentados antes.

#### Vantagens e limitações

**Vantagens:**

* desempenho melhor em comparação com Bubble, Selection e Insertion em muitos cenários
* estratégia elegante e muito importante na formação algorítmica
* na implementação apresentada, é estável

**Limitações:**

* a implementação é um pouco mais abstrata para iniciantes
* costuma exigir memória extra para a intercalação
* pode ser menos intuitivo em um primeiro contato do que os algoritmos mais simples

### Comparação de desempenho

De forma introdutória, podemos resumir assim:

* **Bubble Sort**: simples, mas costuma fazer muitas comparações e trocas
* **Selection Sort**: reduz o número de trocas, mas ainda percorre bastante a lista
* **Insertion Sort**: costuma se sair melhor quando os dados já estão parcialmente ordenados
* **Merge Sort**: usa divisão e conquista e mantém desempenho melhor em listas maiores

Na análise assintótica clássica:

* Bubble Sort → `O(n²)` no pior caso; com a otimização de parada antecipada, pode chegar a `O(n)` quando a lista já está ordenada
* Selection Sort → `O(n²)` no pior caso e também no melhor caso, pois continua procurando o menor elemento no restante da lista
* Insertion Sort → `O(n²)` no pior caso, mas chega a `O(n)` quando a lista já está ordenada
* Merge Sort → `O(n log n)` no pior caso

### Estabilidade de ordenação

Outro conceito útil é a **estabilidade**. Um algoritmo estável preserva a ordem relativa de elementos iguais.

Isso pode ser importante quando:

* os dados possuem mais de um critério de ordenação
* dois elementos têm a mesma chave principal

De forma geral:

* Bubble Sort é estável na implementação apresentada, porque só troca quando o elemento da esquerda é maior que o da direita
* Insertion Sort é estável na implementação apresentada, porque só desloca elementos maiores que o valor atual
* Selection Sort geralmente não é estável na forma mais simples
* Merge Sort é estável na implementação apresentada, porque em caso de empate escolhe primeiro o elemento da lista da esquerda

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

### Como estudar estes algoritmos

Uma boa forma de estudar ordenação é começar pelas estratégias mais concretas e depois avançar para uma abordagem mais eficiente.

Primeiro, observe com atenção o que acontece em:

* **Bubble Sort**, que compara vizinhos
* **Selection Sort**, que escolhe o menor elemento
* **Insertion Sort**, que insere cada valor na posição correta

Depois, compare essas ideias com o **Merge Sort**, que muda a estratégia: em vez de resolver tudo com trocas locais, ele divide a lista em partes menores e depois reconstrói o resultado ordenado.

Essa comparação ajuda a perceber a transição entre algoritmos simples de entender e algoritmos mais eficientes para listas maiores.

### Relação com estruturas de dados

Os algoritmos de ordenação dependem diretamente da estrutura usada para armazenar os dados, como:

* listas baseadas em vetor
* listas encadeadas

Por isso, entender como cada estrutura armazena e acessa seus elementos ajuda a compreender o custo real de ordenar dados. Em Python, os exemplos deste conteúdo usam listas, que permitem acesso direto por índice.

### Conclusão

Os algoritmos de ordenação são fundamentais para organizar dados e permitir operações mais eficientes sobre eles. Ao estudar Bubble Sort, Selection Sort, Insertion Sort e Merge Sort, é possível comparar estratégias, perceber custos diferentes e entender como a ideia de divisão e conquista amplia o repertório algorítmico. Esse conhecimento serve como base para o estudo de algoritmos ainda mais eficientes e para a compreensão de conceitos avançados da computação.
