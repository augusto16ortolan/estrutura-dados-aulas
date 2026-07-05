# 🏥 Exercício – Sistema de Fila de Atendimento no Hospital com Classe `Fila`

**Objetivo:**  
Implementar uma estrutura de dados do tipo **Fila** em Python para simular o atendimento de pacientes em um hospital, respeitando a ordem de chegada, mas priorizando casos urgentes.

---

## Descrição

Você deve criar uma **classe `Fila`** para representar uma fila de atendimento.  
O sistema terá **duas filas**:

- **Fila de prioridade** – para pacientes com casos urgentes (idosos, gestantes, emergências).
- **Fila normal** – para pacientes sem prioridade.

O programa deve permitir que o usuário digite comandos para gerenciar o atendimento.

---

## Regras

1. **Classe `Fila`** deve ter no mínimo os seguintes métodos:
   - `__init__(self)` – cria a fila.
   - `esta_vazia(self)` – retorna `True` se a fila estiver vazia.
   - `enfileirar(self, item)` – adiciona um item no final da fila.
   - `desenfileirar(self)` – remove e retorna o item do início da fila.
   - `tamanho(self)` – retorna a quantidade de elementos na fila.
   - `__str__(self)` – retorna uma representação em string da fila.

2. O sistema deve permitir os seguintes **comandos**:
   - `chegada <nome> <prioridade>` → adiciona um paciente na fila de prioridade (`prioridade = 1`) ou na fila normal (`prioridade = 0`).
   - `atender` → remove e mostra o próximo paciente a ser atendido (priorizando a fila de prioridade).
   - `fila` → exibe o estado atual das filas.
   - `sair` → encerra o programa.

3. O programa deve **sempre atender primeiro** os pacientes da fila de prioridade.

---

## Exemplo de execução

```
Digite um comando: chegada João 0
João adicionado à fila NORMAL.

Digite um comando: chegada Maria 1
Maria adicionado à fila de PRIORIDADE.

Digite um comando: chegada Pedro 0
Pedro adicionado à fila NORMAL.

Digite um comando: fila
Fila prioridade: ['Maria']
Fila normal: ['João', 'Pedro']

Digite um comando: atender
Atendendo Maria (prioridade).

Digite um comando: atender
Atendendo João (normal).
```

---

## Critérios

- Implementação correta da classe `Fila`.
- Utilize POO e arquivos externos.
- Respeito à lógica **FIFO** e ao tratamento de prioridades.
- Boa organização do código e legibilidade.
- Tratamento de erros de entrada (ex.: comando inválido, formato incorreto).
