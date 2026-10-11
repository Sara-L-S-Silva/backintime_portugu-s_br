<!--

SPDX-FileCopyrightText: © 2024 Michael Büker

SPDX-License-Identifier: GPL-2.0-or-later

Este arquivo faz parte do programa "Back In Time", que é distribuído sob a GNU

General Public License v2 (GPLv2). Consulte o diretório LICENSES ou acesse

<https://spdx.org/licenses/GPL-2.0-or-later.html>

-->

# Olhando para o passado do **Back In Time**

**Por Michael Büker, 2024**

O desenvolvimento do **Back In Time** foi inspirado pelo [FlyBack](https://en.wikipedia.org/wiki/FlyBack).

A história do projeto **Back In Time**, que no momento em que este texto foi escrito já se estende por quase 16 anos, é melhor compreendida em quatro períodos:

1. A ****Primeira Era****, de 2008 a 2012, versões 0.5 a ~1.0.12

2. A ****Segunda Era****, de 2012 a 2019, versões ~1.0.14 a 1.2

3. Uma ****Era das Trevas****, de 2019 a 2022, versões 1.2.0 a 1.3.2

4. A ****Terceira Era****, desde 2022, a partir da versão 1.3.3

Esses períodos correspondem aproximadamente a quem estava mantendo e desenvolvendo o *Back In Time*. Mudanças técnicas e organizacionais importantes aconteceram em vários momentos entre eles. Para obter detalhes, consulte [CHANGES](CHANGES). Para ter uma visão do futuro, consulte o [Strategy Outline](CONTRIBUTING.md#strategy-outline).

# A Primeira Era: 0.5 a ~1.0.12 (2008–2012)

## Manutenção

**Back In Time** foi criado por ****Oprea Dan**** e publicado pela primeira vez em um blog privado no final de 2008 ([link do Wayback](https://web.archive.org/web/20081014041759/http://www.le-web.org/2008/10/03/back-in-time-version-05/)).

Pouco depois, o desenvolvimento colaborativo começou no Launchpad. Em algum momento por volta de 2010, o desenvolvimento e a publicação parecem ter sido transferidos inteiramente para o Launchpad, com o blog privado sendo descontinuado.

## Funcionalidade principal

Inicialmente, **Back In Time** usava `diff` para comparar o backup mais recente com a origem, a fim de verificar se um novo backup era necessário. Se a resposta fosse sim, ele usava `cp` para criar um novo backup.

Isso mudou na versão 0.9.2, no início de 2009, quando `diff` foi substituído por `rsync` para a comparação. A cópia ainda era feita por `cp`, aparentemente sem tratamento especial de permissões.

Isso mudou quando, pouco depois, a versão 0.9.24 introduziu `fileinfo.bz2`, que armazena informações de permissões de todos os arquivos em um backup. Introduzido para permitir salvar backups em sistemas de arquivos que não reconhecem permissões Unix, como NTFS, `fileinfo.bz2` é consultado ao restaurar um arquivo para recriar sua propriedade e suas permissões originais.

## GUI

Inicialmente, **Back In Time** possuía apenas uma GUI do GNOME.

A versão 0.9, do início de 2009, separou o backend (`backintime-common`) da GUI, permitindo diferentes frontends. Ao longo de 2009, terminando aproximadamente com a versão 0.9.24, dois frontends separados foram concluídos:

`backintime-gnome` e `backintime-kde4`.

# A Segunda Era: ~1.0.14 a 1.2 (2012–2019)

## Manutenção

Por volta de 2012, ****Germar Reitze**** assumiu a publicação, manutenção e desenvolvimento posterior de Oprea Dan.

No início de 2016, começando com a versão 1.1.10, o desenvolvimento e a publicação foramtransferidos para o Microsoft GitHub, deixando o projeto no Launchpad praticamente abandonado (exceto pelo gerenciamento de traduções e pela publicação do PPA).

## Funcionalidade principal

O desenvolvimento durante a Segunda Era concentrou-se principalmente nas capacidades de backup remoto. No final de 2012, a versão 1.0.12 introduziu locais de backup remotos habilitados por`ssh`.

No início de 2013, a versão 1.0.22 introduziu um "full rsync mode" opcional. Isso substituiu `cp` por `rsync` em todas as operações, incluindo a replicação completa das permissões.

No final de 2013, a versão 1.0.26 introduziu locais de backup criptografados habilitados por `encfs`.

## GUI

No início de 2015, a versão 1.1.0 eliminou os frontends separados `backintime-gnome` e `backintime-kde4` e introduziu `backintime-qt4` como o único frontend.

# A Era das Trevas: 1.2.0 a 1.3.2 (2019–2022)

Em 2019, a versão 1.2.0 foi lançada. Foi a primeira versão desde a versão 1.1.24, no final de 2017, e continha muitas correções de bugs acumuladas durante os 1,5 anos anteriores.

A versão 1.2.0 introduziu uma mudança fundamental: ****"tornar o full-rsync mode o padrão e remover o outro modo"****. Isso significava que os arquivos seriam sempre transferidos por `rsync` em vez de `cp`. Especificamente, `rsync` foi instruído a preservar todas as informações de propriedade e permissões ao transferir os arquivos para o backup (**além** das informações armazenadas em `fileinfo.bz2`).

Isso causou o bug [#988](https://github.com/bit-team/backintime/issues/988), que quebrou a funcionalidade principal do **Back In Time** para qualquer backup criado com

uma versão <1.2.0 (a menos que o "full rsync mode" tivesse sido habilitado): muitos arquivos inalterados deixaram de ser hardlinked durante a transferência e passaram a ser copiados desnecessariamente. Isso levou a tempos de backup muito longos e alto uso de disco. Um bug relacionado, com um impacto um pouco menor, é o [#994](https://github.com/bit-team/backintime/issues/994).

Da forma como esses bugs são atualmente compreendidos, a razão subjacente do problema é a diferença de propriedade/permissões entre os arquivos na origem e no disco de backup. Como múltiplos hardlinks para o mesmo arquivo são, por definição, idênticos, eles não podem possuir permissões diferentes. `rsync` não consegue lidar corretamente com esse caso quando um novo backup é criado, fazendo com que os arquivos em questão sejam copiados desnecessariamente. Com muitos usuários reclamando e compartilhando soluções alternativas no Microsoft GitHub, o desenvolvimento logo chegou a uma paralisação. Alguns bugs foram corrigidos com a versão

1.3.0 em 2021, mas [#988](https://github.com/bit-team/backintime/issues/988) e

[#994](https://github.com/bit-team/backintime/issues/994) permaneceram.

# A Terceira Era: desde a 1.3.3 (desde 2022)

No início de 2022, uma discussão épica sobre o estado do projeto surgiu em

[#1232](https://github.com/bit-team/backintime/issues/1232). Muitos usuários declararam seu amor pelo **Back In Time**, e alguns estavam dispostos a assumir a responsabilidade e reiniciar o desenvolvimento. Com a ajuda e a permissão de Germar Reitze,

**Christian Buhtz**, ****Jürgen Altfeld**** e ****Michael Büker**** formaram uma nova equipe principal. A equipe primeiro analisou e classificou mais de 200 issues abertas que haviam se acumulado desde 2019.

A primeira versão lançada pela nova equipe foi a versão 1.3.3, no início de 2023. O trabalho inicial concentrou-se em garantir compatibilidade com rsync 3.2.4, corrigir problemas com keyring nas operações SSH, a funcionalidade da system tray tanto no X11 quanto no Wayland, além de testes, estilo de código e outras modernizações para alinhar **Back In Time** às práticas atuais de Python.

## Funcionalidade principal

O trabalho para corrigir [#988](https://github.com/bit-team/backintime/issues/988) e

[#994](https://github.com/bit-team/backintime/issues/994) ainda está em andamento no momento em que este texto foi escrito. Esses bugs são amplamente compreendidos agora, mas qualquer possível correção poderia ter consequências graves para os backups existentes, que ainda não foram testados de maneira abrangente. Como o EncFS apresenta problemas de segurança conhecidos e não é mantido ativamente, **Back In Time** está se preparando para descontinuá-lo em um futuro próximo ([#1734](https://github.com/bit-team/backintime/issues/1734)).

## GUI

A GUI está prevista para passar por uma reformulação e refatoração do código, pois se tornou complexa e convoluta ao longo dos anos. Um recurso frequentemente solicitado é uma interface de usuário de terminal (TUI), ou uma melhoria da interface de linha de comando (CLI) existente, conforme discutido em [#254](https://github.com/bit-team/backintime/issues/254). A proposta de um frontend web foi rejeitada ([#209](https://github.com/bit-team/backintime/issues/209)), mas projetos separados que ofereçam um frontend web seriam apoiados.
