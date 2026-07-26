---
description: >-
  Revisão dos principais elementos da linguagem Python, incluindo sintaxe
  básica, estruturas condicionais, laços de repetição e definição de funções.
---

# Python: sintaxe, controle de fluxo e funções

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Esta revisão tem como objetivo **relembrar os principais fundamentos da linguagem Python**, garantindo que todos os alunos tenham uma base sólida antes de avançar para conteúdos mais complexos, como estruturas de dados e Programação Orientada a Objetos.

Python é uma linguagem:

* simples de ler
* expressiva
* muito usada em ensino, mercado e pesquisa

Por isso, entender bem seus fundamentos é essencial.

### Sintaxe básica do Python

A sintaxe do Python é conhecida por ser **limpa e próxima da linguagem humana**.\
Diferente de outras linguagens, Python **não utiliza chaves (`{}`)** para delimitar blocos de código, mas sim **indentação**.

#### Exemplo simples

```python
idade = 18

if idade >= 18:
    print("Maior de idade")
```

A indentação **define o bloco de código**.\
Erros de indentação causam erro no programa.

### Variáveis e tipos básicos

Em Python, **não é necessário declarar o tipo da variável**, ele é inferido automaticamente.

Tipos mais comuns:

* `int` → números inteiros
* `float` → números decimais
* `str` → texto
* `bool` → verdadeiro ou falso

```python
nome = "Ana"
idade = 20
altura = 1.65
ativo = True
```

### Operadores básicos

#### Operadores aritméticos

* `+` soma
* `-` subtração
* `*` multiplicação
* `/` divisão
* `//` divisão inteira
* `%` resto

```python
resultado = 10 % 3  # 1
```

#### Operadores relacionais

* `==` igual
* `!=` diferente
* `>` maior
* `<` menor
* `>=` maior ou igual
* `<=` menor ou igual

### Estruturas condicionais (`if`, `elif`, `else`)

As estruturas condicionais permitem que o programa **tome decisões**.

```python
nota = 7

if nota >= 7:
    print("Aprovado")
elif nota >= 5:
    print("Recuperação")
else:
    print("Reprovado")
```

O código executa apenas **um dos blocos**.\
As condições são avaliadas de cima para baixo.

### Estruturas de repetição (laços)

#### Laço `while`

O `while` executa enquanto a condição for verdadeira.

```python
contador = 0

while contador < 5:
    print(contador)
    contador += 1
```

Usado quando:

* não se sabe exatamente quantas repetições serão necessárias

#### Laço `for`

O `for` é usado para percorrer sequências (listas, strings, intervalos).

```python
for i in range(5):
    print(i)
```

Outro exemplo com lista:

```python
nomes = ["Ana", "João", "Carlos"]

for nome in nomes:
    print(nome)
```

### Controle de laços (`break` e `continue`)

* `break`: interrompe o laço
* `continue`: pula para a próxima iteração

```python
for i in range(10):
    if i == 5:
        break
    print(i)
```

```python
for i in range(5):
    if i == 2:
        continue
    print(i)
```

### Listas

Listas armazenam vários valores em uma única variável.

```python
numeros = [1, 2, 3, 4]
numeros.append(5)
numeros.remove(2)
```

Percorrendo uma lista:

```python
for n in numeros:
    print(n)
```

Além de percorrer, listas permitem:

* acessar por índice
* alterar valores
* fatiar partes com `lista[inicio:fim]`
* crescer e diminuir dinamicamente

Exemplo:

```python
valores = [10, 20, 30, 40, 50]
print(valores[1:4])  # [20, 30, 40]
```

Esse tipo de operação aparece com frequência em exercícios de busca, ordenação
e manipulação de sequências.

### Mutabilidade e cuidado com referências

Listas são **mutáveis**, isto é, podem ser alteradas depois de criadas.

```python
dados = [1, 2, 3]
referencia = dados

referencia.append(4)
print(dados)  # [1, 2, 3, 4]
```

Isso é importante porque, em estruturas de dados, duas variáveis diferentes nem
sempre representam duas estruturas diferentes. Às vezes elas apontam para o
mesmo objeto.

### Funções em Python

Funções permitem **reutilizar código** e **organizar melhor o programa**.

#### Definição de função

```python
def saudacao(nome):
    print(f"Olá, {nome}!")
```

Chamando a função:

```python
saudacao("Ana")
```

### Funções com retorno

Funções podem retornar valores usando `return`.

```python
def soma(a, b):
    return a + b

resultado = soma(3, 5)
print(resultado)
```

Quando a função retorna, ela encerra a execução.

### Funções com valores padrão

```python
def apresentar(nome, curso="Computação"):
    print(nome, "-", curso)

apresentar("João")
apresentar("Maria", "Engenharia")
```

### Funções como ferramenta de abstração

Uma função bem definida ajuda a:

* separar responsabilidades
* reduzir repetição
* esconder detalhes internos
* facilitar testes e manutenção

Por isso, ao implementar estruturas de dados, é comum quebrar o problema em
operações menores, como inserir, remover, buscar, percorrer e validar.

### Escopo de variáveis

* Variáveis criadas **dentro da função** existem apenas nela
* Variáveis criadas **fora** são globais

```python
def teste():
    x = 10
    print(x)

teste()
# print(x) -> erro
```

### Boas práticas iniciais

* Use nomes claros para variáveis e funções
* Mantenha indentação consistente
* Evite funções muito grandes
* Comente quando necessário (sem exagero)
* Teste casos pequenos antes de testar casos maiores

### Relação com os próximos conteúdos

Essa revisão é fundamental para:

* entender estruturas de dados
* implementar classes e métodos
* escrever algoritmos de ordenação e busca
* compreender Programação Orientada a Objetos

Sem uma base sólida em sintaxe, controle de fluxo e funções, os próximos temas ficam muito mais difíceis.

### Conclusão

A revisão de sintaxe, controle de fluxo e funções em Python garante que todos os alunos estejam nivelados para avançar na disciplina. Esses conceitos formam a base de qualquer programa e são indispensáveis para compreender estruturas de dados, algoritmos e Programação Orientada a Objetos. Ao dominar esses fundamentos, o aluno ganha confiança para escrever código mais organizado, legível e eficiente, facilitando o aprendizado dos próximos conteúdos do curso.
