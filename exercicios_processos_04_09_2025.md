# Exercícios Teóricos – Processos

## 1. Qual a diferença entre programa e processo?
- **Programa**: é um conjunto de instruções armazenado em disco (arquivo estático).
- **Processo**: é um programa em execução, ou seja, possui contexto, recursos alocados e estado dinâmico.

---

## 2. Quais são os estados de um processo e quando ocorrem as transições?
- **Novo**: o processo está sendo criado.
- **Pronto (Ready)**: preparado para executar, aguardando CPU.
- **Execução (Running)**: em uso da CPU.
- **Bloqueado (Waiting)**: aguardando evento ou recurso externo.
- **Finalizado (Terminated)**: execução concluída.

Transições ocorrem, por exemplo:
- De **Pronto → Execução**: escalonador escolhe o processo.
- De **Execução → Pronto**: preempção (troca de contexto).
- De **Execução → Bloqueado**: espera por I/O.
- De **Bloqueado → Pronto**: evento concluído.

---

## 3. O que contém um Process Control Block (PCB)?
- Identificação do processo (PID).
- Estado do processo.
- Contador de programa.
- Registradores da CPU.
- Informações de escalonamento (prioridade, fila).
- Informações de memória (tabelas de páginas/segmentos).
- Informações de I/O (arquivos abertos, dispositivos).

---

## 4. O que acontece com os recursos de um processo quando ele termina?
- São liberados pelo sistema operacional:
  - Memória.
  - Arquivos abertos.
  - Dispositivos de I/O.
  - Entradas na tabela de processos.

---

## 5. Qual a diferença entre fork() e exec() no UNIX?
- **fork()**: cria um novo processo (filho) duplicando o processo pai.
- **exec()**: substitui o conteúdo do processo atual por um novo programa.

---

## 6. Como funciona a hierarquia de processos em UNIX?
- Existe um processo raiz (**init ou systemd**) que gera outros processos.
- Cada processo pode criar processos filhos com **fork()**.
- Essa relação forma uma **árvore de processos**.

---

## 7. Compare memória compartilhada e troca de mensagens (IPC).
- **Memória compartilhada**: processos acessam a mesma região de memória.  
  - Mais rápida, mas requer mecanismos de sincronização.
- **Troca de mensagens**: comunicação por envio/recebimento de mensagens.  
  - Mais simples de implementar, porém mais lenta.

---

## 8. Cite exemplos de chamadas de sistema usadas em IPC.
- `pipe()`
- `shmget()`, `shmat()`, `shmdt()`
- `msgget()`, `msgsnd()`, `msgrcv()`
- `socket()`, `send()`, `recv()`

---

## 9. Por que é importante que o sistema operacional faça gerenciamento de processos?
- Para garantir **uso eficiente da CPU e memória**.
- Evitar **deadlocks e conflitos de recursos**.
- Garantir **segurança e isolamento** entre processos.
- Oferecer **desempenho justo** entre múltiplos usuários e programas.

---

## 10. Explique a diferença entre processos independentes e processos cooperativos.
- **Independentes**: não interagem com outros processos, resultado não depende de terceiros.
- **Cooperativos**: interagem e compartilham dados, exigindo sincronização.

---

## 11. O que é um processo zumbi em UNIX/Linux?
- Processo que já terminou a execução, mas cujo **PCB ainda não foi removido** porque o pai não fez o `wait()` para coletar o status.

---

## 12. Explique a diferença entre chamadas bloqueantes e não bloqueantes em IPC.
- **Bloqueantes**: o processo fica em espera até a operação de comunicação terminar.
- **Não bloqueantes**: a operação retorna imediatamente, permitindo que o processo continue.

---

## 13. Qual a diferença entre processo pesado (process) e thread (processo leve)?
- **Processo**: possui espaço de memória e recursos independentes, mais custoso na criação e comunicação.
- **Thread**: compartilha memória e recursos do processo, mais leve e rápido para criar e trocar contexto.

---

## 14. Por que sistemas operacionais multiprogramados precisam de troca de contexto (context switch)?
- Para alternar entre processos que compartilham a CPU.
- Garante uso eficiente do processador.
- Permite execução concorrente e justa entre processos.

---

## 15. Cite vantagens e desvantagens da comunicação via memória compartilhada.
**Vantagens:**
- Mais rápida (não há cópia de mensagens).
- Útil para grandes volumes de dados.

**Desvantagens:**
- Necessita sincronização (semafóros, mutex).
- Maior risco de condições de corrida.
- Mais complexa de programar corretamente.

---
