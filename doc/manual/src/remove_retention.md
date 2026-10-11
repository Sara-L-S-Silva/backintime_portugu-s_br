# Remoção e retenção
<!--
SPDX-FileCopyrightText: © 2025 Christian BUHTZ <c.buhtz@posteo.jp>

SPDX-License-Identifier: GPL-2.0-or-later

This file is part of the program "Back In Time" which is released under GNU
General Public License v2 (GPLv2). See LICENSES directory or go to
<https://spdx.org/licenses/GPL-2.0-or-later.html>
-->
## Visão geral
Backups podem ser removidos ou retidos automaticamente com base em regras.
Essas regras permitem um gerenciamento detalhado do arquivo de backups,
reduzindo o uso de espaço de armazenamento. O processo é executado ao final
de cada execução de backup, mesmo que nenhum backup novo seja criado.

!!! note
    Esse recurso também era conhecido como _Auto-remove_ ou _Smart Remove_ em
    versões anteriores do _Back In Time_ (anteriores à 1.6.0).

![Aba do diálogo - Remoção e retenção](_images/tab_remove_retention.png)

Veja uma breve visão geral das regras disponíveis:
      
- **Manter o backup mais recente**: O último backup (ou o mais novo) será mantido.
- **Manter backups nomeados**: Todos os backups com um nome são excluídos de todas as
  regras e nunca são removidos. Esta é a única regra que não pode ser substituída
  por outras regras.
- **Remover backups com mais de `N` dias/semanas/anos**: Backups anteriores
  ao período especificado são removidos imediatamente.
- **Política de retenção**: Regras que determinam quais backups manter. Os
  demais serão removidos imediatamente.
    - **Manter todos os backups dos últimos `N` dias**
    - **Manter o último backup de cada dia/semana/mês dos últimos `N` dias/semanas/meses**
    - **Manter o último backup de cada ano, para todos os anos**
- **Remover o backup mais antigo se o espaço livre for inferior a `N` GiB/MiB**: Se o
  limite de espaço de armazenamento livre for atingido, os backups mais antigos serão
  removidos até que haja espaço de armazenamento suficiente novamente.
- **Remover o backup mais antigo se os inodes livres forem inferiores a `N` %**: Se o
  limite de inodes livres for atingido, os backups mais antigos serão
  removidos até que haja inodes suficientes novamente.

!!! warning
    Todas as regras são processadas de cima para baixo, conforme apresentadas na GUI ou
    neste manual. Regras posteriores **substituem** as anteriores e **não são
    limitadas** por elas. A única exceção é a primeira regra,
    *Manter backups nomeados*.

Nos exemplos abaixo:

- O <span style="color: #e655ec;"><strong>item em rosa é o backup atual</strong></span>.
- <strong>Os itens em preto são os backups existentes</strong>.
- <span style="color: #60a776;"><strong>Os itens em verde são backups identificados para retenção</strong></span>.
- <span style="color: #d23c48;"><strong>Os itens em vermelho são backups identificados para remoção</strong></span>.
- <span style="color: #6681a5;"><strong>Os itens em azul (às vezes <span style="color: #e655ec;">combinados com rosa</span>) na coluna final são os backups mantidos ao final</strong></span>.

## Detalhes das regras
### Manter os backups mais recentes
Os backups criados mais recentemente, ou seja, os mais novos, serão
mantidos e não serão excluídos por nenhuma das regras configuradas. Embora
essa opção apareça na interface gráfica, esse comportamento não pode ser alterado.

### Manter backups nomeados
Além do timestamp normalmente usado para identificar backups, é possível
associar um nome a eles. Nenhuma outra regra afeta esses backups nomeados.
Isso garante que eles não serão removidos. Consulte
[Janela principal](main_window.md) para obter mais detalhes sobre backups nomeados.

### Remover backups com mais de …

**Remover backups com mais de `N` anos**

- O cálculo é baseado em 12 meses.
- O mês atual é ignorado.
- _Exemplo_: Para backups com mais de dois anos, na data 2025-04-17, serão
  removidos os backups anteriores a (ou mais antigos que) 2023-04-01.
![Regra - Remover backups com mais de 2 anos](_images/rule_older_than_n_years.png)

**Remover backups com mais de `N` semanas**

- O cálculo é baseado em semanas do calendário, considerando segunda-feira como o primeiro dia da semana.
- A semana atual é ignorada.
- _Exemplo_: Para backups com mais de duas semanas, na sexta-feira 2025-08-29, serão removidos
  os backups anteriores a (ou mais antigos que) segunda-feira 2025-08-11.

![Regra - Remover backups com mais de 2 semanas](_images/rule_older_than_n_weeks.png)

**Remover backups com mais de `N` dias**

- O cálculo é baseado em dias completos, das 0:00 às 23:59.
- O dia atual é ignorado.
- _Exemplo_: Para backups com mais de 3 dias, na data 2025-01-10, serão removidos os backups
  anteriores a (ou mais antigos que) 2025-01-07.

![Regra - Remover backups com mais de 3 dias](_images/rule_older_than_n_days.png)

### Política de retenção
Os backups são mantidos se corresponderem a pelo menos uma das regras da
política de retenção. Todos os outros backups, não abrangidos pela política de
retenção, serão removidos.

Os valores especificados são tratados como um período, e não como uma contagem. Por exemplo,
imagine que se mantenha o último backup de cada mês dos últimos seis meses,
incluindo o mês atual. No entanto, somente quatro desses seis meses têm backups.
Nesse caso, apenas quatro backups serão mantidos. O período não é
estendido para trás para atingir um total de seis backups. Consulte as
regras abaixo para ver mais exemplos ilustrados.

**Manter todos os backups dos últimos `N` dias**

- O cálculo é baseado em dias completos, das 0:00 às 23:59.
- O dia atual está incluído.

_Exemplo_:

![Regra - Manter todos os backups dos últimos 2 dias](_images/rule_keep_all_for_n_days.png)

**Manter o último backup de cada dia dos últimos `N` dias**

- O cálculo é baseado em dias completos, das 0:00 às 23:59.
- O dia atual está incluído.

_Exemplo_:

![Regra - Manter o último backup de cada dia dos últimos 5 dias](_images/rule_keep_last_each_day_for_n_days.png)

**Manter o último backup de cada semana das últimas `N` semanas**

- O cálculo é baseado em semanas completas do calendário, começando na segunda-feira.
- A semana atual está incluída.

_Exemplo_:

![Regra - Manter o último backup de cada semana das últimas 4 semanas](_images/rule_keep_last_each_week_for_n_weeks.png)

**Manter o último backup de cada mês dos últimos `N` meses**

- O cálculo é baseado em meses completos do calendário.
- O mês atual está incluído.

_Exemplo_:

![Regra - Manter o último backup de cada mês dos últimos 4 meses](_images/rule_keep_last_each_month_for_n_months.png)

**Manter o último backup de cada ano, para todos os anos**

- O cálculo é baseado em anos do calendário.
- O ano atual está incluído.
- Embora essa opção apareça na interface gráfica, esse comportamento não pode ser
  alterado quando a _Política de retenção_ está ativada.

_Exemplo_:

![Regra - Manter o último backup de cada ano, para todos os anos](_images/rule_keep_last_each_year_for_all_years.png)

### Executar em background mode no remote host
O comando de remoção pode ser executado na máquina local ou em um remote host via
SSH. A segunda opção pode economizar tempo e recursos.

## Interações entre as regras e restrições mútuas
Todas as regras são aplicadas e executadas imediatamente, uma por uma, na ordem
em que são apresentadas na GUI e neste manual. Isso pode levar a interações
confusas entre as regras.

### Exemplo: três anos e todos os anos
Imagine estas duas regras:

1. Remover backups com mais de 3 anos.
2. Manter o último backup de cada ano, para todos os anos.

Vamos continuar supondo que houve vários backups por ano nos últimos
cinco anos.

A regra 2, isoladamente, resultaria em cinco backups mantidos, um para cada um dos
cinco anos existentes. Mas a regra 1 será executada antes. A regra 1 removerá
todos os backups de quatro e cinco anos atrás.
    
### Exemplo: seis meses, mas menos espaço de armazenamento
Imagine estas duas regras:

1. Manter o último backup de cada mês por 6 meses.
2. Remover os backups mais antigos se o espaço livre for inferior a 100 GiB.

A consequência da regra 1 é que seis backups serão mantidos, um para cada
mês. Imagine também que haja alguns outros backups mantidos pelas regras
anteriores. Isso consome tanto espaço de armazenamento que restam apenas 80 GiB
livres. Esse valor é inferior ao limite de 100 GiB configurado na regra 2. Por
isso, os dois backups mais antigos (dos meses cinco e seis) serão
removidos. Depois disso, haverá 105 GiB de espaço de armazenamento disponível novamente e a regra
será interrompida. Como resultado final, serão mantidos backups de quatro meses,
em vez dos seis meses configurados na regra 1.