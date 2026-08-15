# 🎬 Exercício – Catálogo de Filmes com Lista Duplamente Encadeada

**Objetivo:**  
Implementar uma estrutura de dados do tipo **Lista Duplamente Encadeada (LDE)** em Python para gerenciar um catálogo de filmes, permitindo adicionar, buscar, remover e visualizar os filmes nos dois sentidos da lista.

---

## Descrição

Você deve desenvolver um sistema de **catálogo de filmes** utilizando uma Lista Duplamente Encadeada.

Cada filme deverá possuir:

- **Código**
- **Título**
- **Gênero**

Cada elemento da lista deverá ser armazenado em um **`DNodo`**, contendo:

- o dado;
- uma referência para o próximo nodo;
- uma referência para o nodo anterior.

A estrutura deverá funcionar de forma semelhante a:

```text
None <- [Filme] <=> [Filme] <=> [Filme] -> None
          ↑                         ↑
         head                      tail
```

O usuário deverá interagir com o sistema através de um **menu no terminal**.

---

## Regras

1. A classe **`Filme`** deve representar um filme e possuir, no mínimo, os seguintes atributos:
   - `codigo`
   - `titulo`
   - `genero`

2. A classe **`DNodo`** deve armazenar:
   - o dado;
   - a referência `proximo`;
   - a referência `anterior`.

3. A classe **`LDE`** deve possuir, no mínimo, os seguintes atributos:
   - `head` – referência para o primeiro elemento da lista.
   - `tail` – referência para o último elemento da lista.
   - `quantidade_itens` – quantidade de elementos armazenados.

4. A classe **`LDE`** deve possuir, no mínimo, os seguintes métodos:
   - `__init__(self)` – cria a lista.
   - `is_empty(self)` – retorna `True` se a lista estiver vazia.
   - `inserir_inicio(self, dado_a_ser_inserido)` – adiciona um filme no início.
   - `inserir_fim(self, dado_a_ser_inserido)` – adiciona um filme no final.
   - `buscar(self, codigo)` – procura um filme pelo código.
   - `remover(self, codigo)` – remove um filme pelo código.
   - `imprimir_inicio_fim(self)` – percorre e exibe os filmes de `head` até `tail`.
   - `imprimir_fim_inicio(self)` – percorre e exibe os filmes de `tail` até `head`.

5. O programa deve possuir o seguinte **menu**:

```text
==============================
       CATÁLOGO DE FILMES
==============================
1 - Adicionar filme no início
2 - Adicionar filme no final
3 - Buscar filme
4 - Remover filme
5 - Exibir catálogo do início ao fim
6 - Exibir catálogo do fim ao início
7 - Exibir quantidade de filmes
0 - Sair
==============================

Digite a opção desejada:
```

6. Ao adicionar um filme, o usuário deverá informar:
   - código;
   - título;
   - gênero.

7. A opção **Adicionar filme no início** deve utilizar o método `inserir_inicio()`.

8. A opção **Adicionar filme no final** deve utilizar o método `inserir_fim()`.

9. A opção **Buscar filme** deve solicitar o código e percorrer a LDE até encontrar o filme correspondente.

10. A opção **Remover filme** deve solicitar o código e remover o filme correspondente da LDE.

11. Ao remover um filme, o programa deve tratar corretamente:
   - remoção do primeiro elemento;
   - remoção de um elemento no meio da lista;
   - remoção do último elemento;
   - remoção do único elemento da lista;
   - código inexistente;
   - lista vazia.

12. Após uma remoção, as referências `proximo` e `anterior` dos nodos vizinhos devem ser atualizadas corretamente.

13. A opção **Exibir catálogo do início ao fim** deve iniciar em `head` e percorrer a estrutura utilizando `proximo`.

14. A opção **Exibir catálogo do fim ao início** deve iniciar em `tail` e percorrer a estrutura utilizando `anterior`.

15. A opção **Exibir quantidade de filmes** deve mostrar o valor de `quantidade_itens`.

16. Não é permitido utilizar uma `list` do Python para armazenar os filmes do catálogo.

17. O projeto deve utilizar **POO e arquivos externos**.

18. O programa deve utilizar **tratamento de exceções** para entradas inválidas no terminal.

19. Entradas numéricas devem ser validadas antes de serem utilizadas.

20. Entradas de texto devem ser tratadas com `strip()` e não podem ser vazias quando forem obrigatórias.

21. O programa deve continuar em execução após erros de entrada, exibindo uma mensagem adequada ao usuário.

22. A lógica de manipulação da LDE não deve ficar no `main.py`; ela deve permanecer encapsulada nos métodos da classe `LDE`.

---

## Boas práticas e tratamento de dados

Além da implementação da Lista Duplamente Encadeada, o programa deve seguir boas práticas de programação e tratar corretamente os dados informados pelo usuário no terminal.

### Entrada de dados

Todas as entradas do usuário devem ser tratadas antes de serem utilizadas.

Utilize `strip()` para remover espaços desnecessários no início e no final dos textos.

Valores numéricos, como código do filme e opção do menu, devem ser convertidos de forma segura.

Caso o usuário informe um valor inválido, o programa não deve encerrar inesperadamente. Deve exibir uma mensagem de erro e solicitar o valor novamente.

Exemplo:

```text
Digite a opção desejada: abc
Erro: digite um número inteiro válido.

Digite a opção desejada: 9
Erro: opção inválida.
```

### Tratamento de exceções

Utilize tratamento de exceções quando necessário, principalmente para conversões de dados informados pelo usuário.

Exemplo:

```python
try:
    codigo = int(input("Digite o código do filme: ").strip())
except ValueError:
    print("Erro: digite um número inteiro válido.")
```

Evite utilizar:

```python
except:
```

Prefira tratar exceções específicas, como:

```python
except ValueError:
```

### Validações

O sistema deve validar, no mínimo:

- opção informada no menu;
- código do filme;
- título vazio;
- gênero vazio;
- código duplicado;
- busca por código inexistente;
- remoção por código inexistente;
- tentativa de operação em catálogo vazio.

O programa não deve permitir o cadastro de um filme com título ou gênero vazio.

Exemplo:

```text
Digite o título do filme:

Erro: o título não pode estar vazio.
```

### Organização do código

Evite concentrar toda a lógica dentro do `while` principal.

Crie funções auxiliares quando necessário, por exemplo:

```python
def ler_inteiro(mensagem):
    pass

def ler_texto(mensagem):
    pass

def exibir_menu():
    pass
```

O `main.py` deve ser responsável principalmente pela interação com o usuário.

Toda a manipulação de `head`, `tail`, `proximo` e `anterior` deve permanecer dentro da classe `LDE`.

### Boas práticas gerais

- Utilize nomes de variáveis e métodos claros.
- Evite repetir código desnecessariamente.
- Separe responsabilidades entre as classes.
- Mantenha a indentação correta.
- Utilize mensagens claras para o usuário.
- Não manipule diretamente `head`, `tail`, `proximo` ou `anterior` a partir do `main.py`.
- Garanta que `quantidade_itens` permaneça consistente após inserções e remoções.
- Garanta que `head.anterior` permaneça `None`.
- Garanta que `tail.proximo` permaneça `None`.
- O programa deve continuar funcionando após entradas inválidas sempre que possível.

---

## Organização sugerida

```text
catalogo_filmes/
│
├── Filme.py
├── DNodo.py
├── LDE.py
└── main.py
```

- **`Filme.py`** – classe responsável pelos dados de cada filme.
- **`DNodo.py`** – classe responsável pela estrutura de cada nodo duplo.
- **`LDE.py`** – classe responsável pela Lista Duplamente Encadeada.
- **`main.py`** – responsável pelo menu e pela interação com o usuário.

---

## Exemplo de execução

```text
==============================
       CATÁLOGO DE FILMES
==============================
1 - Adicionar filme no início
2 - Adicionar filme no final
3 - Buscar filme
4 - Remover filme
5 - Exibir catálogo do início ao fim
6 - Exibir catálogo do fim ao início
7 - Exibir quantidade de filmes
0 - Sair
==============================

Digite a opção desejada: 2

Digite o código do filme: 1
Digite o título do filme: Interestelar
Digite o gênero do filme: Ficção científica

Filme adicionado com sucesso.

==============================
       CATÁLOGO DE FILMES
==============================
1 - Adicionar filme no início
2 - Adicionar filme no final
3 - Buscar filme
4 - Remover filme
5 - Exibir catálogo do início ao fim
6 - Exibir catálogo do fim ao início
7 - Exibir quantidade de filmes
0 - Sair
==============================

Digite a opção desejada: 2

Digite o código do filme: 2
Digite o título do filme: Matrix
Digite o gênero do filme: Ficção científica

Filme adicionado com sucesso.

==============================
       CATÁLOGO DE FILMES
==============================
1 - Adicionar filme no início
2 - Adicionar filme no final
3 - Buscar filme
4 - Remover filme
5 - Exibir catálogo do início ao fim
6 - Exibir catálogo do fim ao início
7 - Exibir quantidade de filmes
0 - Sair
==============================

Digite a opção desejada: 1

Digite o código do filme: 3
Digite o título do filme: Batman
Digite o gênero do filme: Ação

Filme adicionado com sucesso.

==============================
       CATÁLOGO DE FILMES
==============================
1 - Adicionar filme no início
2 - Adicionar filme no final
3 - Buscar filme
4 - Remover filme
5 - Exibir catálogo do início ao fim
6 - Exibir catálogo do fim ao início
7 - Exibir quantidade de filmes
0 - Sair
==============================

Digite a opção desejada: 5

===== CATÁLOGO: INÍCIO -> FIM =====

3 - Batman - Ação
1 - Interestelar - Ficção científica
2 - Matrix - Ficção científica

==============================
       CATÁLOGO DE FILMES
==============================
1 - Adicionar filme no início
2 - Adicionar filme no final
3 - Buscar filme
4 - Remover filme
5 - Exibir catálogo do início ao fim
6 - Exibir catálogo do fim ao início
7 - Exibir quantidade de filmes
0 - Sair
==============================

Digite a opção desejada: 6

===== CATÁLOGO: FIM -> INÍCIO =====

2 - Matrix - Ficção científica
1 - Interestelar - Ficção científica
3 - Batman - Ação

==============================
       CATÁLOGO DE FILMES
==============================
1 - Adicionar filme no início
2 - Adicionar filme no final
3 - Buscar filme
4 - Remover filme
5 - Exibir catálogo do início ao fim
6 - Exibir catálogo do fim ao início
7 - Exibir quantidade de filmes
0 - Sair
==============================

Digite a opção desejada: 3

Digite o código do filme: 1

Filme encontrado:
1 - Interestelar - Ficção científica

==============================
       CATÁLOGO DE FILMES
==============================
1 - Adicionar filme no início
2 - Adicionar filme no final
3 - Buscar filme
4 - Remover filme
5 - Exibir catálogo do início ao fim
6 - Exibir catálogo do fim ao início
7 - Exibir quantidade de filmes
0 - Sair
==============================

Digite a opção desejada: 4

Digite o código do filme: 1

Filme removido com sucesso.

==============================
       CATÁLOGO DE FILMES
==============================
1 - Adicionar filme no início
2 - Adicionar filme no final
3 - Buscar filme
4 - Remover filme
5 - Exibir catálogo do início ao fim
6 - Exibir catálogo do fim ao início
7 - Exibir quantidade de filmes
0 - Sair
==============================

Digite a opção desejada: 7

Quantidade de filmes: 2

==============================
       CATÁLOGO DE FILMES
==============================
1 - Adicionar filme no início
2 - Adicionar filme no final
3 - Buscar filme
4 - Remover filme
5 - Exibir catálogo do início ao fim
6 - Exibir catálogo do fim ao início
7 - Exibir quantidade de filmes
0 - Sair
==============================

Digite a opção desejada: 0

Programa encerrado.
```

---

## Critérios

- Implementação correta da classe `Filme`.
- Implementação correta da classe `DNodo`.
- Implementação correta da classe `LDE`.
- Utilização correta de `head` e `tail`.
- Utilização correta das referências `proximo` e `anterior`.
- Inserção correta no início da lista.
- Inserção correta no final da lista.
- Busca de filmes percorrendo a LDE.
- Remoção correta de filmes pelo código.
- Atualização correta das referências dos nodos após remoções.
- Atualização correta de `head` e `tail`.
- Percurso correto da lista do início ao fim.
- Percurso correto da lista do fim ao início.
- Controle correto de `quantidade_itens`.
- Não utilização de `list` do Python como estrutura principal.
- Utilização de POO e arquivos externos.
- Utilização adequada de `try` e `except`.
- Tratamento de exceções específicas.
- Validação dos dados recebidos pelo terminal.
- Utilização de `strip()` nas entradas textuais.
- Validação de campos obrigatórios.
- Tratamento de códigos duplicados.
- Boa separação de responsabilidades entre `main.py`, `Filme`, `DNodo` e `LDE`.
- O `main.py` não deve manipular diretamente `head`, `tail`, `proximo` ou `anterior`.
- O programa deve permanecer em execução após entradas inválidas sempre que possível.
- Boa organização do código e legibilidade.
