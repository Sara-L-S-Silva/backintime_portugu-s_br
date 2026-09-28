<!--

SPDX-FileCopyrightText: © 2009 Back In Time Team

SPDX-License-Identifier: GPL-2.0-or-later

Este arquivo faz parte do programa "Back In Time", que é distribuído sob a
Licença Pública Geral GNU v2 (GPLv2). Consulte o diretório LICENSES ou acesse
<https://spdx.org/licenses/GPL-2.0-or-later.html>

-->

**# Como contribuir para** *\_Back In Time\_*

😊 **\*\*Obrigado por reservar um tempo para contribuir.\*\*** 😊

🟢 **\*\*As contribuições podem ser muito mais do que código.\*\*** 🟢

A equipe de manutenção aceita todos os tipos de contribuição. Nenhuma contribuição será rejeitada exclusivamente por não atender aos nossos padrões de qualidade, diretrizes ou regras. Toda contribuição é revisada e, se necessário, aprimorada em colaboração com a equipe de manutenção. Novos contribuidores que precisem de ajuda ou tenham menos experiência são muito bem-vindos e receberão orientação da equipe de manutenção quando solicitado.

Há muitas formas de contribuir além de programar:

- [traduzindo o projeto](https://github.com/bit-team/backintime/issues/1915),
  realizando testes manuais, analisando e reproduzindo
  [bugs](https://github.com/bit-team/backintime/issues), revisando e testando
  [pull requests](https://github.com/bit-team/backintime/pulls),
  fornecendo feedback sobre novos recursos, projetando um
  [logotipo para a aplicação](https://github.com/bit-team/backintime/issues/1961), ou
  revisando a documentação e sugerindo melhorias.

🚀 Toda contribuição ajuda o projeto a crescer! 🚀

> [!TIP]
>
> Não se esqueça de se apresentar se você é novo no projeto. Além disso, leia
> este documento atentamente.

**# Índice**

<!-- TOC start -->

- [Antes de começar](#antes-de-começar)
- [Boas práticas e recomendações](#boas-práticas-e-recomendações)
- [Recursos e leituras adicionais](#recursos-e-leituras-adicionais)
- [Compilar e instalar](#compilar-e-instalar)
  - [Dependências](#dependências)
  - [Compilar e instalar usando o sistema `make`
    (recomendado)](#compilar-e-instalar-usando-o-sistema-make-recomendado)
- [Testes](#testes)
  - [SSH](#ssh)
- [O que acontece depois que você abre um Pull Request (PR)?](#o-que-acontece-depois-que-você-abre-um-pull-request-pr)
- [Instruções sobre tradução](#instruções-sobre-tradução)
  - [Terminologia](#terminologia)
  - [Recomendações gerais para desenvolvedores](#recomendações-gerais-para-desenvolvedores)
  - [Considere idiomas da direita para a esquerda (RTL) e bidirecionais (BIDI)](#considere-idiomas-da-direita-para-a-esquerda-rtl-e-bidirecionais-bidi)
  - [Esteja atento aos indicadores de atalhos e possíveis duplicidades](#esteja-atento-aos-indicadores-de-atalhos-e-possíveis-duplicidades)
  - [Respeite o trabalho de outros tradutores](#respeite-o-trabalho-de-outros-tradutores)
- [Visão geral da estratégia](#visão-geral-da-estratégia)
- [Licenciamento do material contribuído](#licenciamento-do-material-contribuído)
- [Guia técnico rápido](#guia-técnico-rápido)

<!-- TOC end -->

**# Antes de começar**

- **\*\*Leia este documento atentamente.\*\***

- Lembre-se de que este projeto é mantido por voluntários em seu tempo livre –
  seres humanos como você.

- [Você deve ser usuário deste software](FAQ.md#can-i-contribute-without-using-the-software).

- [Apresente-se](FAQ.md#why-do-i-need-to-introduce-myself). Uma apresentação ajudará a distinguir você de contribuições geradas por IA. Caso contrário, há um grande risco de seu PR ser encerrado.

- Assuma a responsabilidade pela sua contribuição. A [política de IA generativa](https://developer.joomla.org/generative-ai-policy.html) do projeto *\_Joomla\_* pode oferecer informações mais detalhadas sobre isso.

- Consulte as [entradas da FAQ sobre como contribuir para o projeto](FAQ.md#project--contributing--more).

- E, finalmente: não deixe de ler este documento atentamente!

**# Boas práticas e recomendações**

Se possível, considere as seguintes boas práticas. Isso reduzirá a carga de trabalho dos mantenedores e aumentará as chances de seu pull request ser aceito.

- Siga a [PEP 8](https://peps.python.org/pep-0008/) como guia mínimo de estilo
  para código Python.

- Sobre strings:

  - Prefira *\_aspas simples\_* (por exemplo, `'Hello World'`) em vez de *\_aspas duplas\_*
    (por exemplo, `"Hello World"`). As exceções são casos em que há aspas simples dentro da
    string (por exemplo, `"Can't unmount"`).

  - Coloque strings traduzíveis desta forma: ` _('Translate me')`. Consulte mais
    detalhes em nossa
    [documentação de localização](doc/maintain/2_localization.md#instructions-for-the-translation-process).

- Para docstrings, siga o [Google Style Guide](https://sphinxcontrib-napoleon.readthedocs.org/en/latest/example_google.html)
  (consulte nosso próprio [HOWTO sobre geração de documentação](doc/maintain/1_doc_howto.md)).

- Evite usar formatadores automáticos como `black`, mas mencione o uso deles ao abrir um pull request.

- Execute os testes unitários antes de abrir um pull request. Consulte [Testes](#testes)
  para mais detalhes.

- Tente criar novos testes unitários quando apropriado. Use o estilo do `unittest` regular do Python
  em vez de `pytest`. Se você conhece a diferença, tente seguir a *\_escola Clássica (também chamada Detroit)\_* em vez da *\_escola London (também chamada mockista)\_*.

- Consulte as recomendações sobre [como lidar com strings traduzíveis](doc/maintain/2_localization.md#instructions-for-the-translation-process).

**# Recursos e leituras adicionais**

- [Lista de e-mails *\_bit-dev\_*](https://mail.python.org/mailman3/lists/bit-dev.python.org/)

<!-- - [Documentação do código-fonte para desenvolvedores](https://backintime-dev.readthedocs.org) Desatualizada. Não há necessidade real. Sem acesso à conta do RTD, ela pertence ao Germar. -->

- [As traduções](https://translate.codeberg.org/engage/backintime) são feitas em uma plataforma separada.

- [HowTos e manutenção](doc/maintain/README.md)

- [Entradas da FAQ sobre como contribuir para o projeto](FAQ.md#project--contributing--more).

- Leituras adicionais

   - [contribution-guide.org](https://www.contribution-guide.org)

   - [Como enviar uma contribuição (opensource.guide)](https://opensource.guide/how-to-contribute/#how-to-submit-a-contribution)

   - [mozillascience.github.io/working-open-workshop/contributing](https://mozillascience.github.io/working-open-workshop/contributing)

**# Compilar e instalar**

Esta seção descreve como compilar e instalar *\_Back In Time\_* como preparação para suas próprias contribuições. Presume-se que você tenha executado `git clone` neste repositório primeiro.

**## Dependências**

As dependências a seguir são baseadas no *\_Debian GNU/Linux\_*. [Abra uma Issue](https://github.com/bit-team/backintime/issues/new/choose) se algo estiver faltando. Se você usa outra distribuição GNU/Linux, instale os pacotes correspondentes. Mesmo que alguns pacotes estejam disponíveis no PyPi, use os pacotes fornecidos pelo repositório oficial da sua distribuição GNU/Linux.

| Dependência | CLI | GUI* | Compilação* | Opcional | Observações |
|:-|:-:|:-:|:-:|:-:|:-|
| `python3` (>=3.13) |🗹|||| |
| `rsync` |🗹|||| |
| `cron-daemon` |🗹||||
| `openssh-client` |🗹||||
| `sshfs` |🗹||||
| `python3-keyring` |🗹||||
| `python3-dbus` |🗹||||
| `python3-packaging` |🗹||||
| `gocryptfs` |🗹||||
| `x11-utils` | |🗹|| |
| `python3-pyqt6` | |🗹|| |Não use a versão PyPi via pip |
| `python3-dbus.mainloop.pyqt6` | |🗹|| |Não disponível via PyPi pip |
| `python3-pyqt6.qtsvg` | |🗹||| Suporte a Qt SVG para renderização da GUI |
| `pkexec` | |🗹||| Auxiliar de elevação de privilégios do Polkit |
| `bash` | |🗹||| Usado pelo script inicializador do modo root qt/backintime-qt_polkit |
| `polkit` | |🗹||| Estrutura de autorização para gerenciamento de privilégios |
| `qt6-translations-l10n` | |🗹||| |
| `qtwayland6` | |🗹||| Necessário se o Wayland for usado em vez do X11 (alternativa qt6-wayland) |
| `python3-secretstorage`<br>ou `python3-keyring-kwallet`<br>ou `python3-gnomekeyring` ||🗹||🗹|Armazenamento de chaves SSH|
| `kompare`<br> ou `meld` ||🗹||🗹|comparação semelhante a diff dos backups|
| `build-essential`|||🗹|| |
| `gzip`|||🗹|| |
| `gettext`|||🗹|| |
| `python3-pyfakefs` (>=5.7)|||🗹|| |
| `asciidoctor`|||🗹|| |
| `pylint` (>=4.0.0)|||🗹|🗹| Suíte de testes |
| `flake8`|||🗹|🗹| Suíte de testes |
| `ruff` (>=0.16.0)|||🗹|🗹| Suíte de testes |
| `codespell`|||🗹|🗹| Suíte de testes |
| `reuse` (>=4.0.0)|||🗹|🗹| Suíte de testes |
| `mkdocs`|||🗹|🗹| Manual do usuário em HTML|
| `mkdocs-material`|||🗹|🗹| |
| `pandoc`|||🗹|🗹| Converter o changelog para HTML|

\* *\_As camadas GUI e Build sempre dependem das dependências da CLI.\_*

**## Compilar e instalar usando o sistema `make` (recomendado)**

> [!IMPORTANT]
>
> Instale as [Dependências](#dependências) antes de compilar e instalar.

Lembre-se de que *\_Back In Time\_* é composto por dois pacotes, que devem ser compilados e instalados separadamente.

* Ferramenta de linha de comando

   1. `cd common`
   2. `./configure && make`
   3. Execute os testes unitários usando `python -m unittest` ou `pytest`.
   4. `sudo make install`

* GUI Qt

   1. `cd qt`
   2. `./configure && make`
   3. Execute os testes unitários usando `python -m unittest` ou `pytest`.
   4. `sudo make install`

Você pode usar argumentos opcionais para `./configure` para criar um Makefile.

Consulte `common/configure --help` e `qt/configure --help` para obter detalhes.

**# Testes**

> [!IMPORTANT]
>
> Lembre-se de testar *\_Back In Time\_* **\*\*manualmente\*\*** e não depender somente da suíte de testes automática. Consulte a seção
> [Testes manuais](doc/maintain/BiT_release_process.md#manual-testing---recommendations)
> sobre recomendações para realizar esses testes.

Depois de [compilar e instalar](#compilar-e-instalar), execute a suíte de testes. Sinta-se à vontade para usar o próprio módulo `unittest` do Python ou `pytest` como executor de testes.

Como *\_Back In Time\_* é composto por dois componentes, `common` e `qt`, os testes são separados de acordo com eles.

    $ cd common
    $ pytest

Ou

    $ cd qt
    $ pytest

> [!IMPORTANT]
>
> Mesmo que `pytest` seja usado como executor de testes, não escreva testes no estilo `pytest`. Mantenha o bom e antigo estilo `unittest`. Essa é uma regra do projeto, levando em conta a manutenibilidade.

**## SSH**

Alguns testes exigem um servidor SSH disponível. Esses testes são ignorados se nenhum servidor SSH estiver disponível. O objetivo é entrar no servidor SSH do seu computador local usando `ssh localhost` sem uma senha:

- Gere um par de chaves RSA executando `ssh-keygen`. Use o nome de arquivo padrão e não use uma senha para a chave.

- Transfira a chave pública para o servidor executando `ssh-copy-id`.

- Faça a instância `ssh` ser executada.

- A porta `22` (padrão do SSH) deve estar disponível.

- *\_Autorize\_* a chave com `$ ssh localhost` e insira a senha da sua conta de usuário.

Para testar a conexão, basta executar `ssh localhost` e você deverá ver um shell SSH **\*\*sem\*\*** que uma senha seja solicitada.

Para obter instruções detalhadas de configuração, consulte as
[instruções sobre como configurar o openssh para testes unitários](doc/maintain/3_How_to_set_up_openssh_server_for_ssh_unit_tests.md).

**# O que acontece depois que você abre um Pull Request (PR)?**

Em resumo:

1. A equipe de manutenção revisará seu PR em dias ou semanas.

2. Modificações poderão ser solicitadas e o PR eventualmente será aprovado.

3. Um de dois rótulos será adicionado ao PR:

   - [PR: Merge after creative-break](https://github.com/bit-team/backintime/labels/PR%3A%20Merge%20after%20creative-break):

     Fazer o merge, mas com um atraso mínimo de uma semana para permitir que outros mantenedores revisem.

   - [PR: Waiting for review](https://github.com/bit-team/backintime/labels/PR%3A%20Waiting%20for%20review):

     Aguardar até obter uma segunda aprovação de outro mantenedor.

Os membros da equipe de manutenção são prontamente notificados sobre sua solicitação. Um deles responderá dentro de dias ou semanas. Observe que todos os membros da equipe realizam suas funções voluntariamente, em seu limitado tempo livre.

Leia atentamente as respostas dos mantenedores, responda às perguntas deles e tente seguir suas instruções. Não hesite em pedir esclarecimentos se necessário. Pelo menos um mantenedor revisará e, por fim, aprovará seu pull request.

Dependendo do assunto ou impacto do PR, o mantenedor poderá decidir que é necessária a aprovação de um segundo mantenedor. Isso pode resultar em tempo adicional de espera. Tenha paciência. Nesses casos, o PR receberá o rótulo

[PR: Waiting for review](https://github.com/bit-team/backintime/labels/PR%3A%20Waiting%20for%20review).

Se uma segunda aprovação não for necessária, o PR receberá o rótulo

[PR: Merge after creative-break](https://github.com/bit-team/backintime/labels/PR%3A%20Merge%20after%20creative-break)

e permanecerá aberto por no mínimo uma semana. Essa regra permite que todos os mantenedores tenham a oportunidade de revisar e, potencialmente, vetar o pull request.



**# Instruções sobre tradução**

**## Terminologia**

- Os tradutores, como falantes nativos, são os responsáveis pela manutenção da tradução em seu idioma e têm a decisão final. Todos os pontos a seguir são recomendações fortes, mas não são regras rígidas. Os responsáveis pelo idioma são livres para desconsiderá-las por boas razões.

- "Directory" ou "Folder"? Preferimos "Directory". Em nossa opinião, é um termo técnico claramente definido e mais preciso para descrever um elemento do sistema de arquivos.

- Traduzir "Back In Time"? Esse é o nome da aplicação. Ele não deve ser traduzido.

- O grupo de usuários-alvo do Back In Time é composto por usuários finais sem conhecimento técnico. Escreva strings e mensagens da GUI de acordo com isso, evitando terminologia técnica ou excessivamente especializada.

- Alguns pontos das seguintes [Recomendações gerais para desenvolvedores](#recomendações-gerais-para-desenvolvedores) também são relevantes para tradutores.

**## Recomendações gerais para desenvolvedores**

Os pontos a seguir tratam da criação de strings do código-fonte que possam ser traduzidas.

- Tenha em mente que alguns de nossos tradutores não têm experiência em programação Python. Eles podem não conhecer os detalhes internos do GNU gettext e outros aspectos técnicos. Eles veem apenas a string traduzível na interface web de nossa [plataforma de tradução](https://translate.codeberg.org/engage/backintime).

- Evite caracteres de escape nas strings.

- Dê aos tradutores contexto suficiente fornecendo nomes significativos para placeholders.

- Evite se dirigir aos usuários como pessoas usando "you". Prefira frases neutras.

- Não use letras maiúsculas de forma excessiva (por exemplo, `WARNING`) nem ponto de exclamação (`!`).

- Forneça uma captura de tela ao introduzir novas strings traduzíveis ou modificá-las. A imagem será usada na interface web de tradução para fornecer mais contexto aos tradutores.

- [Considere idiomas da direita para a esquerda (RTL) e bidirecionais (BIDI)](#considere-idiomas-da-direita-para-a-esquerda-rtl-e-bidirecionais-bidi).

- [Esteja atento aos indicadores de atalhos e possíveis duplicidades](#esteja-atento-aos-indicadores-de-atalhos-e-possíveis-duplicidades).

- [Respeite o trabalho de outros tradutores](#respeite-o-trabalho-de-outros-tradutores).

```python
# Evite caracteres de escape para delimitadores de strings
problematic = _('Hello \'World\'')
correct = _("Hello 'World'")

# Evite caracteres de escape, como quebras de linha
problematic = _('One\nTwo')
correct = _('One') + '\n' + _('Two')  # <- Separar em várias strings não é um
                                      #    problema, pois o tradutor
                                      #    terá uma captura de tela.

# Forneça nomes significativos para placeholders
problematic = _('Can not delete {var}.')
correct = _('Can not delete {backup_path}.')

# Evite se dirigir à pessoa usando "you"
problematic = _('Do you really want to delete this backup?')
correct = _('Is it really intended to delete this backup?')
```

**## Considere idiomas da direita para a esquerda (RTL) e bidirecionais (BIDI)**

Em resumo: sempre inclua sinais de pontuação (por exemplo, dois-pontos) nas strings a serem traduzidas.

Idiomas como árabe ou hebraico são lidos da direita para a esquerda (RTL). Para ser mais preciso, eles podem ter direções de leitura mistas (BIDI). A biblioteca de GUI usada pelo *\_Back In Time\_* leva isso em consideração ao organizar elementos em uma janela. Por exemplo, um widget de entrada de texto fica à esquerda de um widget de rótulo. Essa inversão de ordem é o motivo pelo qual os sinais de pontuação (por exemplo, dois-pontos) na string de um widget de rótulo também precisam mudar de direção. Essa tarefa só pode ser realizada pelo próprio tradutor, razão pela qual os sinais de pontuação precisam ser incluídos na string a ser traduzida.

**## Esteja atento aos indicadores de atalhos e possíveis duplicidades**

Em resumo:

1. Use o caractere `&` para indicar a letra usada para acessar um elemento da GUI por meio de um atalho de teclado.

2. Tenha cuidado para não criar conflitos usando a mesma letra várias vezes no mesmo contexto da GUI.

A GUI do *\_Back In Time\_* pode ser controlada por atalhos de teclado. Na versão em inglês, por exemplo, o menu *\_Back In Time\_* na janela principal pode ser aberto com `Alt+T`, *\_Backup\_* com `Alt+B` ou *\_Help\_* com `Alt+H`. As letras do teclado a serem usadas são indicadas na GUI com uma letra sublinhada. A string original no código-fonte usa o caractere `&` antes de uma letra para indicar o atalho e produzir esse sublinhado. Os exemplos acima usam as strings `Back In &Time`, `&Backup` e `&Help`. Isso ilustra por que não é apropriado usar sempre a primeira letra para os atalhos. Nesse exemplo, `&Back In Time` e `&Backup` usariam a mesma letra.

Traduzir `&Backup` e `&Help` para o turco resulta em `&Yedek` e `Y&ardım`, e usar somente a primeira letra criaria conflitos novamente.

Por isso, o tradutor precisa decidir qual letra usar.

**## Respeite o trabalho de outros tradutores**

Às vezes, é uma questão de gosto ou hábito a forma de traduzir algo. As pessoas são diferentes e, portanto, suas traduções também são diferentes. Ao modificar uma tradução existente, consulte as seções *\_Comments\_* e *\_History\_* dessa string em nossa plataforma de tradução. Pode haver outro tradutor que tenha uma boa razão para essa tradução. Não desperdice o trabalho de outras pessoas sem uma boa razão. Use também os *\_Comments\_* para documentar seus próprios motivos caso espere discussões ou conflitos.

A tradução para alguns idiomas específicos (por exemplo,
[alemão](https://translate.codeberg.org/projects/backintime/common/de/))
tem regras que todo tradutor deve seguir. Essas regras podem ser encontradas em uma caixa colorida no topo da plataforma de tradução. Abra uma issue se achar que elas devem ser modificadas.

**# Visão geral da estratégia**

Esta é uma visão geral ampla das tarefas ou etapas para aprimorar *\_Back In Time\_* como software e como projeto. O cronograma não é fixo, nem a ordem de prioridade.

- [Roteiro preliminar](#roteiro-preliminar)
- [Sistema de plugins](#sistema-de-plugins)
- [Empacotamento](#empacotamento)
- [Análise do código e do comportamento](#análise-do-código-e-do-comportamento)
- [Qualidade do código e testes unitários](#qualidade-do-código-e-testes-unitários)
- [Issues](#issues)
- [Hospedagem do código](#hospedagem-do-código)
- [Interface gráfica do usuário (GUI): redesign e refatoração](#interface-gráfica-do-usuário-gui-redesign-e-refatoração)
- [Interface de usuário de terminal (TUI)](#interface-de-usuário-de-terminal-tui)

**## Roteiro preliminar**

Esta lista apresenta etapas de desenvolvimento futuras que dependem umas das outras:

1. Remover o sistema de plugins para reduzir a complexidade do código e melhorar a manutenibilidade
   ([#2424](https://github.com/bit-team/backintime/issues/2424)).

2. Migrar para o Python Packaging moderno
   ([#1575](https://github.com/bit-team/backintime/issues/1575)).

3. Adaptar ligeiramente a base de código ao novo código de gerenciamento de configuração. Finalmente,
   remover o antigo código de gerenciamento de configuração, que atualmente funciona como substituto.

4. Reativar testes unitários anteriormente desabilitados
   ([#2578](https://github.com/bit-team/backintime/issues/2578)).

5. Implementar o novo formato de arquivo de configuração (TOML).

   Issue relacionada: [#1984](https://github.com/bit-team/backintime/issues/1984)

**\*\*Mais coisas\*\***:

- Migração do mecanismo de logging para o próprio módulo `logging` do Python
  ([#2286](https://github.com/bit-team/backintime/issues/2286)).

- Reescrever a comunicação entre processos (IPC)
  ([#2260](https://github.com/bit-team/backintime/issues/2260)).

**## Sistema de plugins**

O sistema de plugins adiciona complexidade à base de código com menos benefícios. Portanto, ele será removido. Porém, a funcionalidade dos plugins existentes (notify, systray, user-callback) será integrada ao *\_Back In Time\_*. O usuário não deverá perceber a diferença. Isso facilitará o caminho para os novos padrões de empacotamento descritos na próxima seção. Consulte a issue [#2424](https://github.com/bit-team/backintime/issues/2424) para obter detalhes e o estado atual.

**## Empacotamento**

Atualmente, *\_Back In Time\_* utiliza um sistema de compilação baseado em `make`. No entanto, essa abordagem tem várias limitações e não segue os padrões modernos de empacotamento Python ([PEP 621](https://peps.python.org/pep-0621), [PEP 517](https://peps.python.org/pep-0517), [src layout](https://packaging.python.org/en/latest/tutorials/packaging-projects), [pyproject.toml](https://setuptools.pypa.io/en/latest/userguide/pyproject_config.html)).

A equipe pretende migrar para esses padrões contemporâneos para simplificar a manutenção do *\_Back In Time\_* ([#1575](https://github.com/bit-team/backintime/issues/1575)).

**## Análise do código e do comportamento**

Como nenhum dos membros atuais da equipe participou do desenvolvimento original do *\_Back In Time\_*, existe uma falta de compreensão profunda de certos aspectos da base de código e de sua funcionalidade. Parte do trabalho realizado neste projeto envolve pesquisar o código, seus recursos e sua infraestrutura, além de documentar as descobertas.

**## Qualidade do código e testes unitários**

Um dos desafios se assemelha a um problema de ovo e galinha: a estrutura do código não possui isolamento suficiente, tornando difícil, e em alguns casos quase impossível, escrever testes unitários valiosos. É necessária uma refatoração pesada do código, mas isso traz um alto risco de introduzir novos bugs. Para reduzir esse risco, testes unitários são essenciais para detectar possíveis bugs ou mudanças não intencionais no comportamento do *\_Back In Time\_*. Cada um dos problemas impede a solução do outro.

Considerando os três principais tipos de teste (*\_unitários\_*, *\_integração\_* e *\_sistema\_*), a suíte de testes atual consiste principalmente em *\_testes de sistema\_*. Embora esses *\_testes de sistema\_* sejam valiosos, seu propósito é diferente do dos *\_testes unitários\_*.

Devido à falta de *\_testes unitários\_* na suíte de testes, a base de código possui uma cobertura de testes notavelmente baixa
(veja a [Issue #1489](https://github.com/bit-team/backintime/issues/1489)).

A base de código não segue a [PEP8](https://peps.python.org/pep-0008/), que serve como estilo mínimo de programação Python. Atualmente, não é viável utilizar linters em sua configuração padrão. Um dos nossos objetivos é alinhar-nos aos padrões da PEP8 e atender aos requisitos dos linters de código.

**## Issues**

Todas as issues existentes foram triadas pela equipe atual.

[Labels](https://github.com/bit-team/backintime/labels) são atribuídos para indicar a prioridade, juntamente com um [milestone](https://github.com/bit-team/backintime/milestones) indicando qual versão planejada resolverá a issue. Algumas dessas issues persistem por muito tempo e envolvem vários problemas complexos. Elas podem ser difíceis de diagnosticar devido a vários fatores. Aumentar a cobertura de testes e a qualidade do código é uma das medidas destinadas a encontrar e implementar soluções para essas issues.

**## Hospedagem do código**

O plano é migrar para o [Codeberg.org](https://codeberg.org). Consulte também [esta entrada da FAQ](FAQ.md##move-project-to-alternative-code-hoster-eg-codeberg-gitlab-).

A ideia é iniciar a migração depois que o Debian 14 for lançado, na segunda metade do ano de 2027.

**## Interface gráfica do usuário (GUI): redesign e refatoração**

Ao longo dos anos, a GUI tornou-se cada vez mais complexa. Ela requer um redesign visual, bem como uma refatoração do código. Além disso, ela não possui testes. Esta é uma tarefa em andamento.

**## Interface de usuário de terminal (TUI)**

Várias pessoas usam *\_Back In Time\_* pelo terminal, por exemplo, por meio de um shell SSH em um servidor sem interface gráfica. Houve várias ideias para criar alternativas à GUI baseada em Qt: uma interface de usuário de terminal (TUI) ou o aprimoramento da interface de linha de comando (CLI) existente
([#254](https://github.com/bit-team/backintime/issues/254)); um frontend web
([#209](https://github.com/bit-team/backintime/issues/209)). Todas as ideias foram rejeitadas ou adiadas em favor de um formato de arquivo de configuração legível por humanos usando TOML ([#1984](https://github.com/bit-team/backintime/issues/1984)), partindo do pressuposto de que uma TUI ou uma interface web, embora conveniente e agradável, não seria mais necessária.

**# Licenciamento do material contribuído**

Lembre-se, ao contribuir, de que o código, a documentação e outros materiais enviados ao projeto são considerados licenciados sob os mesmos termos que o restante do trabalho. Com algumas exceções, trata-se da
[Licença Pública Geral GNU versão 2 ou posterior](https://spdx.org/licenses/GPL-2.0-or-later.html)
(`GPL-2.0-or-later`). Este projeto usa [metadados SPDX](https://spdx.dev/) para fornecer informações detalhadas sobre licença e direitos autorais em um formato legível por máquina. Esses dados estão
[disponíveis online](https://api.reuse.software/info/github.com/bit-team/backintime).

ou podem ser lidos a partir do repositório local com as
[ferramentas REUSE](https://reuse.software/).

**# Guia técnico rápido**

> [!CAUTION]
>
> Lembre-se de criar uma nova branch antes de começar qualquer modificação.
>
> Baseie sua branch de recurso ou correção de bug em `dev`
> (refletindo o estado de desenvolvimento mais recente).

1. Faça um fork deste repositório. Consulte a própria documentação do Microsoft GitHub sobre
   [como fazer um fork](https://docs.github.com/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo).

2. Clone seu próprio fork para sua máquina local e entre no diretório:

       $ git clone git@github.com:YOURNAME/backintime.git
       $ cd backintime

3. Crie e faça checkout da sua própria branch de recurso ou correção de bug usando `dev` como branch base:

       $ git checkout -b myfancyfeature dev

4. Agora você pode adicionar suas modificações.

5. Faça commit e push para o seu repositório fork:

       $ git commit -am 'commit message'
       $ git push

6. Teste suas modificações. Consulte as seções [Compilar e instalar](#compilar-e-instalar) e [Testes](#testes) para obter mais detalhes.

7. Acesse seu próprio repositório no site do Microsoft GitHub e crie um Pull Request.

   Consulte a própria documentação do Microsoft GitHub sobre
   [como criar um Pull Request com base no seu próprio fork](https://docs.github.com/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork).

<sub>Março de 2026</sub>
