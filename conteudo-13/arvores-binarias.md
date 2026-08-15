---
description: >-
  Introdução às árvores binárias, sua estrutura, terminologia básica e os
  principais percursos utilizados para visitar seus elementos.
---

# Árvores binárias

Uma **árvore binária** é uma estrutura de dados não linear formada por
**nodos conectados em níveis**. Diferente de listas, pilhas e filas, em que os
elementos costumam ser percorridos em sequência, aqui a organização acontece em
forma de hierarquia.

Cada nodo de uma árvore binária pode ter:

* um **valor**
* um **filho à esquerda**
* um **filho à direita**

O nome "binária" vem justamente dessa regra: cada nodo pode ter **no máximo
dois filhos**.

## Por que estudar árvores binárias

Árvores aparecem com muita frequência em computação porque representam bem
estruturas hierárquicas e ajudam a organizar dados de forma eficiente.

Exemplos clássicos:

* estrutura de pastas e arquivos
* árvore genealógica
* expressão matemática
* índice de busca
* menus e categorias em sistemas

Além disso, árvores servem de base para estruturas mais avançadas, como árvores
de busca, heaps, tries e índices de banco de dados.

## Onde árvores binárias aparecem na prática

Árvores binárias são úteis quando os dados possuem uma relação de **hierarquia**,
**decisão** ou **divisão em partes menores**.

Alguns cenários comuns:

* **árvores de decisão**: cada pergunta leva para um próximo caminho, como em um
  sistema de diagnóstico ou questionário
* **expressões matemáticas**: operadores e operandos podem ser representados em
  formato de árvore
* **organização de categorias**: uma categoria pode se dividir em subcategorias
* **buscas eficientes**: árvores binárias de busca organizam valores menores à
  esquerda e maiores à direita
* **jogos**: decisões de personagens, escolhas de caminhos e estados possíveis
  podem ser modelados como árvores
* **compactação e codificação**: algumas técnicas usam árvores para representar
  códigos e frequências
* **bancos de dados e sistemas de arquivos**: estruturas em árvore aparecem em
  índices e organização hierárquica

Um exemplo de árvore de decisão:

```text
              Está chovendo?
              /           \
            sim           não
           /                \
     levar guarda-chuva    sair normal
```

Nesse caso, cada nodo representa uma pergunta ou decisão, e cada caminho leva a
uma consequência.

### Exemplos de cenários por tipo de árvore

Nem toda árvore binária é usada da mesma maneira.
Alguns usos dependem de regras específicas:

* **árvore binária comum**: representa hierarquia ou relacionamento entre nodos,
  sem exigir ordenação
* **árvore binária de busca**: acelera buscas quando os valores seguem a regra
  “menores à esquerda, maiores à direita”
* **árvores de expressão**: ajudam a avaliar contas como `(2 + 3) * 4`
* **árvores balanceadas**: mantêm altura controlada para evitar perda de
  desempenho

Essa distinção é importante: uma árvore binária comum apenas limita cada nodo a
dois filhos. Ela só se torna uma árvore de busca quando adotamos uma regra de
ordenação.

## Terminologia básica

Antes de implementar, vale dominar o vocabulário da estrutura:

* **raiz (root)**: primeiro nodo da árvore
* **pai**: nodo que aponta para outro nodo
* **filho**: nodo apontado por um nodo pai
* **folha**: nodo sem filhos
* **subárvore**: qualquer parte da árvore que também forma uma árvore
* **nível**: distância em relação à raiz; neste material, a raiz está no nível 0
* **altura**: maior número de arestas entre um nodo e uma folha; por essa convenção, uma árvore com apenas a raiz tem altura 0

Exemplo visual:

```text
        A
       / \
      B   C
     / \   \
    D   E   F
```

Nesse caso:

* `A` é a raiz
* `B` e `C` são filhos de `A`
* `D`, `E` e `F` são folhas
* usando a convenção deste material, a altura da árvore é 2, pois o maior caminho da raiz até uma folha tem duas arestas

### Tipos de árvore binária que vale conhecer

Mesmo em uma introdução, já é útil ouvir alguns nomes recorrentes:

* **árvore binária cheia**: cada nodo tem 0 ou 2 filhos
* **árvore binária completa**: todos os níveis, exceto talvez o último, estão totalmente preenchidos; no último nível, os nodos aparecem da esquerda para a direita, sem lacunas no meio
* **árvore binária balanceada**: mantém a altura mais controlada
* **árvore binária de busca**: organiza os valores com uma regra de comparação

Neste conteúdo, o foco está na estrutura geral e nos percursos, mas esses termos
aparecem bastante em estudos posteriores.

## Comparando com estruturas lineares

Nas estruturas lineares, como listas encadeadas, cada elemento costuma apontar
para **um próximo elemento**. Em uma árvore binária, um nodo pode se ramificar,
o que muda a forma de percorrer, buscar e pensar o problema.

Em resumo:

* **listas** organizam dados em sequência
* **árvores** organizam dados em hierarquia
* **árvores binárias de busca** organizam os valores por comparação, mas uma árvore binária comum não precisa estar ordenada

Essa diferença é importante porque muitos problemas do mundo real são mais bem
representados por relações hierárquicas do que por relações estritamente
lineares.

## Estrutura básica em Python

Uma forma simples de modelar um nodo de árvore binária em Python é:

```python
class NodoArvore:
    def __init__(self, valor):
        self.valor = valor
        self.esquerda = None
        self.direita = None
```

Com isso, podemos montar manualmente uma árvore pequena:

```python
raiz = NodoArvore("A")
raiz.esquerda = NodoArvore("B")
raiz.direita = NodoArvore("C")
raiz.esquerda.esquerda = NodoArvore("D")
raiz.esquerda.direita = NodoArvore("E")
```

Esse modelo já é suficiente para estudar a estrutura, os relacionamentos entre
os nodos e os percursos.

## Percursos em árvores binárias

Como uma árvore não é linear, precisamos definir **estratégias de visita** aos
nodos. Essas estratégias são chamadas de **percursos**.

Os três percursos clássicos são:

### Pré-ordem

Visita primeiro a raiz, depois a subárvore da esquerda e por fim a subárvore da
direita.

```text
raiz -> esquerda -> direita
```

Usos comuns:

* copiar a estrutura da árvore
* serializar a árvore
* processar um nodo antes dos filhos

### Em ordem

Visita primeiro a esquerda, depois a raiz e depois a direita.

```text
esquerda -> raiz -> direita
```

Esse percurso é especialmente importante porque, em uma **árvore binária de
busca**, ele visita os elementos em ordem crescente.

### Pós-ordem

Visita primeiro a esquerda, depois a direita e por último a raiz.

```text
esquerda -> direita -> raiz
```

Usos comuns:

* remover nós com segurança
* avaliar expressões
* processar filhos antes do pai

### Percurso por nível

Além dos percursos recursivos clássicos, existe o **percurso por nível**
(`level-order`), em que visitamos os nodos de cima para baixo, da esquerda para
a direita.

Exemplo:

```text
10, 5, 15, 2, 7, 20
```

Esse tipo de percurso costuma ser implementado com **fila**, conectando este
tema aos conteúdos anteriores sobre estruturas lineares.

## Exemplo de percurso com código

Considere a árvore:

```text
      10
     /  \
    5    15
   / \     \
  2   7     20
```

Um percurso em ordem pode ser implementado assim:

```python
def em_ordem(nodo):
    if nodo is not None:
        em_ordem(nodo.esquerda)
        print(nodo.valor)
        em_ordem(nodo.direita)
```

Saída:

```text
2
5
7
10
15
20
```

Isso mostra como a estrutura da árvore influencia diretamente a ordem em que os
valores são acessados.

Nesse exemplo específico, a saída ficou crescente porque a árvore respeita a
regra de uma árvore binária de busca: valores menores ficam à esquerda e valores
maiores ficam à direita. Em uma árvore binária comum, o percurso em ordem ainda
funciona, mas não necessariamente produz valores ordenados.

## Eficiência e observações iniciais

Nesta etapa introdutória, o mais importante é compreender a estrutura e os
percursos. Ainda assim, já vale registrar algumas ideias:

* acessar a raiz é imediato
* percorrer toda a árvore exige visitar todos os nodos
* a eficiência de busca depende muito do formato da árvore

De forma introdutória:

* percursos completos costumam custar `O(n)`
* em árvores mais equilibradas, certas buscas podem ser bem mais rápidas
* em árvores muito degeneradas, o comportamento pode se aproximar ao de uma lista encadeada

Quando a árvore fica muito "torta", várias operações podem perder desempenho.
Quando ela está mais equilibrada, a navegação tende a ser mais eficiente.

Esses detalhes abrem caminho para estudos futuros, como árvores binárias de
busca e árvores balanceadas.

## Relação com os conteúdos anteriores

Árvores binárias aparecem naturalmente depois de listas encadeadas, ordenação e
busca, porque ampliam a forma como os dados podem ser organizados:

* saímos da ideia de sequência
* passamos para a ideia de hierarquia
* introduzimos percursos mais ricos
* preparamos terreno para buscas e organizações mais sofisticadas

Em outras palavras, estudar árvores binárias é dar o próximo passo na evolução
das estruturas de dados.

### Fechamento

Árvores binárias são importantes porque mostram que nem todo problema de
organização de dados cabe em uma sequência linear. Ao introduzir hierarquia,
subárvores e percursos, elas ampliam o repertório de estruturas de dados e
preparam o terreno para estruturas mais avançadas, algoritmos de busca mais
eficientes e modelagens mais próximas de muitos problemas reais.
