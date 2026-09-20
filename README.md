<!--
SPDX-FileCopyrightText: © 2009 Back In Time Team <backintime-project@posteo.de> 

SPDX-License-Identifier: GPL-2.0-or-later 

Este arquivo faz parte do programa "Back In Time", que é distribuído sob a GNU 
General Public License v2 (GPLv2). Consulte o diretório LICENSES ou 
acesse <https://spdx.org/licenses/GPL-2.0-or-later.html> 
-->
# Back In Time

_Back In Time_ é um frontend gráfico confortável e altamente configurável para
backups incrementais usando [`rsync`](https://rsync.samba.org/), com uma
versão de linha de comando também disponível. Os arquivos modificados são
transferidos, enquanto os arquivos inalterados são vinculados ao novo diretório
usando o recurso de hard link do rsync, economizando espaço de armazenamento.
A restauração é simples por meio do gerenciador de arquivos, da linha de
comando ou do próprio _Back In Time_.

Ele é escrito em Python3 e está disponível para todas as principais
distribuições GNU/Linux como a ferramenta de linha de comando `backintime` e a
GUI `backintime-qt`. Os backups podem ser agendados e armazenados localmente
ou remotamente por meio de SSH.

Mais informações de contexto em [CONTRIBUTING](CONTRIBUTING.md) e
[HISTORY](HISTORY.md).

## Status de manutenção

O projeto está em desenvolvimento ativo desde que a [equipe atual](#the-team)
se juntou em meados de 2022, dando continuidade ao trabalho do mantenedor
anterior, Germar. O desenvolvimento é realizado voluntariamente no tempo
livre, portanto as coisas precisam ser priorizadas. Continue conosco, todos
nós ♥️ _Back In Time_. 😁

O foco atual está em corrigir
[problemas importantes](https://github.com/bit-team/backintime/issues?q=is%3Aissue+is%3Aopen+label%3AHigh)
em vez de implementar novos
[recursos](https://github.com/bit-team/backintime/labels/Feature).
Estabilizar a base de código e sua suíte de testes também é uma questão
importante. Leia o
[resumo da estratégia](CONTRIBUTING.md#strategy-outline) para obter mais detalhes.
Consulte [CONTRIBUTING](CONTRIBUTING.md) se tiver interesse no
desenvolvimento e dê uma olhada nas
[issues abertas](https://github.com/bit-team/backintime/issues), especialmente
naquelas marcadas como
[good first issues](https://github.com/bit-team/backintime/labels/GOOD%20FIRST%20ISSUE)
e [help wanted](https://github.com/bit-team/backintime/issues?q=is%3Aissue+is%3Aopen+label%3AHELP-WANTED).

## A equipe
Desde aproximadamente 2024, [@buhtz](https://buhtz.codeberg.page/), integrante
da terceira geração de mantenedores do projeto, tem sido o único mantenedor.
Ele cuida de todas as tarefas principais, desde a análise de código e
documentação até a resolução de issues e implementação de recursos. O trabalho
é realizado voluntariamente durante o tempo livre. O projeto continua se
beneficiando de uma comunidade ativa e engajada que fornece conselhos,
experiência e contribuições, garantindo que ele prospere e evolua.

O projeto foi [reativado em
2022](https://github.com/bit-team/backintime/issues/1232) e, em grande parte,
graças a Michael Büker ([@emtiu](https://github.com/emtiu)) e Jürgen
([@aryoda](https://github.com/aryoda)), que ajudaram a relançá-lo e a definir
sua direção. Consulte [HISTORY](HISTORY.md) para obter mais detalhes.

---

# Índice

- [Documentação](#documentation)
- [Contato e redes sociais](#contact--social)
- [Instalação](#installation)
- [Problemas conhecidos e soluções alternativas](#known-problems-and-workarounds)
- [Contribuindo e outras formas de apoiar o projeto](#contributing-and-other-ways-to-support-the-project)
- [Licenças](#licenses)

# Documentação

* [FAQ - Perguntas frequentes](FAQ.md)
* [Documentação para usuários finais (não totalmente atualizada)](https://backintime.readthedocs.org/) (not totally up-to-date)
* [Documentação do código-fonte para desenvolvedores](https://backintime-dev.readthedocs.org)
  (**Desativada** e não está atualizada. Abra uma issue se precisar utilizá-la.)

# Contato e redes sociais

 * **Lista de discussão**:
    
 * **Lista de e-mails**:
    [bit-dev@python.org](https://mail.python.org/mailman3/lists/bit-dev.python.org/)
    pode ser usada para **qualquer assunto**, pergunta ou ideia relacionada ao _Back In
    Time_. Apesar do nome, ela não é restrita apenas a assuntos de desenvolvimento.
* **Fediverse** no **Mastodon**: [@backintime@fosstodon.org](https://fosstodon.org/@backintime)
* **Bugs** e **solicitações de recursos**: [Seção issues](https://github.com/bit-team/backintime/issues)
* **E-mail**: [backintime-project@posteo.de](mailto:backintime-project@posteo.de)

# Instalação

_Back In Time_ está incluído em
[muitas distribuições GNU/Linux.](https://repology.org/project/backintime/badges).
Use os repositórios delas para instalá-lo. Se quiser contribuir ou usar a
versão mais recente de desenvolvimento do _Back In Time_, consulte a seção
[Build & Install](CONTRIBUTING.md#build--install) em
[`CONTRIBUTING.md`](CONTRIBUTING.md). As dependências também são descritas lá.

# Problemas conhecidos e soluções alternativas

Na versão estável mais recente:
- [Tratamento das permissões de arquivos e, portanto, possíveis backups não diferenciais](#file-permissions-handling-and-therefore-possible-non-differential-backups)

Mais problemas são descritos
[nesta seção da FAQ.](FAQ.md#problems-errors--solutions).

## Tratamento das permissões de arquivos e, portanto, possíveis backups não diferenciais

- Na versão 1.2.0, o tratamento das permissões de arquivos foi alterado.
- Nas versões <= 1.1.24 (até 2017), todas as permissões de arquivos eram definidas como
  `-rw-r--r--` no destino do backup.
- Nas versões >= 1.2.0 (desde 2019), o `rsync` é executado com a opção `--perms`,
  que instrui o `rsync` a preservar a permissão do arquivo de origem.

Portanto, os backups podem ser maiores e mais lentos, especialmente o primeiro
backup após a atualização para uma versão >= 1.2.0.

Se você não gostar do novo comportamento, pode usar Expert Options ->
Paste additional options to rsync para adicionar `--no-perms --no-group --no-owner`
a ele. Observe que as permissões exatas dos arquivos ainda podem ser encontradas
em `fileinfo.bz2` e também são consideradas ao restaurar arquivos.

# Contribuindo e outras formas de apoiar o projeto
Consulte o arquivo [CONTRIBUTING](CONTRIBUTING.md) para obter uma visão geral
do fluxo de trabalho e da estratégia do projeto.

*Apoie o mantenedor*: O projeto é mantido no tempo livre e sem compensação
financeira. Uma forma de apoiar o projeto é por meio de
[doações](https://codeberg.org/buhtz/about-me#donations)
ao mantenedor ([buhtz](https://buhtz.codeberg.page)) via
<a href="https://liberapay.com/buhtz">
<img src="https://codeberg.org/buhtz/about-me/raw/branch/main/liberapay.svg" width="24px" height="24px" />
Liberapay</a> e
<a href="https://ko-fi.com/buhtz">
<img src="https://codeberg.org/buhtz/about-me/raw/branch/main/kofi.png" width="24px" height="24px" />
Ko-fi</a>.
Observe que as doações são feitas pessoalmente ao mantenedor,
não ao Back In Time nem a qualquer outro
[project](https://codeberg.org/buhtz/about-me#projects) específico. Elas
apoiam o trabalho do mantenedor, incluindo o trabalho no _Back In Time_.

# Licenças
Tenha em mente que o código, a documentação e outros materiais
enviados ao projeto são considerados licenciados sob os mesmos termos (consulte
[LICENSES](LICENSES))) que o restante do trabalho. O projeto utiliza as
especificações do [REUSE Software](https://reuse.software) e
[SPDX](https://spdx.github.io/spdx-spec) para armazenar informações de licença
e direitos autorais. Consulte o
[status de compliance com o REUSE](https://api.reuse.software/info/github.com/bit-team/backintime).

---
<sub>Setembro de 2026</sub>