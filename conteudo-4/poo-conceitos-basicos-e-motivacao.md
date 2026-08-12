---
description: >-
  Introdução à programação orientada a objetos, abordando o conceito de
  abstração e a motivação para o uso de classes na organização do código.
---

# POO: conceitos básicos e motivação

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

A **Programação Orientada a Objetos (POO)** é um paradigma de programação que organiza o código em torno de **objetos**, que representam entidades do mundo real ou conceitos do sistema.\
Em vez de pensar apenas em funções soltas que manipulam dados, a POO propõe **unir dados e comportamentos** em uma mesma estrutura.

A principal ideia da POO é tornar o código:

* mais organizado
* mais fácil de entender
* mais próximo da forma como pensamos problemas reais
* mais simples de manter e evoluir

<figure><img src="../.gitbook/assets/image (25).png" alt="" width="563"><figcaption></figcaption></figure>

### Por que surgiu a Programação Orientada a Objetos

Antes da POO, muitos programas eram escritos de forma **procedural**, ou seja:

* dados ficavam separados
* funções manipulavam esses dados
* o crescimento do sistema tornava o código difícil de entender e manter

Com o tempo, percebeu-se que sistemas grandes:

* ficavam difíceis de modificar
* tinham muito código repetido
* quebravam facilmente quando algo mudava

A POO surgiu como uma forma de **organizar melhor a complexidade**, agrupando informações relacionadas e suas ações em um único lugar.

### O que é um objeto

Um **objeto** representa algo que existe no mundo real ou no contexto do sistema.

Exemplos de objetos:

* um aluno
* um carro
* uma conta bancária
* um pedido de compra
* um produto em uma loja

Cada objeto possui:

* **características** (informações)
* **comportamentos** (ações que ele pode executar)

Por exemplo, um carro:

* características: cor, modelo, velocidade
* comportamentos: acelerar, frear, ligar, desligar

### O que é uma classe

Uma **classe** é um **modelo**, um **molde**, que define como os objetos daquele tipo serão criados.

* A classe descreve o que o objeto **é**
* A classe descreve o que o objeto **faz**
* O objeto é uma instância da classe

Exemplo conceitual:

* Classe: `Aluno`
* Objetos: João, Maria, Ana (cada um com seus próprios dados)

Uma analogia simples:

> A classe é a planta de uma casa.\
> Cada casa construída a partir dessa planta é um objeto.

### Por que usar classes para organizar o código

Classes ajudam a organizar o código porque:

* agrupam dados e comportamentos relacionados
* evitam espalhar regras de negócio pelo sistema
* facilitam a leitura e manutenção
* tornam o código mais modular

Sem classes, o sistema tende a virar um conjunto grande de variáveis e funções soltas, difíceis de entender.

### Conceito de abstração

**Abstração** é a capacidade de representar algo do mundo real focando apenas no que é **relevante** para o sistema, ignorando detalhes desnecessários.

Exemplo:\
Um sistema de matrícula de alunos não precisa saber:

* a cor do cabelo do aluno
* a altura
* o tipo de calçado

Ele precisa saber:

* nome
* matrícula
* curso
* disciplinas matriculadas

Abstrair é escolher **o que importa** para resolver o problema.

> “Abstração é representar a realidade de forma simplificada.”

### Abstração no dia a dia

* **Mapa**: não mostra cada árvore e cada prédio, apenas o que é relevante para se localizar.
* **Controle remoto**: você aperta botões sem precisar saber como o circuito funciona.
* **Caixa eletrônico**: você saca dinheiro sem saber como o banco processa internamente a transação.

Na POO, a abstração funciona da mesma forma: o usuário do objeto não precisa saber como tudo funciona por dentro.

### Relação entre classes, objetos e abstração

* A **classe** define a abstração
* O **objeto** é a materialização dessa abstração
* O programador usa o objeto sem precisar conhecer todos os detalhes internos

Isso permite que o sistema cresça sem virar algo caótico.

### Outros pilares importantes da POO

Além de classe, objeto e abstração, existem outros conceitos bastante associados à POO:

* **encapsulamento**: controlar como o estado interno é acessado e alterado
* **herança**: reaproveitar características entre classes
* **polimorfismo**: permitir interfaces parecidas para objetos diferentes

Neste momento do curso, o foco principal está em **abstração e organização do código**, mas é importante reconhecer esse vocabulário desde já.

### Encapsulamento na prática

Encapsular significa evitar que qualquer parte do sistema mexa no estado do objeto de qualquer jeito. Em vez disso, criamos operações controladas.

Exemplo conceitual:

* em vez de alterar um saldo livremente
* usamos métodos como `depositar()` e `sacar()`

Assim, o próprio objeto ajuda a preservar regras importantes do problema.

### Comparação: código sem POO × com POO

#### Sem POO

* dados espalhados
* funções genéricas
* difícil saber indicações de responsabilidade
* mudanças geram efeitos colaterais

#### Com POO

* dados e comportamentos juntos
* responsabilidades bem definidas
* código mais legível
* mudanças localizadas

### Motivação para o uso de POO em sistemas reais

A POO é amplamente usada porque:

* facilita o trabalho em equipe
* melhora a manutenção do código
* reduz duplicação
* ajuda a modelar sistemas complexos
* aproxima o código da realidade do problema

Por isso, a maioria das linguagens modernas suporta POO, como:

* Java
* Python
* C++
* C#
* JavaScript (com classes)

### POO e a evolução do sistema

Sistemas reais estão sempre mudando:

* novas regras
* novos requisitos
* novas funcionalidades

A POO ajuda a:

* isolar mudanças
* reaproveitar código
* manter o sistema compreensível ao longo do tempo

### Relação com estruturas de dados

Ao longo da disciplina, várias estruturas serão modeladas como classes:

* `Pilha`
* `Fila`
* `ListaEncadeada`
* `ArvoreBinaria`

Isso mostra que POO não é um tema isolado. Ela será uma ferramenta para organizar o estado interno das estruturas e as operações que atuam sobre ele.

### Conclusão

A Programação Orientada a Objetos surge como uma resposta à complexidade crescente dos sistemas, oferecendo uma forma mais organizada, intuitiva e sustentável de desenvolver software. Ao trabalhar com classes, objetos e abstração, o programador passa a estruturar o código de maneira mais próxima do mundo real, facilitando o entendimento, a manutenção e a evolução do sistema. Esses conceitos formam a base para outros pilares da POO e são fundamentais para o desenvolvimento de aplicações modernas e bem estruturadas.
