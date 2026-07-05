---
description: >-
  Estudo das estruturas de dados nativas do Python e conceitos de modularização,
  visando melhor organização, reutilização e abstração do código.
---

# Python: estruturas de dados e modularização

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Nesta etapa, o objetivo é revisar as **estruturas de dados nativas do Python** e introduzir o conceito de **modularização**, mostrando como organizar melhor o código, reaproveitar funcionalidades e tornar os programas mais legíveis e fáceis de manter.

Esses conceitos são fundamentais para:

* escrever código mais limpo
* evitar repetição
* dividir problemas grandes em partes menores
* preparar o terreno para estruturas de dados mais avançadas

### O que são estruturas de dados

Uma **estrutura de dados** é uma forma de **organizar e armazenar informações** para que possam ser usadas de maneira eficiente.

No Python, algumas estruturas já vêm prontas, o que facilita muito o desenvolvimento inicial.\
Mesmo assim, é importante entender **quando e por que usar cada uma**.

### Listas (`list`)

As **listas** são estruturas ordenadas e mutáveis, ou seja:

* mantêm a ordem dos elementos
* podem ser modificadas após a criação

#### Exemplo

```python
numeros = [1, 2, 3, 4]
numeros.append(5)
numeros.remove(2)
```

Características importantes:

* acesso por índice (`numeros[0]`)
* permitem elementos repetidos
* podem armazenar tipos diferentes

As listas são muito usadas e servem como base para entender:

* pilhas
* filas
* algoritmos de ordenação

### Tuplas (`tuple`)

As **tuplas** são semelhantes às listas, porém **imutáveis**.

```python
coordenadas = (10, 20)
```

Características:

* não podem ser alteradas após a criação
* garantem que os dados não serão modificados
* são usadas quando a informação é fixa

Uso comum:

* coordenadas
* configurações
* retorno de múltiplos valores de funções

### Conjuntos (`set`)

Os **conjuntos** armazenam elementos **sem repetição** e **sem ordem definida**.

```python
numeros = {1, 2, 3, 3, 4}
print(numeros)  # {1, 2, 3, 4}
```

Características:

* não permitem valores duplicados
* são eficientes para verificar existência de elementos
* não usam índices

Uso típico:

* remover duplicatas
* operações matemáticas (união, interseção)

### Dicionários (`dict`)

Os **dicionários** armazenam dados no formato **chave → valor**.

```python
aluno = {
    "nome": "Ana",
    "idade": 20,
    "curso": "Computação"
}
```

Acesso aos valores:

```python
print(aluno["nome"])
```

Características:

* acesso rápido por chave
* chaves devem ser únicas
* muito usados para representar objetos simples

Dicionários são uma ponte natural para POO.

### Percorrendo estruturas de dados

As estruturas de dados normalmente são percorridas com `for`.

```python
for numero in numeros:
    print(numero)
```

Para dicionários:

```python
for chave, valor in aluno.items():
    print(chave, valor)
```

Percorrer estruturas é uma habilidade essencial para:

* busca
* validação
* processamento de dados

### Estruturas de dados aninhadas

Python permite **estruturas dentro de estruturas**.

```python
turma = [
    {"nome": "Ana", "nota": 8},
    {"nome": "João", "nota": 6}
]
```

Isso permite modelar dados mais complexos, mas exige atenção na leitura e manutenção do código.

### O que é modularização

**Modularização** é o processo de **dividir um programa em partes menores**, chamadas de **módulos**.

Cada módulo:

* tem uma responsabilidade clara
* pode ser reutilizado
* facilita testes e manutenção

A ideia é:

> “Um arquivo deve resolver um problema específico.”

### Criando um módulo em Python

Um módulo é simplesmente um **arquivo `.py`**.

Exemplo: `operacoes.py`

```python
def soma(a, b):
    return a + b

def subtracao(a, b):
    return a - b
```

Usando o módulo em outro arquivo:

```python
import operacoes

print(operacoes.soma(3, 2))
```

### Importando partes específicas de um módulo

```python
from operacoes import soma

print(soma(5, 4))
```

Isso ajuda a:

* deixar o código mais legível
* evitar chamadas longas

### Organização de código com módulos

Separar o código em módulos ajuda a:

* evitar arquivos muito grandes
* organizar funcionalidades
* facilitar o trabalho em equipe

Exemplo de organização:

* `main.py` → fluxo principal
* `modelos.py` → classes
* `utils.py` → funções auxiliares

### Modularização e reutilização

Quando um código está bem modularizado:

* ele pode ser reutilizado em outros projetos
* alterações ficam localizadas
* erros são mais fáceis de corrigir

Esse conceito será muito importante ao trabalhar com:

* estruturas de dados
* POO
* projetos maiores

### Relação com abstração

Modularizar também é uma forma de **abstração**:

* você usa uma função ou módulo
* sem precisar saber como ele funciona internamente

Isso deixa o código mais simples de usar e entender.

### Boas práticas iniciais

* escolha bem a estrutura de dados
* use nomes claros
* evite misturar responsabilidades
* divida o código em módulos lógicos
* não repita código desnecessariamente

### Conclusão

As estruturas de dados nativas do Python oferecem formas flexíveis e poderosas de organizar informações, enquanto a modularização permite estruturar o código de maneira mais clara, reutilizável e organizada. Ao dominar listas, tuplas, conjuntos, dicionários e o uso de módulos, o aluno desenvolve uma base sólida para resolver problemas de forma mais eficiente e preparar-se para estruturas de dados mais avançadas e para a Programação Orientada a Objetos.
