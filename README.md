# Atividade---George---Sistemas-Operacionais
1. Qual a diferença entre programa e processo?

R= Os programas são um conjunto de instruções detalhadas armazenadas em um arquivo e o processo é o programa em execução.

2. Quais são os estados de um processo e quando ocorrem as transições?

R= Os estados de um processo são:

  Novo: processo foi criado e está aguardando a alocação de recursos.
  Pronto: processo apto a ser executado e aguardando a CPU.
  Executando: processo está sendo executado na CPU.
  Bloqueado: processo aguardando algum evento externo.
  Finalizado: processo terminou sua execução e liberou os recursos alocados.

  Transições:
  Novo: Pronto (quando é admitido pelo sistema operacional).
  Pronto: Execução (quando o escalonador escolhe o processo).
  Execução: Pronto (quando é preemptado).
  Execução: Bloqueado (quando espera por E/S).
  Bloqueado: Pronto (quando o evento ocorre).
  Execução: Finalizado (quando termina).

3. O que contém um Process Control Block (PCB)?

R=  O PCB (Process Control Block) é uma estrutura de dados que o sistema operacional usa para controlar e identificar um processo. Dessa forma, ele contém:
    Identificação do processo (PID).
    Estado atual do processo (se está pronto, executando ou esperando).
    Contador de programa (PC).
    Conteúdo dos registradores da CPU.
    Informações de escalonamento (prioridade, tempo de CPU usado).
    Informações de gerenciamento de memória.
    Lista de recursos alocados.

4. O que acontece com os recursos de um processo quando ele termina?

R= Todos os recursos alocados (memória, arquivos abertos, dispositivos) são liberados pelo sistema operacional e ficam disponíveis para outros processos.

5. Qual a diferença entre fork() e exec() no UNIX?

R=  fork(): cria um novo processo, cópia do processo pai.
    exec(): substitui o código e contexto do processo atual por um novo programa.

6. Como funciona a hierarquia de processos em UNIX?

R=  Todo processo é criado a partir de outro (processo pai → processo filho).
    O processo init (ou systemd, nas distribuições modernas) é o ancestral de todos.
    Processos filhos herdam alguns atributos do pai.
    Quando o processo pai termina antes do processo filho, o filho é adotado pelo init.

7. Compare memória compartilhada e troca de mensagens (IPC).

R= Na memória compartilhada, processos acessam a mesma área de memória (de forma rápida, mas exigindo sincronização para evitar conflitos). Na troca de mensagens, processos enviam dados via sistema operacional (mais simples, porém mais lento).

8. Cite exemplos de chamadas de sistema usadas em IPC.

R=  Troca de mensagens: send(), recv(), msgget(), msgsnd(), msgrcv().
    Memória compartilhada: shmget(), shmat(), shmdt().
    Sinais: kill(), signal().
    Pipes: pipe(), mkfifo().

9. Por que é importante que o sistema operacional faça gerenciamento de processos?

R= É importante, pois o sistema operacional precisa controlar processos para dividir recursos, manter segurança e permitir que vários rodem ao mesmo tempo sem atrapalhar uns aos outros.

10. Explique a diferença entre processos independentes e processos cooperativos.

R= Os processos independentes não compartilham dados nem recursos com outros processos. Já os processos cooperativos compartilham dados e precisam se sincronizar.

11. O que é um processo zumbi em UNIX/Linux?

R= É um processo que já terminou sua execução, mas ainda mantém uma entrada na tabela de processos porque o processo pai não coletou seu status (via wait()).

12. Explique a diferença entre chamadas bloqueantes e não bloqueantes em IPC.

R= As chamadas bloqueantes fazem o processo esperar até a operação terminar. Já as não bloqueantes deixam o processo seguir, mesmo que a operação não tenha sido concluída.

13. Qual a diferença entre processo pesado (process) e thread (processo leve)?

R= O processo pesado (process) tem seu próprio espaço de endereçamento e recursos e, como o próprio nome diz, ele é mais pesado de criar e trocar contexto. Já a Thread (processo leve) compartilha memória e recursos do processo pai e é mais leve e rápida, mas exige maior cuidado com sincronização.

14. Por que sistemas operacionais multiprogramados precisam de troca de contexto (context switch)?

R= Os sistemas operacionais precisam de troca de contexto (context switch) para alternar entre processos em execução, permitindo compartilhamento justo da CPU, garantindo que todos os processos tenham chance de rodar e que a máquina seja usada de forma eficiente.

15. Cite vantagens e desvantagens da comunicação via memória compartilhada.

R= Vantagens: é rápida e boa para grandes volumes de dados.
   Desvantagens: exige sincronização cuidadosa, senão gera conflitos e erros de concorrência.
