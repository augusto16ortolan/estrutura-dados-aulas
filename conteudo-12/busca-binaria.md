---
description: >-
  Estudo do algoritmo de busca binária, seus pré-requisitos, funcionamento e
  análise de eficiência em comparação com buscas lineares.
---

# Busca binária

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

A **busca binária** é um algoritmo utilizado para localizar um elemento em uma
coleção **ordenada**. A ideia central é simples e poderosa: em vez de verificar
os elementos um por um, o algoritmo compara o valor desejado com o elemento do
meio e elimina metade do problema a cada passo.

Esse comportamento faz da busca binária uma das estratégias clássicas de ganho
de eficiência em algoritmos.

## Pré-requisito essencial: dados ordenados

A busca binária **só funciona corretamente quando os dados estão ordenados**.
Sem isso, não há como decidir com segurança se o valor procurado está à
esquerda ou à direita do meio.

Exemplo de lista ordenada:

```text
[2, 5, 8, 12, 16, 23, 38]
```

Se quisermos encontrar o valor `12`, podemos começar olhando o elemento do meio
da lista. Se quisermos encontrar `5`, ao comparar com o meio já sabemos em qual
metade continuar.

## Ideia geral do algoritmo

O processo funciona assim:

1. Encontrar o elemento central da faixa atual.
2. Comparar esse elemento com o valor procurado.
3. Se forem iguais, a busca termina.
4. Se o valor procurado for menor, continuar apenas na metade da esquerda.
5. Se o valor procurado for maior, continuar apenas na metade da direita.

Em cada etapa, metade dos elementos deixa de ser considerada.

## Exemplo passo a passo

Considere a lista:

```text
[3, 7, 11, 18, 21, 29, 35, 42, 50]
```

Vamos buscar o valor `21`.

### Passo 1

Elemento do meio: `21`

Como o valor do meio já é o procurado, a busca termina imediatamente.

Agora imagine a busca pelo valor `35`.

### Passo 1

Elemento do meio: `21`

Como `35 > 21`, descartamos toda a metade esquerda.

### Passo 2

Nova faixa:

```text
[29, 35, 42, 50]
```

Elemento do meio da nova faixa: `35`

Valor encontrado.

Esse exemplo mostra por que a busca binária reduz tão rápido o espaço de busca.

## Implementação iterativa em Python

Uma implementação simples e bastante didática é:

```python
def busca_binaria(lista, alvo):
    inicio = 0
    fim = len(lista) - 1

    while inicio <= fim:
        meio = (inicio + fim) // 2

        if lista[meio] == alvo:
            return meio
        elif alvo < lista[meio]:
            fim = meio - 1
        else:
            inicio = meio + 1

    return -1
```

Exemplo de uso:

```python
numeros = [2, 5, 8, 12, 16, 23, 38]
indice = busca_binaria(numeros, 16)
print(indice)
```

Saída:

```text
4
```

### Invariante da busca

Uma maneira madura de entender o algoritmo é observar sua invariante principal:

> Se o elemento procurado existir, então ele precisa estar dentro da faixa entre
> `inicio` e `fim`.

Cada iteração preserva essa ideia, apenas reduzindo a faixa possível.
Pensar assim ajuda muito a evitar erros de limite e laços infinitos.

## Versão recursiva

A busca binária também pode ser escrita de forma recursiva, reforçando a ideia
de dividir o problema em subproblemas menores:

```python
def busca_binaria_recursiva(lista, alvo, inicio, fim):
    if inicio > fim:
        return -1

    meio = (inicio + fim) // 2

    if lista[meio] == alvo:
        return meio
    if alvo < lista[meio]:
        return busca_binaria_recursiva(lista, alvo, inicio, meio - 1)
    return busca_binaria_recursiva(lista, alvo, meio + 1, fim)
```

Para buscar na lista inteira, a chamada inicial deve informar os limites:

```python
indice = busca_binaria_recursiva(numeros, 16, 0, len(numeros) - 1)
```

As versões iterativa e recursiva resolvem o mesmo problema. A escolha entre
elas depende do objetivo didático, clareza do código e restrições do contexto.

## Comparação com a busca linear

Na **busca linear**, os elementos são verificados um a um, desde o início até
que o valor seja encontrado ou a lista termine.

Já na **busca binária**, a cada comparação o espaço de busca é reduzido pela
metade.

### Complexidade

* **Busca linear**: `O(n)` no pior caso
* **Busca binária**: `O(log n)` no pior caso

Isso significa que, em coleções grandes e ordenadas, a busca binária tende a
ser muito mais eficiente.

Exemplo intuitivo:

* com 1.000 elementos, a busca linear pode precisar olhar muitos deles
* a busca binária reduz a faixa rapidamente, ficando em torno de 10 comparações no pior caso

### Importante: a estrutura também influencia

Busca binária combina muito bem com estruturas que permitem acesso rápido ao
elemento do meio, como vetores e listas indexadas.

Em estruturas encadeadas, mesmo que os dados estejam ordenados, chegar ao meio
pode exigir percurso sequencial. Isso reduz bastante a vantagem prática da
estratégia.

## Quando usar busca binária

A busca binária é indicada quando:

* os dados já estão ordenados
* haverá muitas buscas sobre a mesma coleção
* o custo de ordenar previamente compensa o ganho posterior nas consultas

Ela é muito usada em:

* listas classificadas
* catálogos
* tabelas indexadas
* algoritmos que precisam testar rapidamente se um valor existe

## Limitações e cuidados

Apesar de eficiente, a busca binária exige atenção:

* **não funciona corretamente em listas desordenadas**
* depende de limites bem controlados (`inicio`, `fim` e `meio`)
* pode não compensar se a coleção for muito pequena ou se os dados mudarem o
  tempo todo

Também vale lembrar que, quando existem valores repetidos, a busca binária
encontra **uma ocorrência**, mas não necessariamente a primeira ou a última.
Se o problema exigir isso, o algoritmo precisa ser adaptado.

Outro cuidado importante é entender que a busca binária não "organiza" os
dados; ela apenas se beneficia de uma ordenação já existente.

## Relação com ordenação

Existe uma conexão direta entre este conteúdo e o tema anterior:

* algoritmos de ordenação organizam os dados
* a busca binária aproveita essa organização para acelerar a busca

Por isso, em muitos sistemas reais, ordenar e buscar são etapas que aparecem
juntas.

## Fechamento

A busca binária é um ótimo exemplo de como uma ideia simples de
**dividir para conquistar** gera um ganho real de desempenho. Mais do que
decorar o algoritmo, o objetivo aqui é perceber o raciocínio por trás dele:

* o problema precisa estar bem estruturado
* a ordenação cria condições para otimização
* eliminar metade do trabalho a cada passo muda completamente a eficiência

Esse tipo de raciocínio é central no estudo de estruturas de dados e
algoritmos.
