# 🎵 Exercício – Sistema de Playlist de Músicas com Lista Simplesmente Encadeada

**Objetivo:**  
Implementar uma estrutura de dados do tipo **Lista Simplesmente Encadeada (LSE)** em Python para gerenciar uma playlist de músicas, permitindo adicionar, buscar, remover e visualizar músicas.

---

## Descrição

Você deve criar uma **classe `LSE`** para representar uma Lista Simplesmente Encadeada utilizada para armazenar músicas de uma playlist.

Cada música deverá possuir:

- **Código**
- **Título**
- **Artista**

Cada elemento da lista deverá ser armazenado em um **`Nodo`**, contendo o dado e uma referência para o próximo elemento.

O sistema deverá utilizar uma estrutura semelhante a:

```text
head
 ↓
[Música] -> [Música] -> [Música] -> None
```

O programa deve permitir que o usuário interaja com a playlist através de um **menu no terminal**.

---

## Regras

1. A classe **`Musica`** deve representar uma música e possuir, no mínimo, os seguintes atributos:
   - `codigo`
   - `titulo`
   - `artista`

2. A classe **`Nodo`** deve armazenar:
   - o dado;
   - a referência `proximo` para o próximo nodo da lista.

3. A classe **`LSE`** deve possuir, no mínimo, os seguintes atributos:
   - `head` – referência para o primeiro elemento da lista.
   - `tail` – referência para o último elemento da lista.
   - `quantidade_itens` – quantidade de elementos armazenados.

4. A classe **`LSE`** deve possuir, no mínimo, os seguintes métodos:
   - `__init__(self)` – cria a lista.
   - `is_empty(self)` – retorna `True` se a lista estiver vazia.
   - `inserir_inicio(self, dado_a_ser_inserido)` – adiciona uma música no início da lista.
   - `inserir_fim(self, dado_a_ser_inserido)` – adiciona uma música no final da lista.
   - `buscar(self, codigo)` – procura uma música pelo código.
   - `remover(self, codigo)` – remove uma música pelo código.
   - `imprimir_lista_completa(self)` – percorre e exibe todas as músicas da lista.

5. O programa deve possuir o seguinte **menu**:

```text
==============================
       PLAYLIST DE MÚSICAS
==============================
1 - Adicionar música no início
2 - Adicionar música no final
3 - Buscar música
4 - Remover música
5 - Exibir playlist
6 - Exibir quantidade de músicas
0 - Sair
==============================

Digite a opção desejada:
```

6. Ao adicionar uma música, o usuário deverá informar:
   - código;
   - título;
   - artista.

7. A opção **Adicionar música no início** deve utilizar o método `inserir_inicio()`.

8. A opção **Adicionar música no final** deve utilizar o método `inserir_fim()`.

9. A opção **Buscar música** deve solicitar o código e percorrer a LSE até encontrar a música correspondente.

10. A opção **Remover música** deve solicitar o código e remover a música correspondente da LSE.

11. Ao remover uma música, o programa deve tratar corretamente os seguintes casos:
   - remoção do primeiro elemento;
   - remoção de um elemento no meio da lista;
   - remoção do último elemento;
   - código inexistente;
   - lista vazia.

12. A opção **Exibir playlist** deve percorrer a lista a partir de `head` utilizando a referência `proximo`.

13. A opção **Exibir quantidade de músicas** deve mostrar o valor de `quantidade_itens`.

14. Não é permitido utilizar uma `list` do Python para armazenar as músicas da playlist.

15. O projeto deve utilizar **POO e arquivos externos**.

16. O programa deve utilizar **tratamento de exceções** para entradas inválidas no terminal.

17. Entradas numéricas devem ser validadas antes de serem utilizadas.

18. Entradas de texto devem ser tratadas com `strip()` e não podem ser vazias quando forem obrigatórias.

19. O programa deve continuar em execução após erros de entrada, exibindo uma mensagem adequada ao usuário.

20. A lógica de manipulação da LSE não deve ficar no `main.py`; ela deve estar encapsulada nos métodos da classe `LSE`.

---

## Boas práticas e tratamento de dados

Além da implementação da Lista Simplesmente Encadeada, o programa deve seguir boas práticas de programação e tratar corretamente os dados informados pelo usuário no terminal.

### Entrada de dados

1. Todas as entradas do usuário devem ser tratadas antes de serem utilizadas.

2. Utilize `strip()` para remover espaços desnecessários no início e no final dos textos informados.

3. Valores numéricos, como código da música e opção do menu, devem ser convertidos de forma segura.

4. Caso o usuário informe um valor inválido, o programa não deve encerrar inesperadamente. Deve exibir uma mensagem de erro e solicitar o valor novamente.

Exemplo de comportamento esperado:

```text
Digite a opção desejada: teste
Erro: digite um número inteiro válido.

Digite a opção desejada: 9
Erro: opção inválida.

Digite a opção desejada:
```

### Tratamento de exceções

O programa deve utilizar tratamento de exceções quando necessário, principalmente para conversões de dados informados pelo usuário.

Exemplo:

```python
try:
    codigo = int(input("Digite o código da música: ").strip())
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
- código da música;
- título vazio;
- artista vazio;
- código duplicado;
- busca por código inexistente;
- remoção por código inexistente;
- tentativa de operação em playlist vazia.

O programa não deve permitir o cadastro de uma música com título ou artista vazio.

Exemplo:

```text
Digite o título da música:

Erro: o título não pode estar vazio.
```

### Organização do código

Evite concentrar toda a lógica dentro do `while` principal.

Crie funções auxiliares quando necessário, por exemplo:

```python
def ler_inteiro(mensagem):
    pass

def exibir_menu():
    pass

def cadastrar_musica():
    pass
```

O `main.py` deve ser responsável principalmente pela interação com o usuário.

A manipulação da estrutura encadeada deve permanecer dentro da classe `LSE`.

### Boas práticas gerais

- Utilize nomes de variáveis e métodos claros.
- Evite repetir código desnecessariamente.
- Separe responsabilidades entre as classes.
- Mantenha a indentação correta.
- Utilize mensagens claras para o usuário.
- Não utilize números ou valores sem significado espalhados pelo código quando puderem ser evitados.
- Não acesse ou altere diretamente `head`, `tail` ou `proximo` a partir do `main.py`.
- Toda alteração na lista deve ser realizada pelos métodos da classe `LSE`.
- Garanta que `quantidade_itens` permaneça consistente após inserções e remoções.
- O programa deve continuar funcionando após uma entrada inválida, sempre que possível.

---

## Organização sugerida

```text
playlist/
│
├── Musica.py
├── Nodo.py
├── LSE.py
└── main.py
```

- **`Musica.py`** – classe responsável pelos dados de cada música.
- **`Nodo.py`** – classe responsável pela estrutura de cada nodo.
- **`LSE.py`** – classe responsável pela Lista Simplesmente Encadeada.
- **`main.py`** – responsável pelo menu e pela interação com o usuário.

---

## Exemplo de execução

```text
==============================
       PLAYLIST DE MÚSICAS
==============================
1 - Adicionar música no início
2 - Adicionar música no final
3 - Buscar música
4 - Remover música
5 - Exibir playlist
6 - Exibir quantidade de músicas
0 - Sair
==============================

Digite a opção desejada: 2

Digite o código da música: 1
Digite o título da música: Numb
Digite o artista: Linkin Park

Música adicionada com sucesso.

==============================
       PLAYLIST DE MÚSICAS
==============================
1 - Adicionar música no início
2 - Adicionar música no final
3 - Buscar música
4 - Remover música
5 - Exibir playlist
6 - Exibir quantidade de músicas
0 - Sair
==============================

Digite a opção desejada: 2

Digite o código da música: 2
Digite o título da música: Yellow
Digite o artista: Coldplay

Música adicionada com sucesso.

==============================
       PLAYLIST DE MÚSICAS
==============================
1 - Adicionar música no início
2 - Adicionar música no final
3 - Buscar música
4 - Remover música
5 - Exibir playlist
6 - Exibir quantidade de músicas
0 - Sair
==============================

Digite a opção desejada: 1

Digite o código da música: 3
Digite o título da música: Believer
Digite o artista: Imagine Dragons

Música adicionada com sucesso.

==============================
       PLAYLIST DE MÚSICAS
==============================
1 - Adicionar música no início
2 - Adicionar música no final
3 - Buscar música
4 - Remover música
5 - Exibir playlist
6 - Exibir quantidade de músicas
0 - Sair
==============================

Digite a opção desejada: 5

===== PLAYLIST =====

3 - Believer - Imagine Dragons
1 - Numb - Linkin Park
2 - Yellow - Coldplay

==============================
       PLAYLIST DE MÚSICAS
==============================
1 - Adicionar música no início
2 - Adicionar música no final
3 - Buscar música
4 - Remover música
5 - Exibir playlist
6 - Exibir quantidade de músicas
0 - Sair
==============================

Digite a opção desejada: 3

Digite o código da música: 1

Música encontrada:
1 - Numb - Linkin Park

==============================
       PLAYLIST DE MÚSICAS
==============================
1 - Adicionar música no início
2 - Adicionar música no final
3 - Buscar música
4 - Remover música
5 - Exibir playlist
6 - Exibir quantidade de músicas
0 - Sair
==============================

Digite a opção desejada: 4

Digite o código da música: 1

Música removida com sucesso.

==============================
       PLAYLIST DE MÚSICAS
==============================
1 - Adicionar música no início
2 - Adicionar música no final
3 - Buscar música
4 - Remover música
5 - Exibir playlist
6 - Exibir quantidade de músicas
0 - Sair
==============================

Digite a opção desejada: 6

Quantidade de músicas: 2

==============================
       PLAYLIST DE MÚSICAS
==============================
1 - Adicionar música no início
2 - Adicionar música no final
3 - Buscar música
4 - Remover música
5 - Exibir playlist
6 - Exibir quantidade de músicas
0 - Sair
==============================

Digite a opção desejada: 0

Programa encerrado.
```

---

## Critérios

- Implementação correta da classe `Musica`.
- Implementação correta da classe `Nodo`.
- Implementação correta da classe `LSE`.
- Utilização correta de `head`, `tail` e `proximo`.
- Inserção correta no início da lista.
- Inserção correta no final da lista.
- Busca de músicas percorrendo a LSE.
- Remoção correta de músicas pelo código.
- Atualização correta de `head` e `tail` após remoções.
- Controle correto de `quantidade_itens`.
- Não utilização de `list` do Python como estrutura principal.
- Utilize POO e arquivos externos.
- Boa organização do código e legibilidade.
- Tratamento de erros de entrada, como opção inválida, lista vazia e código inexistente.
- Utilização adequada de `try` e `except` para conversões e entradas inválidas.
- Tratamento de exceções específicas, evitando `except` genérico.
- Validação dos dados recebidos pelo terminal.
- Utilização de `strip()` nas entradas textuais.
- Validação de campos obrigatórios.
- Tratamento de códigos duplicados.
- Criação de funções auxiliares para evitar repetição de código.
- Separação adequada de responsabilidades entre `main.py`, `Musica`, `Nodo` e `LSE`.
- O `main.py` não deve manipular diretamente `head`, `tail` ou `proximo`.
- O programa deve permanecer em execução após entradas inválidas sempre que possível.
