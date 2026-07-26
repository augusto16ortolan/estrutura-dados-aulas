---
description: >-
  Estudo da estrutura de dados pilha, seu funcionamento, principais operações,
  aplicações práticas e análise de eficiência.
---

# Pilhas

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Uma **pilha** (stack) é um **Tipo Abstrato de Dados (TAD)** que define **comportamento**, não necessariamente como é implementada.

* Ela mantém uma coleção de elementos com acesso restrito a **um único ponto**: o **topo**.
* As operações acontecem **somente no topo**.
* A regra de remoção é **LIFO** (_Last In, First Out_).

> “TAD” é importante porque você pode implementar pilha com lista, vetor, nós/ponteiros, etc., e ainda assim ela continua sendo “pilha” se respeitar as operações e regras.

<figure><img src="../.gitbook/assets/image (19).png" alt="" width="563"><figcaption></figcaption></figure>

### Exemplos de pilha no mundo real

* **Pratos na pia**: você coloca um prato em cima do outro. Quando vai pegar, pega o de cima. O último que você colocou é o primeiro que sai.
* **Roupas dobradas em uma pilha**: você dobra e coloca por cima. Na hora de pegar, normalmente pega a que está por cima. A última roupa colocada é a primeira usada.
* **Caixas empilhadas**: você empilha caixas. Se quiser pegar a de baixo, antes precisa tirar as de cima. Então a caixa mais recente, que ficou no topo, é a mais fácil de sair primeiro.
* **Um monte de folhas em cima da mesa**: você vai colocando uma folha por cima da outra. Quando precisa pegar uma, quase sempre pega a de cima — que foi a última que você colocou ali.
* **“Desfazer” no computador** (Ctrl+Z): quando você erra, o computador desfaz primeiro o que você acabou de fazer. Ele volta passo a passo na ordem inversa do que aconteceu.
* **Botão “Voltar” do navegador**: você vai clicando e abrindo páginas. Quando aperta “voltar”, ele volta para a página anterior, depois para a anterior dela, e assim por diante — como se estivesse desfazendo o caminho ao contrário.

<figure><img src="../.gitbook/assets/image (22).png" alt="" width="563"><figcaption></figcaption></figure>

### Estado e invariantes

Uma pilha tem um **estado interno** (os elementos armazenados) e um conjunto de **invariantes** (regras que sempre devem ser verdade).

**Invariantes típicas:**

1. Existe um “topo” bem definido (ou a pilha está vazia).
2. Só o topo pode ser removido ou consultado diretamente.
3. Depois de um `push(x)`, o topo passa a ser `x`.
4. Depois de um `pop()`, o topo vira o elemento que estava logo abaixo.

### Operações e especificação

Em teoria, a gente descreve operações com:

* **Pré-condição**: o que precisa ser verdade antes de executar
* **Pós-condição**: o que será verdade depois de executar

**push(x)**

* Pré: nenhuma
* Pós: `x` vira o novo topo; tamanho aumenta em 1

**pop()**

* Pré: pilha **não** vazia
* Pós: remove e retorna o topo; tamanho diminui em 1

**peek()**

* Pré: pilha **não** vazia
* Pós: retorna o topo sem alterar a pilha

**is\_empty()**

* Pré: nenhuma
* Pós: retorna verdadeiro se não há elementos

### Complexidade das operações

Quando a pilha é implementada de forma adequada, as operações principais
costumam ter custo constante:

* `push()` → `O(1)`
* `pop()` → `O(1)`
* `peek()` → `O(1)`

Isso acontece porque todas agem sobre o topo, sem precisar percorrer a
estrutura inteira.

### Possíveis implementações

Uma pilha pode ser implementada de diferentes formas:

* com lista do Python
* com lista encadeada
* com vetor em outras linguagens

Independentemente da implementação, a estrutura continua sendo pilha se
mantiver a regra LIFO e o acesso controlado pelo topo.

### Exemplo de classe Pilha em Python

```python
class Pilha:
    def __init__(self):
        self._itens = []

    def push(self, item):
        """Coloca um item no topo da pilha."""
        self._itens.append(item)

    def pop(self):
        """Remove e retorna o item do topo da pilha."""
        if self.is_empty():
            raise IndexError("Não dá para desempilhar: a pilha está vazia.")
        return self._itens.pop()

    def peek(self):
        """Mostra o item do topo sem remover."""
        if self.is_empty():
            raise IndexError("Não dá para ver o topo: a pilha está vazia.")
        return self._itens[-1]

    def is_empty(self):
        """Retorna True se a pilha estiver vazia."""
        return len(self._itens) == 0

    def size(self):
        """Retorna quantos itens há na pilha."""
        return len(self._itens)


# Exemplo de uso:
p = Pilha()
p.push(10)
p.push(20)
p.push(30)

print("Topo:", p.peek())       # 30
print("Saiu:", p.pop())        # 30
print("Tamanho:", p.size())    # 2
print("Vazia?", p.is_empty())  # False
```

### Aplicações clássicas de pilha na computação

Além dos exemplos do cotidiano, pilhas aparecem muito em problemas reais:

* controle de chamadas de função
* processamento de expressões matemáticas
* verificação de parênteses e delimitadores
* mecanismo de desfazer e refazer
* algoritmos de backtracking

Em outras palavras, pilha aparece sempre que precisamos “voltar um passo” ou
recuperar a última decisão tomada.

### Limitações e cuidados

Pilha é excelente quando o problema combina com LIFO, mas não é ideal quando:

* precisamos acessar elementos do meio com frequência
* queremos remover um item arbitrário
* a ordem natural do problema não é a ordem inversa de inserção

Numa pilha, **a ordem das operações é tudo**. Como você sempre coloca e tira itens **pelo topo**, o que está no topo em cada momento depende exatamente do que você fez antes.

Pensa assim:

* Cada `push(x)` **coloca `x` em cima** de tudo que já estava lá.
* Cada `pop()` **tira exatamente o que está em cima naquele instante**.
* Então, se você quer saber “o que está no topo agora?”, você precisa olhar para a **sequência** de `push` e `pop` que aconteceu, na ordem em que aconteceu.

Um jeito simples de raciocinar é imaginar uma pilha física e ir acompanhando:

```python
p = Pilha()

p.push(10)   # pilha: [10]         topo = 10
p.push(20)   # pilha: [10, 20]     topo = 20
p.pop()      # sai 20, pilha: [10] topo = 10
p.push(30)   # pilha: [10, 30]     topo = 30
```

Repara que:

* O `push(20)` colocou o 20 no topo.
* Mas logo depois o `pop()` tirou o 20.
* Então o topo voltou a ser o 10.
* E quando fez `push(30)`, o topo passou a ser o 30.

Ou seja, **não dá para adivinhar o topo só olhando os números**; você precisa acompanhar a **história** da pilha: o que entrou e o que saiu, e **em qual ordem**.

> “Em pilha, o topo é sempre o resultado da última operação que mexeu nela.”

### Conclusão

Em resumo, a pilha é uma estrutura fundamental na computação porque organiza os dados de forma simples, previsível e eficiente, baseada na ideia de que o último elemento inserido é o primeiro a ser removido. Ao entender o conceito de topo, a regra LIFO e a importância da ordem das operações, o aluno consegue compreender não apenas como a pilha funciona, mas também por que ela aparece com tanta frequência em situações do mundo real e em sistemas computacionais, como no desfazer de ações e na navegação entre páginas. Esse entendimento conceitual é essencial para o aprendizado de outras estruturas de dados e algoritmos mais complexos, pois reforça a noção de comportamento, abstração e controle de acesso aos dados.
