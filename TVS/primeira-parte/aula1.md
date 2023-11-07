# Introdução à cadeira

## Avaliação

- **1ª Parte da cadeira:**
- SE1 - Sistemas Operativos (SO) Unix - **sai 22 setembro**
- SE2 - Isolamento por coordenação entre HW + SO

- Sessão de feeback #1
- Teste 1 - semana 8, talvez 9

- **2º Parte da cadeira:**
- SE3 - Serviços (Emuladores, Hipervisores)
- SE4 - Contentores

- Sessão de feedback #2
- Teste 2

## Virtual Machines

- Criam um ambiente de execução para um software

- VMWare, Virtual Box, Parallels, ... (Virtual Machine Monitors/Hipervisores)
  - Criam e gerem máquinas virtuais "de sistema"
- JVM (Java Virtual Machine), .NET Runtime, Node.js, ...
  - Ambiente Virtual de Execução - Virtual Execution Environment (VEE)
**ISA - Instruction Set Architecture**

|  | System | Process |
| --- | --- | --- |
| ISA = | VM -> VMWare, VirtualBox | Processo |
| ISA != | Emuladores | JVM, .NET Runtime, Node.js, ... |

Também com o mesmo ISA entre o System e o Process, encontramos os **contentores**.

## O que é um processo
>
>Reminder: Thread é um fio de execução

- O seu objetivo **nos anos 80** era criar uma entidade executiva para permitir correr várias coisas em simultâneo
- Hoje em dia queremos que o processo seja multi-threaded, logo **não são entidades executivas**.
- Processo é o nome que se dá a um programa em execução, este tem como característica ser **uma entidade de isolamento.**

- Uso de endereços virtuais para diferenciar mesmos valores em diferentes programas para serem mapeados para endereços físicos diferentes sem que haja conflito.

- O SO para cada programa em execução define:
  - Um espaço de endereçamento (gamas válidas de endereços virtuais; mapeamento para endereços físicos)
  - CPU Virtual para cada programa (Thread)
