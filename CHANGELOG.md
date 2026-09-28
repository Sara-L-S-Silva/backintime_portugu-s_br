<!---
SPDX-FileCopyrightText: © 2023 Christian BUHTZ <c.buhtz@posteo.jp>

SPDX-Licença-Identifier: GPL-2.0-or-later

This Arquivo is part of the program "Back In Tempo" which is released under GNU
General Public Licença v2 (GPLv2). See LICENSES Diretório or go para
<https://spdx.org/licenses/GPL-2.0-or-later.html>
-->
# Registro de alterações
[![Common Changelog](https://common-changelog.org/badge.svg)](https://common-changelog.org)

<!--- [2.0.0] (Desenvolvimento não lançado) -->
## [2.0.0-rc2] (2026-09-02)

### Alterado
- **Incompatível**: Gravação do arquivo de configuração by 2.0.0 not backward compatible com 
  Anterior versions devido à remoção de the legacy `profiles=` entry and EncFS
  Suporte. ([PR#1850](https://github.com/bit-team/backintime/pull/1850))
- **Reescrito do zero**: Subsistema de montagem (backend and Criptografia).
  O comportamento deve permanecer inalterado; regressions cannot be fully ruled
  out. ([PR#2449](https://github.com/bit-team/backintime/pull/2449))
- **Incompatível**: Versão mínima do Python 3.13 increased
- **Incompatível**: Part of the metadados do Backup ("info" Arquivo) migrado de an
  INI-like format para JSON. Older versions of _Back In Tempo_ (antes 2.0.0) may
  have issues com Backups created in 2.0.0 or later. Restoring still works,
  but Propriedade and Permissão Informações não é restored correctly.
  ([PR#2527](https://github.com/bit-team/backintime/pull/2527)) para evitar
- As permissões padrão do ponto de montagem foram alteradas de 700 para 711
  ([PR#2451](https://github.com/bit-team/backintime/pull/2451)) para evitar
  FUSE Montagem failures ao acessar por diferentes contextos de usuário.
- Registro de alterações migrado para _Common Changelog_ standard
- Build: registro de alterações distribuído como HTML
- GUI: Melhorado o diálogo de importação de configuração na primeira inicialização (Dominic Maluski, @maluskid, [#2483](https://github.com/bit-team/backintime/issues/2483))
- Opções avançadas: Descontinuar and Avisar about Desativado SSH Remoto checks
  if one of these two options is (non-Padrão) Desativado: "Verificar if host remoto
  está Online", "Verificar if host remoto suporta todos os comandos necessários"
  ([#2482](https://github.com/bit-team/backintime/issues/2482))
- Clear up Licença and copyright situation of `qt/serviceHelper.py`
  ([#1986](https://github.com/bit-team/backintime/issues/1986))
- GUI: Modo de agendamento "Repeatedly (anacron)" re-phrased and extended com
  explanations ([#2507](https://github.com/bit-team/backintime/issues/2507))
- Estado da GUI: "Mostrar arquivos ocultos" is on by Padrão
- Plugins definidos pelo usuário: Descontinuar and Avisar about Plugins definidos pelo usuário found 
  ([#2424](https://github.com/bit-team/backintime/issues/2424))
- Ciclo de vida ocioso for D-Bus helper (serviceHelper.py) em vez de running
  indefinitely ([#2581](https://github.com/bit-team/backintime/issues/2581))

### Adicionado
- Novo idioma Lao (lo) (Bone NI [@bounkirdni](https://codeberg.org/bounkirdni)]
- Detectar e relatar coreutils variant (GNU, Rust/uutils, BusyBox) in `--diagnostics` output ([#2478](https://github.com/bit-team/backintime/issues/2478))
- Gocryptfs for SSH Criptografado Perfis ([PR#2486](https://github.com/bit-team/backintime/pull/2486))
- CLI: `--usage` option for the `show` command, showing total physical disk usage of Todos Backups ([@arcsinhx](https://github.com/arcsinhx), [PR#2480](https://github.com/bit-team/backintime/pull/2480))
- Dependências:
  - Build: `pandoc` para convert markdown changelog into HTML
  - CLI em tempo de execução: `gocryptfs`
- CLI: Listar todos os perfis com `show --profiles` ([#2336](https://github.com/bit-team/backintime/issues/2336))

### Removido
- **Incompatível**: EncFS Suporte including existing EncFS Perfis
  ([PR#2492](https://github.com/bit-team/backintime/pull/2492))
- **Incompatível**: Suporte a arquivo de configuração global
  ([PR#2493](https://github.com/bit-team/backintime/issues/2493))
- Dependência: `encfs`
- CLI:
  - **Incompatível**: CLI option `--share-path` which was Obsoleto earlier in `1.6.0` ([#2535](https://github.com/bit-team/backintime/issues/2535))
  - Switch `--keep-mount`
  - Command `decode` por causa de EncFS removal ([#1734](https://github.com/bit-team/backintime/issues/1734))
  - Command `benchmark-cipher` ([#2120](https://github.com/bit-team/backintime/issues/2120))
- SSH Cipher ([#2176](https://github.com/bit-team/backintime/issues/2176))
- Exemplos de configuração
- Idiomas Faroese, Croatian, Vietnames and Norwegian (Nynorsk)
  ([#2080](https://github.com/bit-team/backintime/issues/2080))
- GUI Opções avançadas:
  - "Verificar if host remoto está Online" ([#2482](https://github.com/bit-team/backintime/issues/2482)).
  - "Verificar if host remoto suporta todos os comandos necessários" ([#2482](https://github.com/bit-team/backintime/issues/2482)).
- Alvos de teste nos Makefiles. Usar um executor de testes Python comum (e.g. pytest) instead.

## Corrigido
- **Incompatível**: "Remover Backups older than" value was stored only as years ([#2460](https://github.com/bit-team/backintime/issues/2460))
- Impedir travamento in case a plugin fails ([#2447](https://github.com/bit-team/backintime/issues/2447))
- Garantir que a janela de restauração permaneça aberta while Restaurar is running. (Dominic Maluski, @maluskid, [#2503](https://github.com/bit-team/backintime/issues/2503))
- Incluir SSH_AUTH_SOCK no ambiente do cron para Ativar SSH agent access (Dan Kortschak, [@kortschak](https://github.com/kortschak), [#2506](https://github.com/bit-team/backintime/issues/2506))
- Modo de agendamento "Repeatedly" using "Hourly" units is now consistent com Outro units ([#2507](https://github.com/bit-team/backintime/issues/2507))
- Travamento ao Usar Btrfs-subvolume as Backup Destino (Daidalos [@D4id4los](https://github.com/D4id4los), [#2487](https://github.com/bit-team/backintime/issues/2487))
- Travamento ao polkit Autenticação Diálogo times out while setting up udev Agendamento ([#2375](https://github.com/bit-team/backintime/issues/2375))
- Guard pause/resume/Parar actions in the GUI against ProcessLookupError quando o Backup Processo has already exited ([#1604](https://github.com/bit-team/backintime/issues/1604))
- Enum names in config Arquivo are replaced by their values ([11930b68](https://github.com/bit-team/backintime/commit/11930b68))
- Remoção de Backup ausente devido a a miscalculation in the "Remover Backups older than" rule, introduced in Versão 1.5.4 ([#2588](https://github.com/bit-team/backintime/issues/2588#issuecomment-5675126121))

## [1.6.1] (2026-02-10)

### Corrigido

- SSH-Key selector widget Tratar binary keys, Ausente but configured keys ([#2399](https://github.com/bit-team/backintime/issues/2399), [#2400](https://github.com/bit-team/backintime/issues/2400))
- SSH-Key selector widget is Mais robust on unexpected edge cases ([#2399](https://github.com/bit-team/backintime/issues/2399), [#2400](https://github.com/bit-team/backintime/issues/2400))
- Instalar backintime-config man page in Correto location

## [1.6.0] (2026-02-08)

### Alterado

- **Incompatível** Desativar EncFS for creation of Novo Backup Perfis ([#2315](https://github.com/bit-team/backintime/issues/2315), [#1734](https://github.com/bit-team/backintime/issues/1734))
- **Incompatível** A "Snapshot" now is a "Backup" ([#1929](https://github.com/bit-team/backintime/issues/1929))
- **Incompatível** Obsoleto and removed make targets: "Teste", "Teste-v", "unittest", "unittest-v"
- Manpage backintime-config moved de section 1 para 5 ([#1773](https://github.com/bit-team/backintime/issues/1773))
- Novo Dependência "bash" for root mode starter script "backintime-qt_polkit" ([#2328](https://github.com/bit-team/backintime/issues/2328))
- Novo Dependência (GUI em tempo de execução) para "python3-pyqt6.qtsvg" for loading SVG icons ([#1961](https://github.com/bit-team/backintime/issues/1961))
- Desativar Agendamento widget in GUI if cron/crontab está ausente ([#2245](https://github.com/bit-team/backintime/issues/2245), [@m4rcu5](https://github.com/m4rcu5) Marcus von Dam)
- Opções avançadas replaced two checkboxes com single widget para configure symlink copying behavior ([#1652](https://github.com/bit-team/backintime/issues/1652))
- "Repeatedly (anacron)" Agendamento behave consistent. Reversed minor bug introduced com 060324e ([#1791](https://github.com/bit-team/backintime/issues/1791)) in 1.5.3 ([#2250](https://github.com/bit-team/backintime/issues/2250))
- Stricter Permissões (600) for fileinfo.bz2 and takesnapshot.Log.bz2 ([#2235](https://github.com/bit-team/backintime/issues/2235))
- Unlocking ssh-agent Usar "force" em vez de "prefer" for SSH_ASKPASS_REQUIRE ([#2170](https://github.com/bit-team/backintime/issues/2170)) ([@daviewales](https://github.com/daviewales))
- Parar passing Janela ID when inhibiting Suspensão via D-Bus power manager ([#2084](https://github.com/bit-team/backintime/issues/2084))
- Reorder DBUS Serviço provider Listar for Suspensão mode inhibition ([#2084](https://github.com/bit-team/backintime/issues/2084))
- Man pages generated de AsciiDoc, except backintime-config ([#2085](https://github.com/bit-team/backintime/issues/2085))
- Descontinuar command "benchmark-cipher" ([#2120](https://github.com/bit-team/backintime/issues/2120))
- Descontinuar command "Snapshots-Caminho" ([#2130](https://github.com/bit-team/backintime/issues/2130))
- Descontinuar commands "Snapshots-Listar", "Snapshots-Listar-Caminho", "Último-Snapshots" and "Último-Snapshot-Caminho" ([#2130](https://github.com/bit-team/backintime/issues/2130))
- Descontinuar command "smart-Remover" ([#2124](https://github.com/bit-team/backintime/issues/2124))
- Descontinuar command "Backup-job" ([#2124](https://github.com/bit-team/backintime/issues/2124))
- Descontinuar command "Remover-and-do-not-ask-again" ([#2124](https://github.com/bit-team/backintime/issues/2124))
- Descontinuar command "decode" ([#2124](https://github.com/bit-team/backintime/issues/2124))
- Descontinuar flag-like command aliases (e.g. "--Backup" for "Backup") ([#2124](https://github.com/bit-team/backintime/issues/2124))
- Descontinuar argument flag "--Perfil-id" ([#2125](https://github.com/bit-team/backintime/issues/2125))
- Descontinuar argument flag "--share-Caminho" ([#2124](https://github.com/bit-team/backintime/issues/2124))
- Descontinuar Usar of SSH Cipher ([#2143](https://github.com/bit-team/backintime/issues/2143))
- Prefer ed25519 SSH keys (if present) for Novo created Perfis ([#2094](https://github.com/bit-team/backintime/issues/2094))
- Generating Novo SSH key will Usar Padrão key type provided by ssh-keygen ([#2194](https://github.com/bit-team/backintime/issues/2194))
- Abrir man page and changelog in a text Diálogo
- Minimum PyLint Versão increased para 4.0.0

### Adicionado

- Idioma Georgian (ka)
- Gocryptfs for Local Criptografado Perfis ([#1897](https://github.com/bit-team/backintime/issues/1897), [#1734](https://github.com/bit-team/backintime/issues/1734), [@germar](https://github.com/germar), [@daviewales](https://github.com/daviewales))
- Diálogo para sugerir arquivos/diretórios/padrões usados com frequência for Backup exclusion ([#2309](https://github.com/bit-team/backintime/issues/2309))
- Systray icon can be forced para Dark or Light
- Logotipo do aplicativo and symbolic systray icon ([#1961](https://github.com/bit-team/backintime/issues/1961), Gregory Deseck [@gregorydk](https://github.com/gregorydk))
- Root mode indicator in barra de status ([#1964](https://github.com/bit-team/backintime/issues/1964))
- Option para not using an explicit SSH key Arquivo. In consequence this supports extern key agents and SSH clients own Configuração ([#1146](https://github.com/bit-team/backintime/issues/1146))
- SSH-Key selector widget in Manage Perfis Diálogo ([#1146](https://github.com/bit-team/backintime/issues/1146), [#2094](https://github.com/bit-team/backintime/issues/2094), [#2095](https://github.com/bit-team/backintime/issues/2095), [#2275](https://github.com/bit-team/backintime/issues/2275) [@m4rcu5](https://github.com/m4rcu5) Marcus van Dam)
- "ETA" value in barra de status ([#2101](https://github.com/bit-team/backintime/issues/2101))
- Diálogo de confirmação de desligamento ([#2102](https://github.com/bit-team/backintime/issues/2102)) (Huaide Jiang [@LatiosInAltoMare](https://github.com/LatiosInAltoMare))
- Verificar e avisar if include Listar entries do not exists in Backup Origem ([#1586](https://github.com/bit-team/backintime/issues/1586)) ([@rafaelhdr](https://github.com/rafaelhdr))
- Asciidoctor as dependência de Build ([#2085](https://github.com/bit-team/backintime/issues/2085))
- Command "Mostrar" para Substituir "Snapshots-Listar", "Snapshots-Listar-Caminho", "Último-Snapshots" and "Último-Snapshot-Caminho" ([#2130](https://github.com/bit-team/backintime/issues/2130))
- Command "prune" para Substituir "smart-Remover" ([#2124](https://github.com/bit-team/backintime/issues/2124))
- Flag "--Segundo plano" for command "Backup" para Substituir command "Backup-job" ([#2124](https://github.com/bit-team/backintime/issues/2124))
- Flag "--skip-confirmation" for command "Remover" para Substituir command "Remover-and-do-not-ask-again" ([#2124](https://github.com/bit-team/backintime/issues/2124))
- Flag "--Perfil" accept ID's beside names only ([#2125](https://github.com/bit-team/backintime/issues/2125))
- Flag "-p" as alias for "--Perfil" ([#2125](https://github.com/bit-team/backintime/issues/2125))
- "Menos storage space" threshold para Avisar the Usuário ([#2110](https://github.com/bit-team/backintime/issues/2110)) ([@fest6](https://github.com/fest6))
- Lembrar tamanho e posição of Manage Perfis Diálogo
- Editor de Usuário-callback offer a Padrão script in case no script exists ([#1331](https://github.com/bit-team/backintime/issues/1331))

### Removido

- **Incompatível** Remover suporte ao Python for Versão 3.9 & 3.10 ([#2129](https://github.com/bit-team/backintime/issues/2129))
- Parar de usar QWindow.winId() ([#2084](https://github.com/bit-team/backintime/issues/2084))
- Tradução da interface in Bosnian, Thai, and Occidental/Interlingue ([#1914](https://github.com/bit-team/backintime/issues/1914))
- arquivo Licença em favor de LICENSES Diretório and LICENSES.md Arquivo
- SSH Cipher Configuração in Manage Perfis Diálogo ([#2143](https://github.com/bit-team/backintime/issues/2143))

### Corrigido

- Travamento em config Restaurar Diálogo
- Consider symbolic icons as fallbacks ([#2345](https://github.com/bit-team/backintime/issues/2345), [#2289](https://github.com/bit-team/backintime/issues/2289))
- Avisar usuários e impedir Backups para exFAT volumes devido a lack of hardlink Suporte ([#2337](https://github.com/bit-team/backintime/issues/2337))
- Exibir mensagem adequada aos usuários when root mode fails devido a inactive or Ausente polkit agent ([#2328](https://github.com/bit-team/backintime/issues/2328), Derek Veit [@DerekVeit](https://github.com/DerekVeit))
- Travamento em Compare Snapshots Diálogo (aka Snapshots Diálogo) when comparing/diff two Backups ([#2327](https://github.com/bit-team/backintime/issues/2327) Michael Neese [@madic-creates](https://github.com/madic-creates))
- Visualização de arquivos and Diálogo Comparar Backups now Abrir the clicked item correctly even com multiple selection or single-click-para-Abrir Ativado ([#2330](https://github.com/bit-team/backintime/issues/2330))
- Travamento em Compare Snapshots Diálogo (aka Snapshots Diálogo) when comparing/diff two Backups ([#2327](https://github.com/bit-team/backintime/issues/2327) Michael Neese [@madic-creates](https://github.com/madic-creates))
- Forçar codificação UTF-8 in takesnapshot.Log and Alguns Outro Arquivos ([#2298](https://github.com/bit-team/backintime/issues/2298))
- Erro de atributo about Ausente 'cbCopyUnsafeLinks' ([#2279](https://github.com/bit-team/backintime/issues/2279))
- Usar LC_Todos em vez de LC_Tempo para set the locale
- Otimizar subparsers and usage output ([#2132](https://github.com/bit-team/backintime/issues/2132))
- Redesenhar about Diálogo ([#1936](https://github.com/bit-team/backintime/issues/1936))
- Parar waking up monitor when inhibit Suspensão on Backup starts ([#714](https://github.com/bit-team/backintime/issues/714), [#1090](https://github.com/bit-team/backintime/issues/1090))
- Evitar diálogo de confirmação de desligamento on Budgie and Cinnamon Desktop environments ([#788](https://github.com/bit-team/backintime/issues/788))
- Travamento em "Manage Perfis" Diálogo when using "qt6ct" ([#2128](https://github.com/bit-team/backintime/issues/2128))
- **Incompatível** Systray Processo não mais exposes sensitive Backup Perfil Informações quando o Desktop session belongs para another Usuário ([#2237](https://github.com/bit-team/backintime/issues/2237), reported and co-authored by [@samo-sk](https://github.com/samo-sk))
- Permitir que o modo root do BiT abra URLs em navegador externo

## [1.5.6] (2025-10-05)

### Corrigido

- Always Usar 0 as Janela ID value when inhibiting Suspensão via D-Bus power manager ([#2084](https://github.com/bit-team/backintime/issues/2084), [#2268](https://github.com/bit-team/backintime/issues/2268), [#2192](https://github.com/bit-team/backintime/issues/2192))
- Travamento em "Manage Perfis" Diálogo when using "qt6ct" ([#2128](https://github.com/bit-team/backintime/issues/2128))
- Abrir o registro de alterações Online se o arquivo CHANGES Local estiver ausente ([#2266](https://github.com/bit-team/backintime/issues/2266))
- Desativar a abertura do navegador (e.g. project Site) in root-mode

## [1.5.5] (2025-06-05)

### Corrigido

- Desbloqueio de chaves SSH com frases-senha on Novo created Perfis ([#2164](https://github.com/bit-team/backintime/issues/2164)) ([@davidfjoh](https://github.com/davidfjoh))

## [1.5.4] (2025-03-24)

### Não categorizado

- Alteração incompatível: Regras de remoção automática "Inodes livres" and "Espaço livre" Desativado by Padrão in Novo created Perfis ([#1976](https://github.com/bit-team/backintime/issues/1976))
- Corrigir!: Regra de remoção inteligente "Manter um Snapshot por semana ou o da última semana" Usar calendar weeks
- Doc: Remover & Retention (formally known as Auto-/Smart-Remover) com improved GUI and Usuário Manual section ([#2000](https://github.com/bit-team/backintime/issues/2000))

### Alterado

- Completed informações de licença para conform para REUSE.software and SPDX standards.
- Aviso mais claro e enfático about EncFS deprecation and removal ([#1904](https://github.com/bit-team/backintime/issues/1904))
- Updated Desktop entry Arquivos
- Mover several values de config Arquivo into Novo introduce state Arquivo ($XDG_STATE_HOME/backintime.json)

### Corrigido

- Padrões de exclusão are now diferencia maiúsculas de minúsculas when added ([#2040](https://github.com/bit-team/backintime/issues/2040))
- The largura da quarta coluna in Arquivos view is now saved
- Snapshot compare copiar link simbólico como link simbólico ([#1902](https://github.com/bit-team/backintime/issues/1902)) (Peter Sevens [@sevens](https://github.com/sevens))
- Travamento ao comparing a Snapshot com a symlink pointing para a nonexistent target (Peter Sevens [@sevens](https://github.com/sevens))
- Travamento (KeyError) opening Idioma setup Diálogo com localidade/idioma desconhecido

### Adicionado

- Abrir Manual do usuário (Local if Disponível otherwise Online) via Help menu
- Menu de contexto da barra de ferramentas para display the Botões in different combinations com icons and text ([#1105](https://github.com/bit-team/backintime/issues/1105), [#2002](https://github.com/bit-team/backintime/issues/2002)) (Samuel Moore [@s4moore](https://github.com/s4moore))
- Adicionar minutos de deslocamento para hourly Agendamentos (David Gibbs [@fallingrock](https://github.com/fallingrock))

## [1.5.3] (2024-11-13)

### Não categorizado

- Doc: Usuário Manual (Build com MkDocs) ([#1838](https://github.com/bit-team/backintime/issues/1838)) (Kosta Vukicevic [@stcksmsh](https://github.com/stcksmsh))
- Doc: Usuário-callback topic in Usuário Manual ([#1659](https://github.com/bit-team/backintime/issues/1659))
- Refactor!: Remover campo de configuração não utilizado "Usuário_callback.no_logging" ([#1887](https://github.com/bit-team/backintime/issues/1887))
- Refactor!: Remover verificação do eCryptFS for home Pasta ([#1855](https://github.com/bit-team/backintime/issues/1855))
- Build: Substituir "pycodestyle" linter com "flake8" ([#1839](https://github.com/bit-team/backintime/issues/1839))

### Adicionado

- Suporte ao idioma Interlingua (Occidental)
- Avisar se o diretório de destino is formatted as NTFS ([#1854](https://github.com/bit-team/backintime/issues/1854)) (David Gibbs [@fallingrock](https://github.com/fallingrock))
- Suporte fcron ([#610](https://github.com/bit-team/backintime/issues/610))
- Mensagem ao usuário sobre a versão candidata ([#1906](https://github.com/bit-team/backintime/issues/1906))

### Corrigido

- Impedir duplicatas in Exclude/Include Listar of Manage Perfis Diálogo
- Corrigir Qt segmentation fault when canceling out of unconfigured BiT ([#1095](https://github.com/bit-team/backintime/issues/1095)) (Derek Veit [@DerekVeit](https://github.com/DerekVeit))
- Corrigir alternativas do flock global ([#1834](https://github.com/bit-team/backintime/issues/1834)) (Timothy Southwick [@NickNackGus](https://github.com/NickNackGus))
- Usar a senha da chave SSH somente se ela for válida, otherwise request it de Usuário ([#1852](https://github.com/bit-team/backintime/issues/1852)) (David Wales [@daviewales](https://github.com/daviewales))

### Alterado

- **Incompatível**: Python 3.9 é a versão mínima necessária ([#1731](https://github.com/bit-team/backintime/issues/1731))
- **Incompatível**: Auto migration of config Versão 4 or lower not longer supported ([#1857](https://github.com/bit-team/backintime/issues/1857))
- Dependência: remover libnotify-bin (notify-send) ([#1156](https://github.com/bit-team/backintime/issues/1156))
- Dependência: PyFakeFS minimal Versão 5.6 ([#1911](https://github.com/bit-team/backintime/issues/1911))
- Aba Geral and its Agendamento section
- Módulo próprio para Manage Perfis Diálogo and separate Generals tab code ([#1865](https://github.com/bit-team/backintime/issues/1865))
- Remover classe OrderedSet
- Remover os.Sistema() de class Execute
- Systray notificações usam DBUS em vez de notify-send ([#1156](https://github.com/bit-team/backintime/issues/1156)) (Felix Stupp [@Zocker1999NET](https://github.com/Zocker1999NET))

## [1.5.2] (2024-08-06)

### Corrigido

- Garantir nova linha no final do crontab ([#781](https://github.com/bit-team/backintime/issues/781))

### Não categorizado

- Corrigir(Tradução): Corrigir strings traduzidas corrompidas in Basque, Islandic and Spanish causing Aplicativo Travamentos ([#1828](https://github.com/bit-team/backintime/issues/1828))
- Build(Tradução): Script auxiliar de idiomas processing syntax checks on po-Arquivos

## [1.5.1] (2024-07-27)

### Corrigido

- Usar Correto port para ping SSH Proxy ([#1815](https://github.com/bit-team/backintime/issues/1815))

## [1.5.0] (2024-07-26)

### Não categorizado

- Dependência: Migração para PyQt6
- Alteração incompatível: EncFS Aviso de descontinuação ([#1735](https://github.com/bit-team/backintime/issues/1735), [#1734](https://github.com/bit-team/backintime/issues/1734))
- Alteração incompatível: GUI iniciada com --debug does não mais Adicionar --debug para the crontab for scheduled Perfis. 
- Chore!: Remover "debian" Pasta ([#1548](https://github.com/bit-team/backintime/issues/1548))
- Build: Ativar várias regras do PyLint ([#1755](https://github.com/bit-team/backintime/issues/1755), [#1766](https://github.com/bit-team/backintime/issues/1766))
- Build: adicionar metadados do AppStream ([#1642](https://github.com/bit-team/backintime/issues/1642))
- Build: PyLint unit Teste is skipped if PyLint isn't installed, but will always Executar on TravisCI ([#1634](https://github.com/bit-team/backintime/issues/1634))
- Build: hash do commit Git is presevered while "make Instalar" ([#1637](https://github.com/bit-team/backintime/issues/1637))
- Build: corrigir criação do link simbólico do bash-completion while installing & adding --diagnostics ([#1615](https://github.com/bit-team/backintime/issues/1615))
- Build: TravisCI Usar PyQt (except arch "ppc64le")

### Adicionado

- Avisar se o Cron não estiver em execução ([#1747](https://github.com/bit-team/backintime/issues/1747))
- Perfil and GUI Permitir para activate debug output for scheduled jobs by adding '--debug' para crontab entry ([#1616](https://github.com/bit-team/backintime/issues/1616), contributed by [@stcksmsh](https://github.com/stcksmsh) Kosta Vukicevic)
- Suporte a proxy SSH (jump) host ([#1688](https://github.com/bit-team/backintime/issues/1688)) ([@cgrinham](https://github.com/cgrinham), Christie Grinham)
- Suporte ao rsync '--one-Arquivo-Sistema' in Opções avançadas ([#1598](https://github.com/bit-team/backintime/issues/1598))
- "*-dev" Versão strings contain Último commit hash ([#1637](https://github.com/bit-team/backintime/issues/1637))

### Corrigido

- Alternativa do flock global para modo de usuário único if insufficient Permissões ([#1743](https://github.com/bit-team/backintime/issues/1743), [#1751](https://github.com/bit-team/backintime/issues/1751))
- Corrigir Qt segmentation fault com uninstall ExtraMouseButtonEventFilter when closing main Janela ([#1095](https://github.com/bit-team/backintime/issues/1095))
- Names of weekdays and months translated Correto ([#1729](https://github.com/bit-team/backintime/issues/1729))
- Flock global para vários usuários ([#1122](https://github.com/bit-team/backintime/issues/1122), [#1676](https://github.com/bit-team/backintime/issues/1676))
- "Backup Pastas" Listar does reflect the selected Snapshot ([#1585](https://github.com/bit-team/backintime/issues/1585)) ([@rafaelhdr](https://github.com/rafaelhdr) Rafael Hurpia da Rocha)
- Validação das configurações do comando diff in compare Snapshots Diálogo ([#1662](https://github.com/bit-team/backintime/issues/1662)) ([@stcksmsh](https://github.com/stcksmsh) Kosta Vukicevic)
- Abrir pastas vinculadas simbolicamente in Visualização de arquivos ([#1476](https://github.com/bit-team/backintime/issues/1476))
- Respeitar o modo escuro using color roles ([#1601](https://github.com/bit-team/backintime/issues/1601))
- "Highly recommended" exclusion pattern in "Manage Perfil" Diálogo's "Exclude" tab Mostrar Ausente only ([#1620](https://github.com/bit-team/backintime/issues/1620))
- `make install` ignored $(DEST) in Arquivo migration part ([#1630](https://github.com/bit-team/backintime/issues/1630))

### Removido

- Context menu in LogViewDialog ([#1578](https://github.com/bit-team/backintime/issues/1578))
- Field "filesystem_Montagem" and "Snapshot_Versão" in "info" Arquivo ([#1684](https://github.com/bit-team/backintime/issues/1684))

### Alterado

- Substituir Config.Usuário() com getpass.getuser() ([#1694](https://github.com/bit-team/backintime/issues/1694))

## [1.4.3] (2024-01-30)

### Adicionado

- Exclude 'SingletonLock' and 'SingletonCookie' (Discord) and 'lock' (Mozilla Firefox) Arquivos by Padrão (part of [#1555](https://github.com/bit-team/backintime/issues/1555))

### Não categorizado

- Work around: Relax `rsync` exit code 23: Ignorar em vez de Erro now (part of [#1587](https://github.com/bit-team/backintime/issues/1587))
- Feature (Experimental): Adicionar Novo Snapshot Log filter `rsync transfer failures (experimental)` para find them easier (they are normally not shown as "Erro").  
- Melhorar: Launcher for BiT GUI (root) does not enforce Wayland anymore but uses same Configurações as for BiT GUI (userland) ([#1350](https://github.com/bit-team/backintime/issues/1350))
- Alterar of semantics: BiT running as root never disables Suspensão durante taking a Backup ("inhibit Suspensão") even though this may have worked antes in BiT <= v1.4.1 sometimes (required para Corrigir [#1592](https://github.com/bit-team/backintime/issues/1592))
- Build: Usar PyLint in unit Testes para catch E1101 (no-member) Erros.
- Build: Activate PyLint Aviso W1401 (anomalous-backslash-in-string).
- Build: Adicionar codespell config.
- Build: Permitir Manual specification of python executable (--python=PYTHON_Caminho) in common/configure and qt/configure
- Build: Todos starter scripts do Usar an absolute Caminho para the python executable by Padrão now via common/configure and qt/configure ([#1574](https://github.com/bit-team/backintime/issues/1574))
- Build: Instalar dbus Configuração Arquivo para /usr/share not /etc ([#1596](https://github.com/bit-team/backintime/issues/1596))
- Build: `configure` does Excluir Antigo installed Arquivos (`qt4plugin.py` and `net.launchpad.backintime.serviceHelper.conf`) that were renamed or moved in a Anterior Versão ([#1596](https://github.com/bit-team/backintime/issues/1596))
- Tradução: Minor modifications in Origem strings and updating Idioma Arquivos.
- Improved: qtsystrayicon.py, qt5_probing.py, usercallbackplugin.py and Todos parts of app.py 

### Corrigido

- 'qt5_probing.py' hangs when BiT is Executar as root and no Usuário is logged into a Desktop environment ([#1592](https://github.com/bit-team/backintime/issues/1592) and [#1580](https://github.com/bit-team/backintime/issues/1580))
- Launching BiT GUI (root) hangs on Wayland sem showing the GUI ([#836](https://github.com/bit-team/backintime/issues/836))
- Disabling Suspensão durante taking a Backup ("inhibit Suspensão") hangs when BiT is Executar as root and no Usuário is logged into a Desktop environment ([#1592](https://github.com/bit-team/backintime/issues/1592))
- RTE: module 'qttools' has no attribute 'initate_translator' com encFS when prompting the Usuário for a Senha ([#1553](https://github.com/bit-team/backintime/issues/1553)).
- Agendamento dropdown menu used "minutes" em vez de "hours".
- Unhandled exception "TypeError: 'NoneType' object não é callable" in tools.py function __Log_Chaveiro_Aviso ([#820](https://github.com/bit-team/backintime/issues/820)). 

### Alterado

- Solved circular Dependência between tools.py and logger.py para Corrigir [#820](https://github.com/bit-team/backintime/issues/820)

## [1.4.1] (2023-10-01)

### Não categorizado

- Dependência: Adicionar "qt Traduções" para GUI runtime Dependências ([#1538](https://github.com/bit-team/backintime/issues/1538)).
- Build: Unit Testes do generically Ignorar Todos em vez de well-known Avisos now ([#1539](https://github.com/bit-team/backintime/issues/1539)).
- Build: Avisos about Ausente Qt Tradução now are ignored while Testes ([#1537](https://github.com/bit-team/backintime/issues/1537)).

### Corrigido

- GUI didn't Iniciar when "Mostrar arquivos ocultos" Botão was on ([#1535](https://github.com/bit-team/backintime/issues/1535)).

## [1.4.0] (2023-09-14)

### Não categorizado

- Project: Renamed branch "master" para "main" and started "gitflow" branching model.
- GUI Alterar: View Último (Snapshot) Log Botão in GUI uses "document-Abrir-recent" icon now em vez de "document-Novo" ([#1386](https://github.com/bit-team/backintime/issues/1386))
- Alteração incompatível: Versão mínima do Python 3.8 required ([#1358](https://github.com/bit-team/backintime/issues/1358)).
- Documentação: Removed outdated docbook ([#1345](https://github.com/bit-team/backintime/issues/1345)).
- Testes: TravisCI now can Usar dbus
- Build: Introduced .readthedocs.yaml as asked by ReadTheDocs.org ([#1443](https://github.com/bit-team/backintime/issues/1443)).
- Dependência: The oxygen icons should be installed com the BiT Qt GUI since they are used as Alternativa in case of Ausente icons
- Tradução: Strings para translate now easier para understand for translators ([#1448](https://github.com/bit-team/backintime/issues/1448), [#1457](https://github.com/bit-team/backintime/issues/1457), [#1462](https://github.com/bit-team/backintime/issues/1462), [#1465](https://github.com/bit-team/backintime/issues/1465)).
- Tradução: Improved completeness of Traduções and additional modifications of Origem strings ([#1454](https://github.com/bit-team/backintime/issues/1454), [#1512](https://github.com/bit-team/backintime/issues/1512))
- Tradução: Plural forms Suporte ([#1488](https://github.com/bit-team/backintime/issues/1488)).

### Alterado

- Renamed qt4plugin.py para systrayiconplugin.py (we are using Qt5 for years now ;-)
- Removed unfinished feature "Full Sistema Backup" ([#1526](https://github.com/bit-team/backintime/issues/1526))

### Corrigido

- AttributeError: can't set attribute 'showHiddenFiles' in app.py ([#1532](https://github.com/bit-team/backintime/issues/1532))
- Verificar SSH login works on machines com limited commands ([#1442](https://github.com/bit-team/backintime/issues/1442))
- Ausente icon in SSH private key Botão ([#1364](https://github.com/bit-team/backintime/issues/1364))
- issue principal for Ausente or empty Sistema-tray icon ([#1306](https://github.com/bit-team/backintime/issues/1306))
- Sistema-tray icon Ausente or empty (GUI and cron) ([#1236](https://github.com/bit-team/backintime/issues/1236))
- Melhorar KDE plasma icon compatibility ([#1159](https://github.com/bit-team/backintime/issues/1159))
- Unit Teste fails on Alguns machines devido a Aviso "Ignoring XDG_SESSION_TYPE=wayland on Gnome..." ([#1429](https://github.com/bit-team/backintime/issues/1429))
- Generation of config-manpage caused an Erro com Debian's Lintian ([#1398](https://github.com/bit-team/backintime/issues/1398)).
- Return empty Listar in smartRemove ([#1392](https://github.com/bit-team/backintime/issues/1392), [Debian#973760](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=973760))
- Ao criar um Snapshot reports `rsync` Erros now even se não houver Snapshot was taken ([#1491](https://github.com/bit-team/backintime/issues/1491))
- takeSnapshot() recognizes Erros now by also evaluating the rsync exit code ([#489](https://github.com/bit-team/backintime/issues/489)) 
- The Usuário-callback de erro is now always called if an Erro happened while Ao criar um Snapshot ([#1491](https://github.com/bit-team/backintime/issues/1491))
- D-Bus serviceHelper Erro "LimitExceeded: Maximum length of command line reached (100)": 
- Treat rsync exit code 24 as INFO em vez de Erro ([#1506](https://github.com/bit-team/backintime/issues/1506))
- Adicionar Suporte for ChainerBackend class as Chaveiro which iterates over Todos supported Chaveiro backends ([#1410](https://github.com/bit-team/backintime/issues/1410))

### Adicionado

- Introduzir novos códigos de erro for the "Erro" Usuário callback (as part of [#1491](https://github.com/bit-team/backintime/issues/1491)):  
- The `rsync` exit code is now contained in the Snapshot Log (part of [#489](https://github.com/bit-team/backintime/issues/489)). Example: 
- Exclude /swapfile by Padrão ([#1053](https://github.com/bit-team/backintime/issues/1053))
- Rearranged menu bar and its entries in the main Janela ([#1487](https://github.com/bit-team/backintime/issues/1487), [#1478](https://github.com/bit-team/backintime/issues/1478)).
- Configurar o idioma da interface do usuário via config Arquivo and GUI.
- Tradução para persa e vietnamita ([#1460](https://github.com/bit-team/backintime/issues/1460)).
- Mensagem para Usuários (depois 10 starts of BIT Gui) para motivate them contributing Traduções ([#1473](https://github.com/bit-team/backintime/issues/1473)).

### Removido

- Tratamento e verificação of Usuário Grupo "fuse" ([#1472](https://github.com/bit-team/backintime/issues/1472)).
- Tradução in Canadian English, British English and Javanese ([#1455](https://github.com/bit-team/backintime/issues/1455)).

## [1.3.3] (2023-01-04)

### Adicionado

- Novo argumento de linha de comando "--diagnostics" para Mostrar helpful info for better issue Suporte ([#1100](https://github.com/bit-team/backintime/issues/1100))
- Gravar toda a saída do Log em stderr; do not pollute stdout com INFO and Aviso Mensagens anymore ([#1337](https://github.com/bit-team/backintime/issues/1337))

### Não categorizado

- GUI Alterar: Remover Exit Botão de the toolbar ([#172](https://github.com/bit-team/backintime/issues/172))
- GUI Alterar: Define accelerator keys for menu bar and tabs, bem como toolbar shortcuts ([#1104](https://github.com/bit-team/backintime/issues/1104))
- Integração com o Desktop: Atualizar .Desktop Arquivo para mark Back In Tempo as a single main Janela program ([#1258](https://github.com/bit-team/backintime/issues/1258))
- Atualização da documentação: Correto description of Perfil<N>.Agendamento.Tempo in backintime-config manpage ([#1270](https://github.com/bit-team/backintime/issues/1270))
- Atualização da tradução: Brazilian Portuguese ([#1267](https://github.com/bit-team/backintime/issues/1267))
- Atualização da tradução: Italian ([#1110](https://github.com/bit-team/backintime/issues/1110), [#1123](https://github.com/bit-team/backintime/issues/1123))
- Atualização da tradução: French ([#1077](https://github.com/bit-team/backintime/issues/1077))
- Testes: Corrigir a Teste fail when dealing com an empty crontab ([#1181](https://github.com/bit-team/backintime/issues/1181))
- Testes: Corrigir a Teste fail when dealing com an empty config Arquivo ([#1305](https://github.com/bit-team/backintime/issues/1305))
- Testes: Skip "Teste_quiet_mode" (não funciona reliably)
- Testes: Melhorar "Teste_diagnostics_arg" (introduced com [#1100](https://github.com/bit-team/backintime/issues/1100)) para não mais fail 
- Testes: Diversas correções e extensões nos testes ([#1115](https://github.com/bit-team/backintime/issues/1115), [#1213](https://github.com/bit-team/backintime/issues/1213), [#1279](https://github.com/bit-team/backintime/issues/1279), [#1280](https://github.com/bit-team/backintime/issues/1280), [#1281](https://github.com/bit-team/backintime/issues/1281), [#1285](https://github.com/bit-team/backintime/issues/1285), [#1288](https://github.com/bit-team/backintime/issues/1288), [#1290](https://github.com/bit-team/backintime/issues/1290), [#1293](https://github.com/bit-team/backintime/issues/1293), [#1309](https://github.com/bit-team/backintime/issues/1309), [#1334](https://github.com/bit-team/backintime/issues/1334))

### Corrigido

- RTE "reentrant call inside io.BufferedWriter" in logFile.flush() durante Backup ([#1003](https://github.com/bit-team/backintime/issues/1003))
- Incompatibilidade com rsync 3.2.4 or later por causa de rsync's "Novo argument protection" ([#1247](https://github.com/bit-team/backintime/issues/1247)). Deactivate "--Antigo-args" rsync argument earlier recommended para Usuários as a workaround.
- Avisos de descontinuação about invalid escape sequences.
- AttributeError in "Diff Options" Diálogo ([#898](https://github.com/bit-team/backintime/issues/898))
- GUI de configurações: "Salvar Senha para Chaveiro" was Desativado devido a "no appropriate Chaveiro found" ([#1321](https://github.com/bit-team/backintime/issues/1321))
- Back In Tempo não iniciou com D-Bus Erro   
- Evitar registrar erros while waiting for a target drive para be mounted ([#1142](https://github.com/bit-team/backintime/issues/1142), [#1143](https://github.com/bit-team/backintime/issues/1143), [#1328](https://github.com/bit-team/backintime/issues/1328))
- [Arch Linux] AUR pkg "backintime-git": Build Testes fails and Instalação is aborted ([#1233](https://github.com/bit-team/backintime/issues/1233), fixed com [#921](https://github.com/bit-team/backintime/issues/921))
- Ícone incorreto da bandeja do sistema showing in Wayland ([#1244](https://github.com/bit-team/backintime/issues/1244))

## [1.3.2] (2022-03-12)

### Corrigido

- Os testes não funcionam mais com Python 3.10 ([#1175](https://github.com/bit-team/backintime/issues/1175))

## [1.3.1] (2021-07-05)

### Não categorizado

- bump Versão, forgot para push branch para Github antes releasing

## [1.3.0] (2021-07-04)

### Não categorizado

- Mesclar PR: Corrigir FileNotFoundError exception in Montagem.mounted, Obrigado tatokis ([PR #1157](https://github.com/bit-team/backintime/pull/1157))
- Mesclar PR: qt/plugins/notifyplugin: Corrigir setting self.Usuário, not Local variable, Obrigado Zocker1999NET ([PR #1155](https://github.com/bit-team/backintime/pull/1155))
- Mesclar PR: Usar Link Color em vez de lightGray as not para break theming, Obrigado newhinton ([PR #1153](https://github.com/bit-team/backintime/pull/1153))
- Mesclar PR: Match Antigo and Novo rsync Versão format, Obrigado TheTimeWalker ([PR #1139](https://github.com/bit-team/backintime/pull/1139))
- Mesclar PR: 'TempPasswordThread' object has no attribute 'isAlive', Obrigado FMeinicke ([PR #1135](https://github.com/bit-team/backintime/pull/1135))
- Mesclar PR: Keep Permissões of an existing Ponto de montagem de being overridden, Obrigado bentolor ([PR #1058](https://github.com/bit-team/backintime/pull/1058))

### Corrigido

- YEAR ausente na configuração ([#1023](https://github.com/bit-team/backintime/issues/1023))
- SSH module didn't send identification string while checking if host remoto is Disponível ([#1030](https://github.com/bit-team/backintime/issues/1030))

## [1.2.1] (2019-08-25)

### Corrigido

- TypeError in backintime.py if Montagem failed while running a Snapshot ([#1005](https://github.com/bit-team/backintime/issues/1005))

## [1.2.0] (2019-04-27)

### Corrigido

- O código de saída está associado à mensagem de status errada ([#906](https://github.com/bit-team/backintime/issues/906))
- AppName exibia 'python3' em vez de 'Back In Tempo' ([#950](https://github.com/bit-team/backintime/issues/950))
- a cifra configurada não é usada com Todos ssh-commands ([#934](https://github.com/bit-team/backintime/issues/934))
- 'make Teste' fails because Local SSH server is running on non-standard port ([#945](https://github.com/bit-team/backintime/issues/945))
- 23:00 está ausente in the Listar of every day hours ([#736](https://github.com/bit-team/backintime/issues/736))
- ssh-agent output changed ([#840](https://github.com/bit-team/backintime/issues/840))
- exception on making backintime Pasta world writable ([#812](https://github.com/bit-team/backintime/issues/812))
- stat Espaço livre for Snapshot Pasta em vez de backintime Pasta ([#733](https://github.com/bit-team/backintime/issues/733))
- backintime root crontab doesn't Executar; Ausente line-feed 0x0A on Último line ([#781](https://github.com/bit-team/backintime/issues/781))
- IndexError in inhibitSuspend ([#772](https://github.com/bit-team/backintime/issues/772))
- polkit CheckAuthorization: race condition in Privilégio authorization ([CVE-2017-7572](https://www.cve.org/CVERecord?id=CVE-2017-7572))
- OSError when running Backup-job de systemd ([#720](https://github.com/bit-team/backintime/issues/720))
- Restaurar filesystem-root sem 'Full rsync mode' com ACL and/or xargs activated broke whole Sistema ([#708](https://github.com/bit-team/backintime/issues/708))
- Usar Atual Pasta se não houver Arquivo is selected in Arquivos view ([#687](https://github.com/bit-team/backintime/issues/687), [#685](https://github.com/bit-team/backintime/issues/685))
- don't reload Perfil depois editing Perfil Nome ([#706](https://github.com/bit-team/backintime/issues/706))
- Exception in FileInfo
- falhou ao Restaurar suid Permissões ([#661](https://github.com/bit-team/backintime/issues/661))
- on remount Usuário-callback got called depois trying para Montagem ([#654](https://github.com/bit-team/backintime/issues/654))
- confirm Restaurar Diálogo has no scroll bar ([#625](https://github.com/bit-team/backintime/issues/625))
- Padrão_EXCLUDE not deletable ([#634](https://github.com/bit-team/backintime/issues/634))
- GUI barra de status unreadable ([#612](https://github.com/bit-team/backintime/issues/612))
- udev Agendamento not working ([#605](https://github.com/bit-team/backintime/issues/605))
- decode Caminho spooled de /etc/mtab ([PR #607](https://github.com/bit-team/backintime/pull/607))
- in Snapshots.py, gives Mais helpful advice if a lock Arquivo is present that shouldn't be.  ([#601](https://github.com/bit-team/backintime/issues/601))
- Fail para Criar Remoto Snapshot Caminho com spaces ([#567](https://github.com/bit-team/backintime/issues/567))
- broken Novo_Snapshot can Executar into infinite saveToContinue loop ([#583](https://github.com/bit-team/backintime/issues/583))
- udev Agendamento didn't work com LUKS Criptografado drives ([#466](https://github.com/bit-team/backintime/issues/466))
- sshMaxArg failed on none Padrão ssh port ([#581](https://github.com/bit-team/backintime/issues/581))
- failed if host remoto send SSH banner ([#581](https://github.com/bit-team/backintime/issues/581))
- incorrect handling of IPv6 addresses ([#577](https://github.com/bit-team/backintime/issues/577))
- Snapshot Log View freeze on big Log Arquivos ([#456](https://github.com/bit-team/backintime/issues/456))
- 'inotify_Adicionar_watch failed: Arquivo or Diretório não encontrado' depois deleting Snapshot
- a continued Snapshot não foi incremental ([#557](https://github.com/bit-team/backintime/issues/557))
- config Backup in Snapshot had nome incorreto if using --config option
- Não é possível abrir Arquivos com spaces in Nome ([#552](https://github.com/bit-team/backintime/issues/552))
- BIT-root won't Iniciar de .Desktop Arquivo ([#549](https://github.com/bit-team/backintime/issues/549))
- Chaveiro não funciona com KDE Plasma5 ([#545](https://github.com/bit-team/backintime/issues/545))
- Qt4 built-in phrases where not translated ([Debian#816197](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=816197))
- configure Ignorar unknown args ([#547](https://github.com/bit-team/backintime/issues/547))
- Snapshots-Listar on command-line não foi sorted
- SHA256 ssh-key fingerprint não foi detected
- Novo Snapshot did not Mostrar up depois finished
- TimeLine headers were not Correto
- wildcards ? and [] não foi recognized correctly
- Último char of Último element in tools.get_rsync_caps got cut off
- TypeError in tools.get_git_ref_hash
- don't include empty values in Listar ([#521](https://github.com/bit-team/backintime/issues/521))
- bash-completion não funciona for backintime-qt4
- 'make unittest' incorrectly used 'coverage' by Padrão ([#522](https://github.com/bit-team/backintime/issues/522))
- pm-utils is Obsoleto; Remover Dependência ([#519](https://github.com/bit-team/backintime/issues/519))

### Não categorizado

- minor changes para Permitir running BiT inside Docker ([PR #959](https://github.com/bit-team/backintime/pull/959))
- Remover progressbar on systray icon until BiT has it's own icon ([#902](https://github.com/bit-team/backintime/issues/902))
- clarify 'nocache' option ([#857](https://github.com/bit-team/backintime/issues/857))
- Criar a config-Backup in root dir if Backup is Criptografado ([#556](https://github.com/bit-team/backintime/issues/556))
- Mover progressbar under statusbar
- alleviate Padrão exclude [Tt]rash* ([#759](https://github.com/bit-team/backintime/issues/759))
- Ativar high DPI scaling ([#732](https://github.com/bit-team/backintime/issues/732))
- Smart Remover try para keep healthy Snapshots ([#703](https://github.com/bit-team/backintime/issues/703))
- ask for Restaurar-para Caminho antes confirm ([#678](https://github.com/bit-team/backintime/issues/678))
- Corrigir 'Back in Tempo (root)' on wayland ([#640](https://github.com/bit-team/backintime/issues/640))
- sort int values in config numerical instead if alphabetical ([#175](https://github.com/bit-team/backintime/issues/175)#issuecomment-272941811)
- set timestamp directly depois Novo Snapshot ([#584](https://github.com/bit-team/backintime/issues/584))
- Adicionar shortcut CTRL+H for toggle Mostrar arquivos ocultos para fileselect Diálogo ([#378](https://github.com/bit-team/backintime/issues/378))
- redesign Restaurar menu ([#661](https://github.com/bit-team/backintime/issues/661))
- Adicionar ability para Desativar SSH command- and ping-Verificar ([#647](https://github.com/bit-team/backintime/issues/647))
- Ativar bwlimit for Local Perfis ([#646](https://github.com/bit-team/backintime/issues/646))
- import host remoto-key into known_hosts de Configurações
- Copiar public SSH key para host remoto de Configurações
- Criar a Novo SSH key de Configurações
- rename debian Pacote de backintime-qt4 into backintime-qt
- rename paths and methods de *qt4* into *qt*
- rename executable backintime-qt4 into backintime-qt
- Novo config Versão 6, rename qt4 keys into qt, Adicionar Novo domain for Agendamento
- Verificar crontab entries on every GUI startup ([#129](https://github.com/bit-team/backintime/issues/129))
- Iniciar a Novo ssh-agent instance somente se necessary
- Adicionar cli command 'Desligamento' ([#596](https://github.com/bit-team/backintime/issues/596))
- make LogView and Configurações Diálogo non-modal ([#608](https://github.com/bit-team/backintime/issues/608))
- port para Qt5/pyqt5 ([#518](https://github.com/bit-team/backintime/issues/518))
- Recognize changes on Anterior runs while continuing Novo Snapshots
- Adicionar pause, resume and Parar function for running Snapshots ([#474](https://github.com/bit-team/backintime/issues/474), [#195](https://github.com/bit-team/backintime/issues/195))
- Usar rsync para Salvar Permissões
- Substituir os.Sistema calls com subprocess.Popen
- Automaticamente refresh Log view if a Snapshot is currently running
- make full-rsync mode Padrão, Remover the Outro mode
- Usar rsync para Remover Snapshots which will give a nice speedup ([#151](https://github.com/bit-team/backintime/issues/151))
- Abrir temporary Local Copiar of Arquivos em vez de original Backup on double-click in GUI
- Abrir Atual Log directly de systray icon durante Ao criar um Snapshot
- Usar Monospace font in logview
- Corrigir lintian Aviso: manpage-has-Erros-de-man: bad argument Nome 'P'
- Do not print 'SnapshotID' or 'SnapshotPath' if running 'Snapshots-Listar' command (and Outro) com '--quiet'
- Remover Dependência 'ps'
- Reescrever huge parts of Snapshots.py

### Removido

- unused and undocumented userscript plugin
- Dependência for extended 'find' command on host remoto
- backwards compatibility para Versão < 1.0

### Adicionado

- contextmenu for logview Diálogo which can Copiar, exclude and decode lines
- 'Edit Usuário-callback' Diálogo
- cli command 'smart-Remover'
- option para decrypt paths in systray menu com mode ssh-Criptografado
- tool-tips para Restaurar menu
- --share-Caminho option
- Restaurar option --only-Novo
- Botão 'Take Snapshot com checksums'

### Alterado

- Padrão configure option para --no-fuse-Grupo as Ubuntu >= 12.04 don't need fuse Grupo-membership anymore

## [1.1.24] (2017-11-07)

### Corrigido

- shell injection in notify-send ([#834](https://github.com/bit-team/backintime/issues/834), [CVE-2017-16667](https://www.cve.org/CVERecord?id=CVE-2017-16667))

## [1.1.22] (2017-10-28)

### Corrigido

- stat Espaço livre for Snapshot Pasta em vez de backintime Pasta ([#733](https://github.com/bit-team/backintime/issues/733))
- backintime root crontab doesn't Executar; Ausente line-feed 0x0A on Último line ([#781](https://github.com/bit-team/backintime/issues/781))
- Não é possível abrir Arquivos com spaces in Nome ([#552](https://github.com/bit-team/backintime/issues/552))

## [1.1.20] (2017-04-09)

### Corrigido

- polkit CheckAuthorization: race condition in Privilégio authorization ([CVE-2017-7572](https://www.cve.org/CVERecord?id=CVE-2017-7572))

## [1.1.18] (2017-03-29)

### Corrigido

- Manual Snapshots de GUI didn't work ([#728](https://github.com/bit-team/backintime/issues/728))

## [1.1.16] (2017-03-28)

### Corrigido

- Iniciar a Novo ssh-agent instance somente se necessary ([#722](https://github.com/bit-team/backintime/issues/722))
- OSError when running Backup-job de systemd ([#720](https://github.com/bit-team/backintime/issues/720))

## [1.1.14] (2017-03-05)

### Corrigido

- udev Agendamento not working ([#605](https://github.com/bit-team/backintime/issues/605))
- Chaveiro não funciona com KDE Plasma5 ([#545](https://github.com/bit-team/backintime/issues/545))
- nameError in tools.make_dirs ([#622](https://github.com/bit-team/backintime/issues/622))
- Usar Atual Pasta se não houver Arquivo is selected in Arquivos view
- Restaurar filesystem-root sem 'Full rsync mode' com ACL and/or xargs activated broke whole Sistema ([#708](https://github.com/bit-team/backintime/issues/708))

## [1.1.12] (2016-01-11)

### Corrigido

- Remover x-terminal-emulator Dependência ([#515](https://github.com/bit-team/backintime/issues/515))
- AttributeError in About Diálogo ([#515](https://github.com/bit-team/backintime/issues/515))

## [1.1.10] (2016-01-09)

### Corrigido

- falhou ao Remover empty lock Arquivo ([#505](https://github.com/bit-team/backintime/issues/505))
- Restaurar the Correto Arquivo Proprietário and Grupo fail if they não são present in Sistema ([#58](https://github.com/bit-team/backintime/issues/58))
- QObject::startTimer Erro on closing app
- FileNotFoundError while starting pw-cache de Origem
- suppress Aviso about failed inhibit Suspensão if Executar as root ([#500](https://github.com/bit-team/backintime/issues/500))
- UI blocked/grayed out while removing Snapshot ([#487](https://github.com/bit-team/backintime/issues/487))
- pw-cache failed on leftover PID Arquivo, using ApplicationInstance now ([#468](https://github.com/bit-team/backintime/issues/468))
- falhou ao parse Alguns arguments ([#492](https://github.com/bit-team/backintime/issues/492))
- falhou ao Iniciar GUI if launched de systray icon
- deleted Snapshot is still listed in Timeline if using mode SSH ([#493](https://github.com/bit-team/backintime/issues/493))
- PermissionError while deleting readonly Arquivos on sshfs mounted share ([#490](https://github.com/bit-team/backintime/issues/490))
- Criar Novo Criptografado Perfis com encfs >= 1.8.0 failed ([#477](https://github.com/bit-team/backintime/issues/477))
- AttributeError in common/tools.py if Chaveiro está ausente ([#473](https://github.com/bit-team/backintime/issues/473))
- Remoto rename of 'Novo_Snapshot' Pasta sometimes isn't recognized locally; rename Local now (https://answers.launchpad.net/questions/271792)

### Não categorizado

- Adicionar Icon 'Mostrar-hidden' ([#507](https://github.com/bit-team/backintime/issues/507))
- subclass ApplicationInstance in GUIApplicationInstance para reduce redundant code
- speed up app Iniciar by adding Snapshots para timeline in Segundo plano thread
- Adicionar Aviso on failed Permissão Restaurar ([#58](https://github.com/bit-team/backintime/issues/58))
- continue an unfinished Novo_Snapshot if possible ([#400](https://github.com/bit-team/backintime/issues/400))
- Adicionar Nautilus-like shortcuts for navigating in Arquivo browser ([#483](https://github.com/bit-team/backintime/issues/483))
- speed up mounting of SSH+Criptografado Perfis
- Mover Origem code and bug tracking para GitHub

### Adicionado

- Modify for Full Sistema Backup Botão para Configurações page, para Alterar Alguns Perfil Configurações
- get|set_Listar_value para configfile
- unittest (Obrigado para Dorian, Alexandre, Aurélien and Gregory de IAGL)

## [1.1.8] (2015-09-28)

### Corrigido

- unlock private SSH key Executar into 5sec timeout if Senha is empty
- BiT freeze when activate 'Decode Caminho' in 'Snapshot Log View'
- empty gray Janela appears when starting the gui as root ([Launchpad#1493020](https://bugs.launchpad.net/backintime/+bug/1493020))
- gnu_find_suffix_Suporte doesn't set back para True ([Launchpad#1487781](https://bugs.launchpad.net/backintime/+bug/1487781))
- lintian Aviso dbus-policy-sem-send-Destino
- dbus exception if dbus systembus não é running
- depend on virtual Pacote cron-daemon em vez de cron for compatibility com Outro cron implementations ([Debian#776856](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=776856))
- não foi able para Iniciar de alternate Instalar dir ([Launchpad#478689](https://bugs.launchpad.net/backintime/+bug/478689))
- não foi able para Iniciar de Origem dir
- 'Inhibit Suspensão' fails com 'org.freedesktop.PowerManagement.Inhibit' ([Launchpad#1485242](https://bugs.launchpad.net/backintime/+bug/1485242))
- No mounting while selecting a secondary Perfil in the gui ([Launchpad#1481267](https://bugs.launchpad.net/backintime/+bug/1481267))
- Corrigir for bug [Launchpad#1419466](https://bugs.launchpad.net/backintime/+bug/1419466) broke crontab on Slackware
- Corrigir for bug [Launchpad#1431305](https://bugs.launchpad.net/backintime/+bug/1431305) broke pw-cache on Ubuntu
- bash-complete
- Configurações accepted empty strings for Host/Usuário/Perfil-ID ([Launchpad#1477733](https://bugs.launchpad.net/backintime/+bug/1477733))
- IndexError on 'Verificar_Remoto_commands' devido a too long args ([Launchpad#1471930](https://bugs.launchpad.net/backintime/+bug/1471930))
- Makefile has no uninstall target ([Launchpad#1469152](https://bugs.launchpad.net/backintime/+bug/1469152))

### Não categorizado

- Mostrar Atual app Nome and Perfil ID in syslog ([Launchpad#906213](https://bugs.launchpad.net/backintime/+bug/906213))
- Mostrar 'Perfis' dropdown only in 'Último Log Viewer', Adicionar 'Snapshots' dropdown in 'Snapshot Log Viewer' ([Launchpad#1478219](https://bugs.launchpad.net/backintime/+bug/1478219))
- do not Restaurar Permissão if they are identical com Atual Permissões
- Segurança issue: do not Executar Usuário-callback in a shell
- apply timestamps-in-gzip.patch de Debian backintime/1.1.6-1 Pacote
- Executar multiple smart-Remover jobs in one screen session ([Launchpad#1487781](https://bugs.launchpad.net/backintime/+bug/1487781))
- Usar native Python code para Verificar Ponto de montagem
- Adicionar expert option for stdout and stderr redirection in cronjobs (https://answers.launchpad.net/questions/270105)
- Mostrar 'man backintime' on Help; Remover link para backintime.le-web.org ([Launchpad#1475995](https://bugs.launchpad.net/backintime/+bug/1475995))
- Adicionar --Local-Backup, --no-Local-Backup and --Excluir option para Restaurar on command-line ([Launchpad#1467239](https://bugs.launchpad.net/backintime/+bug/1467239))
- Reescrever command-line argument parsing. Now using argparse

### Adicionado

- option para not Log Usuário-callback output
- Erro Mensagens if PID Arquivo creation fail
- Aviso about unsupported filesystems
- --debug argument
- 'Backup on Restaurar' option para confirm Diálogo
- Verificar-config command for command-line
- expert option SSH command prefix

### Removido

- shebang in common/askpass.py and common/Criar-manpage-backintime-config.py

## [1.1.6] (2015-06-27)

### Não categorizado

- Mostrar Perfil Nome in systrayicon menu
- make own Exceptions a childclass de BackInTimeException
- Specifying the SSH private key whenever ssh is called ([Launchpad#1433682](https://bugs.launchpad.net/backintime/+bug/1433682))
- Adicionar para in-/exclude directly de mainwindow ([Launchpad#1454856](https://bugs.launchpad.net/backintime/+bug/1454856))
- Adicionar option para Executar Smart Remover in Segundo plano on host remoto ([Launchpad#1457210](https://bugs.launchpad.net/backintime/+bug/1457210))
- Usar Atual Perfil when starting GUI de Systray

### Corrigido

- Criptografado Remoto Backup hangs on 'Iniciar encfsctl encode Processo' ([Launchpad#1455925](https://bugs.launchpad.net/backintime/+bug/1455925))
- Ausente Perfil<N>.Nome crashed GUI
- Segmentation fault caused by two QApplication instances ([Launchpad#1463732](https://bugs.launchpad.net/backintime/+bug/1463732))
- no Changes [C] Log entries com 'Verificar for changes' Desativado ([Launchpad#1463367](https://bugs.launchpad.net/backintime/+bug/1463367))
- Alguns changed options de Settingsdialog where not respected durante Automático Testes depois hitting OK
- python Versão Verificar fails on python 3.3 ([Launchpad#1463686](https://bugs.launchpad.net/backintime/+bug/1463686))
- pw-cache didn't Iniciar on Mint KDE por causa de Ausente stdout and stderr ([Launchpad#1431305](https://bugs.launchpad.net/backintime/+bug/1431305))
- falhou ao Restaurar Arquivo names com white spaces using CLI ([Launchpad#1435602](https://bugs.launchpad.net/backintime/+bug/1435602))
- UnboundLocalError com 'Último_Snapshot' in _free_space ([Launchpad#1437623](https://bugs.launchpad.net/backintime/+bug/1437623))

### Removido

- consolekit de Dependências

## [1.1.4] (2015-03-22)

### Não categorizado

- Adicionar option para keep Novo Snapshot com 'full rsync mode' regardless of changes ([Launchpad#1434722](https://bugs.launchpad.net/backintime/+bug/1434722))
- Remover base64 encoding for Senhas as it doesn't Adicionar any Segurança but broke the Senha Processo ([Launchpad#1431305](https://bugs.launchpad.net/backintime/+bug/1431305))
- Adicionar confirm Diálogo antes restoring ([Launchpad#438079](https://bugs.launchpad.net/backintime/+bug/438079))
- cache uuid in config so it doesn't fail se o device isn't plugged in ([Launchpad#1426881](https://bugs.launchpad.net/backintime/+bug/1426881))
- Impedir Snapshots de being removed com Restaurar and Excluir; Mostrar Aviso if Restaurar and Excluir filesystem root (https://answers.launchpad.net/questions/262837)
- Usar 'crontab' em vez de 'crontab -' para read de stdin ([Launchpad#1419466](https://bugs.launchpad.net/backintime/+bug/1419466))

### Corrigido

- Incorreto quote in 'Salvar config Arquivo'
- Deleting the Último Snapshot does not Atualizar the Último_Snapshot symlink ([Launchpad#1434724](https://bugs.launchpad.net/backintime/+bug/1434724))
- Incorreto status text in the tray icon ([Launchpad#1429400](https://bugs.launchpad.net/backintime/+bug/1429400))
- Restaurar Permissões of lots of Arquivos made BackInTime unresponsive ([Launchpad#1428423](https://bugs.launchpad.net/backintime/+bug/1428423))
- falhou ao Restaurar Arquivo Proprietário and Grupo
- OSError in free_space; Adicionar alternate method para get Espaço livre
- ugly theme while running as root on Gnome based DEs ([Launchpad#1418447](https://bugs.launchpad.net/backintime/+bug/1418447))
- UnicodeError thrown if filename has broken charset ([Launchpad#1419694](https://bugs.launchpad.net/backintime/+bug/1419694))

### Adicionado

- option para Executar only one Snapshot at a Tempo
- Aviso about Incorreto Python Versão in configure
- bash-completion

## [1.1.2] (2015-02-04)

### Não categorizado

- sort 'Backup Pastas' in main Janela
- Salvar in- and exclude sort order
- Usar PolicyKit para Instalar Udev rules
- Mover compression de Instalar para Build in Makefiles
- Usar pkexec para Iniciar backintime-qt4 as root

## [1.1.0] (2015-01-15)

### Adicionado

- tooltips for rsync options
- Mais Usuário-callback events (on App Iniciar and exit, on Montagem and Desmontagem)
- context menu para Arquivos view
- Mais Padrão exclude; Remover [Cc]ache* de exclude
- option for custom rsync-options
- ProgressBar for rsync
- progress for smart-Remover
- --gksu/--gksudo arg para qt4/configure

### Não categorizado

- make only one debian/control
- multiselect Arquivos para Restaurar ([Launchpad#1135886](https://bugs.launchpad.net/backintime/+bug/1135886))
- force Executar Manual Snapshots on battery ([Launchpad#861553](https://bugs.launchpad.net/backintime/+bug/861553))
- Backup encfs config para Local config Pasta
- apply 'Instalar-docs-Mover.patch' de Debian Pacote by Jonathan Wiltshire
- Adicionar Restaurar option para Excluir Novo Arquivos durante Restaurar ([Launchpad#1371951](https://bugs.launchpad.net/backintime/+bug/1371951))
- Usar flock para Impedir two instances running at the same Tempo
- Restaurar config Diálogo added ([Launchpad#480391](https://bugs.launchpad.net/backintime/+bug/480391))
- inhibit Suspensão/Hibernação while take_Snapshot or Restaurar
- Usar Mais reliable code for get_Usuário
- implement anacrons functions inside BIT => Mais flexible Agendamentos and no Novo timestamp if there was an Erro
- Automaticamente Executar in Segundo plano if started com 'backintime --Backup-job'
- Corrigir typos and style Avisos in manpages reported by Lintian (https://lintian.debian.org/full/jmw@debian.org.html#backintime_1.0.34-0.1)
- Adicionar exclude Arquivos by Tamanho ([Launchpad#823719](https://bugs.launchpad.net/backintime/+bug/823719))
- optional Executar 'rsync' com 'nocache' ([Launchpad#1344528](https://bugs.launchpad.net/backintime/+bug/1344528))
- mark invalid exclude pattern com mode ssh-Criptografado
- make Settingsdialog tabs scrollable
- Remover colon (: ) restriction in exclude pattern
- Impedir starting Novo Snapshot if Restaurar is running
- Adicionar top-level Diretório for tarball ([Launchpad#1359076](https://bugs.launchpad.net/backintime/+bug/1359076))
- multi selection in timeline => Remover multiple Snapshots com one click
- print Aviso if started com sudo
- ask para include symlinks target instead link ([Launchpad#1117709](https://bugs.launchpad.net/backintime/+bug/1117709))
- port para Python 3.x
- returncode >0 if there was an Erro ([Launchpad#1040995](https://bugs.launchpad.net/backintime/+bug/1040995))
- Ativar Usuário-callback script para cancel a Backup by returning a non-zero exit code.
- merge backintime-notify into backintime-qt4
- Lembrar Último Caminho for each Perfil ([Launchpad#1254870](https://bugs.launchpad.net/backintime/+bug/1254870))
- sort include and exclude Listar ([Launchpad#1193149](https://bugs.launchpad.net/backintime/+bug/1193149))
- Timeline Mostrar tooltip 'Último Verificar'
- Mostrar arquivos ocultos in FileDialog ([Launchpad#995925](https://bugs.launchpad.net/backintime/+bug/995925))
- Adicionar Botão text for Todos Botões ([Launchpad#992020](https://bugs.launchpad.net/backintime/+bug/992020))
- Adicionar shortcuts ([Launchpad#686694](https://bugs.launchpad.net/backintime/+bug/686694))
- Adicionar menubar ([Launchpad#528851](https://bugs.launchpad.net/backintime/+bug/528851))
- port KDE4 GUI para pure Qt4 para Substituir both KDE4 and Gnome GUI

### Removido

- 'Auto Host/Usuário/Perfil-ID' as this is Mais confusing than helping
- Snapshots de commandline
- Antigo status-bar Mensagem depois a Snapshot crashed.

### Corrigido

- Verificar procname of pid-locks ([Launchpad#1341414](https://bugs.launchpad.net/backintime/+bug/1341414))
- Port Verificar failed on IPv6 ([Launchpad#1361634](https://bugs.launchpad.net/backintime/+bug/1361634))
- 'inotify_Adicionar_watch failed' while closing BIT
- systray icon didn't Mostrar up ([Launchpad#658424](https://bugs.launchpad.net/backintime/+bug/658424))

## [1.0.40] (2014-11-02)

### Não categorizado

- Usar fingerprint para Verificar if ssh key was unlocked correctly (https://answers.launchpad.net/questions/256408)
- Adicionar Alternativa method para get UUID (https://answers.launchpad.net/questions/254140)

### Corrigido

- 'Attempt para unlock mutex that não foi locked'... this Tempo for good

## [1.0.38] (2014-10-01)

### Corrigido

- 'Attempt para unlock mutex that não foi locked' in gnomeplugin (https://answers.launchpad.net/questions/255225)
- housekeeping by gnome-session-daemon might Excluir Backup and original data ([Launchpad#1374343](https://bugs.launchpad.net/backintime/+bug/1374343))
- Type Erro in 'backintime --decode' ([Launchpad#1365072](https://bugs.launchpad.net/backintime/+bug/1365072))
- take_Snapshot didn't wait for Snapshot Pasta come Disponível if notifications are Desativado ([Launchpad#1332979](https://bugs.launchpad.net/backintime/+bug/1332979))

### Não categorizado

- compare os.Caminho.realpath em vez de os.stat para get devices UUID

## [1.0.36] (2014-08-06)

### Não categorizado

- Remover UbuntuOne de exclude ([Launchpad#1340131](https://bugs.launchpad.net/backintime/+bug/1340131))
- Gray out 'Adicionar Perfil' if 'Main Perfil' isn't configured yet ([Launchpad#1335545](https://bugs.launchpad.net/backintime/+bug/1335545))
- Don't Verificar for fuse Grupo-membership if Grupo doesn't exist
- Desativar Chaveiro for root

### Corrigido

- backintime-kde4 as root falhou ao load ssh-key ([Launchpad#1276348](https://bugs.launchpad.net/backintime/+bug/1276348))
- kdesystrayicon.py Travamentos por causa de Ausente environ ([Launchpad#1332126](https://bugs.launchpad.net/backintime/+bug/1332126))
- OSError if sshfs/encfs não é installed ([Launchpad#1316288](https://bugs.launchpad.net/backintime/+bug/1316288))
- TypeError in config.py Verificar_config() (https://bugzilla.redhat.com/show_bug.cgi?id=1091644)
- unhandled exception in Criar_Último_Snapshot_symlink() ([Launchpad#1269991](https://bugs.launchpad.net/backintime/+bug/1269991))

## [1.0.34] (2013-12-21)

### Não categorizado

- sync/flush Todos disks antes Desligamento ([Launchpad#1261031](https://bugs.launchpad.net/backintime/+bug/1261031))

### Corrigido

- BIT running as root Desligamento depois Snapshot, regardless of option checked ([Launchpad#1261022](https://bugs.launchpad.net/backintime/+bug/1261022))

## [1.0.32] (2013-12-13)

### Corrigido

- cron scheduled Snapshots won't Iniciar com 1.0.30

## [1.0.30] (2013-12-12)

### Não categorizado

- scheduled and Manual Snapshots Usar --config
- make configure scripts portable ([Launchpad#377429](https://bugs.launchpad.net/backintime/+bug/377429))
- Adicionar symlink Último_Snapshot ([Launchpad#787118](https://bugs.launchpad.net/backintime/+bug/787118))
- Adicionar option para Executar rsync com 'nice' or 'ionice' on host remoto ([Launchpad#1240301](https://bugs.launchpad.net/backintime/+bug/1240301))
- Adicionar Desligamento Botão para Desligamento Sistema depois Snapshot has finished ([Launchpad#838742](https://bugs.launchpad.net/backintime/+bug/838742))
- wrap long lines for syslog

### Corrigido

- udev rule doesn't finish ([Launchpad#1249466](https://bugs.launchpad.net/backintime/+bug/1249466))
- multiple Erros in PPA Build Processo; reorganize updateversion.sh
- Mate and xfce Desktop didn't Mostrar systray icon ([Launchpad#658424](https://bugs.launchpad.net/backintime/+bug/658424)/comments/31)
- Ubuntu Lucid doesn't provide SecretServiceKeyring ([Launchpad#1243911](https://bugs.launchpad.net/backintime/+bug/1243911))
- 'gksu backintime-gnome' failed com dbus.exceptions.DBusException

### Adicionado

- virtual Pacote backintime-kde for PPA

## [1.0.28] (2013-10-19)

### Removido

- config on 'apt-get purge'

### Adicionado

- Mais options for configure scripts; Atualizar README
- udev Agendamento (Executar BIT as soon as the drive is connected)

### Corrigido

- AttributeError com python-Chaveiro>1.6.1 ([Launchpad#1234024](https://bugs.launchpad.net/backintime/+bug/1234024))
- TypeError: KDirModel.removeColumns() is a private method in kde4/app.py ([Launchpad#1232694](https://bugs.launchpad.net/backintime/+bug/1232694))
- sshfs Montagem disconnect depois a while devido a Alguns firewalls (Adicionar ServerAliveInterval) (https://answers.launchpad.net/backintime/+question/235685)
- Ping fails if ICMP is Desativado on host remoto ([Launchpad#1226718](https://bugs.launchpad.net/backintime/+bug/1226718))
- KeyError in getgrnam if there is no 'fuse' Grupo ([Launchpad#1225561](https://bugs.launchpad.net/backintime/+bug/1225561))
- anacrontab won't work com profilename com spaces ([Launchpad#1224620](https://bugs.launchpad.net/backintime/+bug/1224620))
- NameError in tools.Mover_Snapshots_Pasta ([Launchpad#871466](https://bugs.launchpad.net/backintime/+bug/871466))
- KPassivePopup não é defined ([Launchpad#871475](https://bugs.launchpad.net/backintime/+bug/871475))
- ValueError while reading pw-cache PID (https://answers.launchpad.net/backintime/+question/235407)

### Não categorizado

- Adicionar '--checksum' commandline option ([Launchpad#886021](https://bugs.launchpad.net/backintime/+bug/886021))
- multi selection for include and exclude Listar ([Launchpad#660753](https://bugs.launchpad.net/backintime/+bug/660753))

## [1.0.26] (2013-09-07)

### Não categorizado

- Adicionar feature: keep min Inodes livres
- roll back commit 836.1.5 (Verificar free-space on ssh host remoto): statvfs DOES work over sshfs. But not com quite outdated sshd
- Adicionar feature: Restaurar de command line; Adicionar option --config
- Usar 'ps ax' para Verificar if 'backintime --pw-cache' is still running
- Montagem depois locking, Desmontagem antes unlocking in take_Snapshot
- redirect logger.Erro and .Aviso para stderr; Novo argument --quiet
- deactivate 'Salvar Senha' se não houver Chaveiro is Disponível
- Usar Senha-cache for Usuário-input too
- Tratar two Senhas
- Adicionar 'SSH Criptografado': Montagem / com encfs reverse and sync Criptografado com rsync. Experimental!
- Adicionar 'Local Criptografado': Montagem encfs

### Adicionado

- daily anacron Agendamento
- Excluir Botão and 'Listar only equal' in Snapshot Diálogo; multiSelect in Snapshot Listar
- manpage backintime-config and config-examples
- option --bwlimit for rsync

### Corrigido

- Restaurar makes Arquivos public durante the operation
- Cannot keep modifications para cron ([Launchpad#698106](https://bugs.launchpad.net/backintime/+bug/698106))
- cannot stat 'backintime-kde4-root.Desktop.kdesudo' ([Launchpad#696659](https://bugs.launchpad.net/backintime/+bug/696659))
- unreadable dark KDE color schemes ([Launchpad#1184920](https://bugs.launchpad.net/backintime/+bug/1184920))
- Permissão denied if Remoto uid não foi the same as Local uid

## [1.0.24] (2013-05-08)

### Não categorizado

- hide Verificar_for_canges if full_rsync_mode is checked
- Padrão_EXCLUDE Sistema Pastas com /foo/* so pelo menos the Pasta itself will Backup
- Padrão_EXCLUDE /Executar; exclude Montagem_ROOT com higher priority and not com Padrão_EXCLUDE anymore
- 'Salvar Senha' Padrão off para evitar problems com existing Perfis
- if Restaurar uid/gid failed try para Restaurar pelo menos gid
- SSH need para store Permissões in separate Arquivo com "Full rsync mode" because Remoto Usuário might not be able para store Propriedade
- switch para 'find -exec cmd {} +' ([Launchpad#1157639](https://bugs.launchpad.net/backintime/+bug/1157639))

### Corrigido

- 'CalledProcessError' object has no attribute 'strerror'
- quote rsync Remoto Caminho com spaces
- Restaurar Permissão failed on "Full rsync mode"
- glib.GError: Unknown internal child: selection
- GtkWarning: Unknown property: GtkLabel.margin-top
- Verificar Chaveiro backend somente se Senha is needed

### Alterado

- Todos indent tabs para 4 spaces

## [1.0.22] (2013-03-26)

### Não categorizado

- Verificar free-space on ssh host remoto (statvfs didn't work over sshfs)

### Adicionado

- Senha storage mode ssh
- "Full rsync mode" (can be faster but ...)

### Corrigido

- "Restaurar para..." failed devido a spaces in Diretório Nome ([Launchpad#1096319](https://bugs.launchpad.net/backintime/+bug/1096319))
- host não encontrado in known_hosts if port != 22 ([Launchpad#1130356](https://bugs.launchpad.net/backintime/+bug/1130356))
- sshtools.py used not POSIX conform conditionals

## [1.0.20] (2012-12-15)

### Corrigido

- Restaurar Remoto Caminho com spaces using mode ssh returned Erro

## [1.0.18] (2012-11-17)

### Não categorizado

- Corrigir Pacotes: man & Traduções
- Map multiple arguments for gettext so they can be rearranged by translators

### Corrigido

- [Launchpad#1077446](https://bugs.launchpad.net/backintime/+bug/1077446)
- [Launchpad#1078979](https://bugs.launchpad.net/backintime/+bug/1078979)
- [Launchpad#1079479](https://bugs.launchpad.net/backintime/+bug/1079479)

## [1.0.16] (2012-11-15)

### Não categorizado

- Corrigir a Pacote Dependência problem ... this Tempo for good ([Launchpad#1077446](https://bugs.launchpad.net/backintime/+bug/1077446))

## [1.0.14] (2012-11-09)

### Corrigido

- a Pacote Dependência problem

## [1.0.12] (2012-11-08)

### Não categorizado

- Adicionar links para: Site, Documentação, Relatar a bug, answers, faq
- Usar libnotify for gnome/kde4 notifications em vez de gnome specific libraries
- Adicionar Mais Agendamento options: every 30 min, every 2 hours, every 4 hours, every 6 hours & every 12 hours

### Corrigido

- [Launchpad#1059247](https://bugs.launchpad.net/backintime/+bug/1059247)
- caminho incorreto if Restaurar Sistema root
- glade (xml) Arquivos did not translate
- [Launchpad#1073867](https://bugs.launchpad.net/backintime/+bug/1073867)

### Adicionado

- generic Montagem-framework
- mode 'SSH' for Backups on host remoto using ssh protocol.

## [1.0.10] (2012-03-06)

### Adicionado

- "Restaurar para ..." in replacement of Copiar (com or sem drag & drop) because Copiar don't Restaurar Usuário/Grupo/rights

## [1.0.8] (2011-06-18)

### Corrigido

- [Launchpad#723545](https://bugs.launchpad.net/backintime/+bug/723545)
- [Launchpad#705237](https://bugs.launchpad.net/backintime/+bug/705237)
- [Launchpad#696663](https://bugs.launchpad.net/backintime/+bug/696663)
- [Launchpad#671946](https://bugs.launchpad.net/backintime/+bug/671946)

## [1.0.6] (2011-01-02)

### Corrigido

- [Launchpad#676223](https://bugs.launchpad.net/backintime/+bug/676223)
- [Launchpad#672705](https://bugs.launchpad.net/backintime/+bug/672705)

### Não categorizado

- Smart Remover: configurable options ([Launchpad#406765](https://bugs.launchpad.net/backintime/+bug/406765))

## [1.0.4] (2010-10-28)

### Não categorizado

- SettingsDialog: Mostrar highly recommended excludes
- Option para Usar checksum para Detectar changes ([Launchpad#666964](https://bugs.launchpad.net/backintime/+bug/666964))
- Option para select Log verbosity ([Launchpad#664423](https://bugs.launchpad.net/backintime/+bug/664423))
- Gnome: Usar gloobus-preview if installed

### Corrigido

- [Launchpad#664783](https://bugs.launchpad.net/backintime/+bug/664783)

## [1.0.2] (2010-10-16)

### Não categorizado

- reduce Log Arquivo (no Mais duplicate "Compare com..." lines)
- declare backintime-kde4 Pacotes as a replacement of backintime-kde

## [1.0] (2010-10-16)

### Não categorizado

- Adicionar '.dropbox*' para Padrão Padrões de exclusão ([Launchpad#628172](https://bugs.launchpad.net/backintime/+bug/628172))
- Adicionar option para take a Snapshot at every boot ([Launchpad#621810](https://bugs.launchpad.net/backintime/+bug/621810))
- Adicionar continue on Erros ([Launchpad#616299](https://bugs.launchpad.net/backintime/+bug/616299))
- Adicionar Opções avançadas: Copiar unsafe links & Copiar links
- "Usuário-callback" Substituir "Usuário.callback" and receive Perfil Informações
- Documentação: on-line only (easier para maintain)
- merge com: lp:~dave2010/backintime/minor-edits
- merge com: lp:~mcfonty/backintime/unique-Snapshots-view
- reduce memory usage durante compare com Anterior Snapshot Processo
- custom Backup hour (for daily Backups or mode): [Launchpad#507451](https://bugs.launchpad.net/backintime/+bug/507451)
- smart Remover was slightly changed ([Launchpad#502435](https://bugs.launchpad.net/backintime/+bug/502435))
- make Backup on Restaurar optional
- Corrigir bug that could cause "ghost" Pastas in Snapshots (LP: 406092)
- Corrigir bug that converted / into // ([Launchpad#455149](https://bugs.launchpad.net/backintime/+bug/455149))
- Remover "Agendamento per included Diretório" (Perfis do that) (+ bug [Launchpad#412470](https://bugs.launchpad.net/backintime/+bug/412470))
- fig bug: [Launchpad#489380](https://bugs.launchpad.net/backintime/+bug/489380)
- Atualizar Slovak Tradução (Tomáš Vadina <kyberdev@gmail.com>)
- multiple Perfis Suporte
- GNOME: Corrigir notification
- backintime Snapshot Pasta is restructured para ../backintime/machine/Usuário/Perfil_id/
- added a Desktop Arquivo for kdesu and a Teste if kdesu or kdesudo should be used ([Launchpad#389988](https://bugs.launchpad.net/backintime/+bug/389988))
- added expert option para Desativar Snapshots when on battery ([Launchpad#388178](https://bugs.launchpad.net/backintime/+bug/388178))
- Corrigir bug handling big Arquivos by the GNOME GUI ([Launchpad#409130](https://bugs.launchpad.net/backintime/+bug/409130))
- Corrigir bug in handling of & characters by GNOME GUI ([Launchpad#415848](https://bugs.launchpad.net/backintime/+bug/415848))
- Corrigir a Segurança bug in chmods antes Snapshot removal ([Launchpad#419774](https://bugs.launchpad.net/backintime/+bug/419774))
- Snapshots are stored entirely Somente leitura ([Launchpad#386275](https://bugs.launchpad.net/backintime/+bug/386275))
- Corrigir Padrões de exclusão in KDE4 ([Launchpad#432537](https://bugs.launchpad.net/backintime/+bug/432537))
- Corrigir opening german Arquivos com external Aplicativos in KDE ([Launchpad#404652](https://bugs.launchpad.net/backintime/+bug/404652))
- changed Padrão Padrões de exclusão para caches, thumbnails, trashbins, and Backups ([Launchpad#422132](https://bugs.launchpad.net/backintime/+bug/422132))
- write access para Snapshot Pasta is checked & Alterar para Snapshot Versão 2 ([Launchpad#423086](https://bugs.launchpad.net/backintime/+bug/423086))
- Corrigir small bugs (a.o. [Launchpad#474307](https://bugs.launchpad.net/backintime/+bug/474307))
- Used a Mais standard crontab syntax ([Launchpad#409783](https://bugs.launchpad.net/backintime/+bug/409783))
- Parar the "Over zealous removal of crontab entries" ([Launchpad#451811](https://bugs.launchpad.net/backintime/+bug/451811))

### Corrigido

- xattr
- [Launchpad#588841](https://bugs.launchpad.net/backintime/+bug/588841)
- [Launchpad#588215](https://bugs.launchpad.net/backintime/+bug/588215)
- [Launchpad#588393](https://bugs.launchpad.net/backintime/+bug/588393)
- [Launchpad#426400](https://bugs.launchpad.net/backintime/+bug/426400)
- [Launchpad#575022](https://bugs.launchpad.net/backintime/+bug/575022)
- [Launchpad#571894](https://bugs.launchpad.net/backintime/+bug/571894)
- [Launchpad#553441](https://bugs.launchpad.net/backintime/+bug/553441)
- [Launchpad#550765](https://bugs.launchpad.net/backintime/+bug/550765)
- [Launchpad#507246](https://bugs.launchpad.net/backintime/+bug/507246)
- [Launchpad#538855](https://bugs.launchpad.net/backintime/+bug/538855)
- [Launchpad#386230](https://bugs.launchpad.net/backintime/+bug/386230)
- [Launchpad#527039](https://bugs.launchpad.net/backintime/+bug/527039)
- [Launchpad#520956](https://bugs.launchpad.net/backintime/+bug/520956)
- [Launchpad#520930](https://bugs.launchpad.net/backintime/+bug/520930)
- [Launchpad#521223](https://bugs.launchpad.net/backintime/+bug/521223)
- [Launchpad#516066](https://bugs.launchpad.net/backintime/+bug/516066)
- [Launchpad#512813](https://bugs.launchpad.net/backintime/+bug/512813)
- [Launchpad#503859](https://bugs.launchpad.net/backintime/+bug/503859)
- [Launchpad#501285](https://bugs.launchpad.net/backintime/+bug/501285)
- [Launchpad#493558](https://bugs.launchpad.net/backintime/+bug/493558)
- [Launchpad#441628](https://bugs.launchpad.net/backintime/+bug/441628)
- [Launchpad#489319](https://bugs.launchpad.net/backintime/+bug/489319)
- [Launchpad#447841](https://bugs.launchpad.net/backintime/+bug/447841)
- [Launchpad#412695](https://bugs.launchpad.net/backintime/+bug/412695)

### Adicionado

- Erro Log and Erro Log view Diálogo (Gnome & KDE4)
- ionice Suporte for Usuário/cron Backup Processo
- the possibility para include Outro Snapshot Pastas within a Perfil, it can only read those, there não é a GUI implementation yet
- a tag suffix para the Snapshot_id, para evitar double Snapshot_ids

## [0.9.26] (2009-05-19)

### Não categorizado

- Atualizar Traduções de Launchpad
- Corrigir a bug in smart-Remover algorithm ([Launchpad#376104](https://bugs.launchpad.net/backintime/+bug/376104))
- Atualizar German Tradução (Michael Wiedmann <mw@miwie.in-berlin.de>)
- Usar only 'Pasta' term (Mais consistent com GNOME/KDE)
- Adicionar 'expert option': Ativar/Desativar nice for cron jobs
- GNOME & KDE4: refresh Snapshots Botão force Arquivos view para Atualizar too
- you can include a Backup parent Diretório (Backup Diretório will auto-exclude itself)

### Corrigido

- [Launchpad#374477](https://bugs.launchpad.net/backintime/+bug/374477)
- [Launchpad#375113](https://bugs.launchpad.net/backintime/+bug/375113)
- Alguns small bugs

### Adicionado

- '--no-Verificar' option para configure scripts

## [0.9.24] (2009-05-07)

### Não categorizado

- Atualizar Traduções
- KDE4: Corrigir python string <=> QString problems
- KDE4 FilesView/SnapshotsDialog: ctrl-click just select (don't execute)
- KDE4: Corrigir crush depois "take Snapshot" Processo ([Launchpad#366241](https://bugs.launchpad.net/backintime/+bug/366241))
- store basic Permissão in a special Arquivo so it can Restaurar them correctly (event de NTFS)
- implement Gnome/KDE4 systray icons and Usuário.callback as plugins
- reorganize code: common/GNOME/KDE4
- GNOME: break the big glade Arquivo in multiple Arquivo
- backintime is não mais aware of 'backintime-gnome' and 'backintime-kde4'  

### Adicionado

- config Versão

## [0.9.22.1] (2009-04-27)

### Corrigido

- French Tradução

## [0.9.22] (2009-04-24)

### Não categorizado

- Atualizar Traduções de Launchpad
- KDE4: Corrigir Alguns Tradução problems
- Atualizar German Tradução (Michael Wiedmann <mw@miwie.in-berlin.de>)
- Criar Diretório now Usar python os.makedirs (Substituir Usar of mkdir command)
- KDE4: Corrigir a crush related para QString - python string conversion
- GNOME & KDE4 SettingsDialog: if Agendamento Automático Backups per Diretório is set, global Agendamento is hidden
- GNOME FilesView: thread "*~" Arquivos (Backup Arquivos) as hidden Arquivos
- GNOME: Usar gtk-preferences icon for SettingsDialog (Substituir gtk-execute icon)
- expert option: $XDG_CONFIG_HOME/backintime/Usuário.callback (if exists) is called a different steps 
- Adicionar Mais command line options: --Snapshots-Listar, --Snapshots-Listar-Caminho, --Último-Snapshot, --Último-Snapshot-Caminho
- follow FreeDesktop Diretórios specs:  
- Novo Instalar Sistema: Usar Mais common steps (./configure; make; sudo make Instalar)

### Removido

- --safe-links for Salvar/Restaurar (this means Copiar symlinks as symlinks)

## [0.9.20] (2009-04-06)

### Não categorizado

- smart Remover: Corrigir an important bug and make it Mais verbose in syslog
- Atualizar Spanish Tradução (Francisco Manuel García Claramonte <franciscomanuel.garcia@hispalinux.es>)

## [0.9.18] (2009-04-02)

### Não categorizado

- Atualizar Traduções de Launchpad
- Atualizar Slovak Tradução (Tomáš Vadina <kyberdev@gmail.com>)
- Atualizar French Tradução (Michel Corps <mahikeulbody@gmail.com>)
- Atualizar German Tradução (Michael Wiedmann <mw@miwie.in-berlin.de>)
- GNOME bugfix: Corrigir a crush in Arquivos view for Arquivos com special characters (ex: "a%20b")
- GNOME SettingsDialog bugfix: if Snapshots Caminho is a Novo created Pasta, Snapshots navigation (Arquivos view) don't work
- Atualizar doc
- GNOME & KDE4 MainWindow: Rename "Places" Listar com "Snapshots"
- GNOME SettingsDialog bugfix: modify something, then press cancel. If you reopen the Diálogo it Mostrar Incorreto values (the ones antes cancel)
- GNOME & KDE4: Adicionar root mode menu entries (Usar gksu for gnome and kdesudo for kde)
- GNOME & KDE4: MainWindow - Arquivos view: se o Atual Diretório don't exists in Atual Snapshot display a Mensagem
- SettingDialog: Adicionar an expert option para Ativar para Agendamento Automático Backups per Diretório
- SettingDialog: Agendamento Automático Backups - se o Aplicativo can't find crontab it Mostrar an Erro
- SettingDialog: se o Aplicativo can't write in Snapshots Diretório there should be an Erro Mensagem
- GNOME & KDE4: rework Configurações Diálogo
- SettingDialog: Adicionar an option para Ativar/Desativar notifications

### Adicionado

- Polish Tradução (Paweł Hołuj <pholuj@gmail.com>)
- cron in common Pacote Dependências

## [0.9.16.1] (2009-03-16)

### Corrigido

- a bug/crush for French Versão

## [0.9.16] (2009-03-13)

### Não categorizado

- Atualizar Spanish Tradução (Francisco Manuel García Claramonte <franciscomanuel.garcia@hispalinux.es>)
- Atualizar Swedish Tradução (Niklas Grahn <terra.unknown@yahoo.com>)
- Atualizar French Tradução (Michel Corps <mahikeulbody@gmail.com>)
- Atualizar German Tradução (Michael Wiedmann <mw@miwie.in-berlin.de>)
- Atualizar Slovenian Tradução (Vanja Cvelbar <cvelbar@gmail.com>)
- don't Mostrar the Snapshot that is being taken in Snapshots Listar
- GNOME & KDE4: quando o Aplicativo starts and Snapshots Diretório don't exists Mostrar a messagebox
- give Mais Informações for 'take Snapshot' progress (para prove that não é blocked)
- MainWindow: rename 'Timeline' column com 'Snapshots'
- when it tries para take a Snapshot se o Snapshots Diretório don't exists  
- GNOME & KDE4: Adicionar notify se o Snapshots Diretório don't exists
- KDE4: rework MainWindow

### Adicionado

- Slovak Tradução (Tomáš Vadina <kyberdev@gmail.com>)

## [0.9.14] (2009-03-05)

### Não categorizado

- Atualizar German Tradução (Michael Wiedmann <mw@miwie.in-berlin.de>)
- Atualizar Swedish Tradução (Niklas Grahn <terra.unknown@yahoo.com>)
- Atualizar Spanish Tradução (Francisco Manuel García Claramonte <franciscomanuel.garcia@hispalinux.es>)
- Atualizar French Tradução (Michel Corps <mahikeulbody@gmail.com>)
- GNOME & KDE4: rework MainWindow
- GNOME & KDE4: rework SettingsDialog
- GNOME & KDE4: Adicionar "smart" Remover

## [0.9.12] (2009-02-28)

### Corrigido

- now if you include ".abc" Pasta and exclude ".*", ".abc" will be saved in the Snapshot
- bookmarks com special characters

### Não categorizado

- KDE4: Adicionar help

### Adicionado

- Slovenian Tradução (Vanja Cvelbar <cvelbar@gmail.com>)

## [0.9.10] (2009-02-24)

### Adicionado

- Swedish Tradução (Niklas Grahn <terra.unknown@yahoo.com>)

### Não categorizado

- KDE4: drop and drop de backintime Arquivos view para any Arquivo manager

### Corrigido

- Corrigir a segfault when running de cron

## [0.9.8] (2009-02-20)

### Não categorizado

- Atualizar Spanish Tradução (Francisco Manuel García Claramonte <franciscomanuel.garcia@hispalinux.es>)
- unsafe links are ignored (that means that a link para a Arquivo/Diretório outside of include Diretórios are ignored)
- KDE4: Adicionar Copiar para clipboard
- KDE4: sort Arquivos by Nome, Tamanho or Data
- cron 5/10 minutes: Substituir multiple lines com a single crontab line using divide (*/5 or */10)
- cron: when called de cron redirect output (stdout & stderr) para /dev/null

### Corrigido

- incapaz de Restaurar Arquivos that contains space char in their Nome

## [0.9.6] (2009-02-09)

### Não categorizado

- Atualizar Spanish Tradução (Francisco Manuel García Claramonte <franciscomanuel.garcia@hispalinux.es>)
- Atualizar German Tradução (Michael Wiedmann <mw@miwie.in-berlin.de>)
- GNOME: Atualizar docbook
- KDE4: Adicionar Snapshots Diálogo
- GNOME & KDE4: Adicionar Atualizar Snapshots Botão
- GNOME: Tratar special Pastas icons (home, Desktop)

## [0.9.4] (2009-01-30)

### Não categorizado

- Atualizar German Tradução (Michael Wiedmann <mw@miwie.in-berlin.de>)
- gnome: better handling of 'take Snapshot' status icon
- KDE4 (>= 4.1): Primeiro Versão (not finished)
- Atualizar man

## [0.9.2] (2009-01-16)

### Não categorizado

- Atualizar Spanish Tradução (Francisco Manuel García Claramonte <franciscomanuel.garcia@hispalinux.es>)
- Atualizar German Tradução (Michael Wiedmann <mw@miwie.in-berlin.de>)
- Substituir diff com rsync para Verificar if a Novo Snapshot is needed
- code cleanup

### Corrigido

- if you Adicionar "/a" in include Diretórios and "/a/b" in Padrões de exclusão, "/a/b*" items 
- it does not include ".*" items even if they não são excluded  

### Adicionado

- Mostrar hidden & Backup Arquivos toggle Botão for Arquivos view

## [0.9] (2009-01-09)

### Não categorizado

- Atualizar Spanish Tradução (Francisco Manuel García Claramonte <franciscomanuel.garcia@hispalinux.es>)
- make deb Pacotes Mais debian friendly (Obrigado para Michael Wiedmann <mw@miwie.in-berlin.de>)
- Atualizar German Tradução (Michael Wiedmann <mw@miwie.in-berlin.de>)
- better separation between common and gnome specific Arquivos and  
- code cleanup

### Corrigido

- when you Abrir Snapshots Diálogo for the second Tempo ( or Mais ) and you make a diff  

## [0.8.20] (2008-12-22)

### Corrigido

- sorting Arquivos/Diretórios by Nome is now case insensitive

### Não categorizado

- getmessages.sh: Ignorar "gtk-" items (this are gtk stock item ids and should not be changed)

## [0.8.18] (2008-12-17)

### Não categorizado

- Atualizar man/docbook

### Adicionado

- sort columns in MainWindow/FileView (by Nome, by Tamanho or by Data) and SnapshotsDialog (by Data)

### Corrigido

- German Tradução (Michael Wiedmann <mw@miwie.in-berlin.de>)

## [0.8.16] (2008-12-11)

### Não categorizado

- Adicionar Drag & Drop de MainWindow: FileView/SnapshotsDialog para Nautilus
- Atualizar German Tradução (Michael Wiedmann <mw@miwie.in-berlin.de>)

## [0.8.14] (2008-12-07)

### Adicionado

- Mais command line parameters ( --Versão, --Snapshots, --help )

### Corrigido

- a crush for getting info on dead symbolic links

### Não categorizado

- when taking a Novo Backup based on the Anterior one don't Copiar the Anterior extra info (ex: Nome)
- Copiar unsafe links when Ao criar um Snapshot

## [0.8.12] (2008-12-01)

### Adicionado

- German Tradução (Michael Wiedmann <mw@miwie.in-berlin.de>)
- SnapshotNameDialog
- Nome/Remover Snapshot in main toolbar

### Alterado

- the way it detects se o mainwindow is the active Janela (no Diálogos)

### Não categorizado

- toolbars: Mostrar icons only
- Atualizar Spanish Tradução (Francisco Manuel García Claramonte <franciscomanuel.garcia@hispalinux.es>)

## [0.8.10] (2008-11-22)

### Não categorizado

- SnapshotsDialog: Adicionar right-click popup-menu and a toolbar com Copiar & Restaurar Botões
- Usar a Mais robust Backup lock Arquivo
- Log using syslog
- Atualizar Spanish Tradução (Francisco Manuel García Claramonte <franciscomanuel.garcia@hispalinux.es>)

### Corrigido

- a small bug in Copiar para clipboard

## [0.8.8] (2008-11-19)

### Não categorizado

- SnapshotsDialog: Adicionar diff
- Atualizar Spanish Tradução (Francisco Manuel García Claramonte <franciscomanuel.garcia@hispalinux.es>)

## [0.8.6] (2008-11-17)

### Corrigido

- Alterar Backup Caminho crush

### Adicionado

- SnapshotsDialog

## [0.8.2] (2008-11-14)

### Não categorizado

- Adicionar right-click menu in Arquivos Listar: Abrir (using gnome-Abrir), Copiar (you can paste in Nautilus), Restaurar (for Snapshots only)

### Adicionado

- Copiar toolbar Botão for Arquivos Listar

## [0.8.1] (2008-11-10)

### Adicionado

- every 5/10 minutes Automático Backup

## [0.8] (2008-11-07)

### Não categorizado

- don't Mostrar Backup Arquivos (*~)
- makedeb.sh: make a single Pacote com Todos Idiomas included
- Instalar.sh: Instalar Todos Idiomas
- the Aplicativo can be started com a 'Caminho' para a Pasta or Arquivo as command line parameter
- quando o Aplicativo Iniciar, if it is already running pass its command line para the Primeiro instance (this Permitir a basic integration com Arquivo-managers - see README)

### Adicionado

- Backup Arquivos para Padrão Padrões de exclusão (*~)
- English Manual (man)
- English help (docbook)
- help Botão in main toolbar

### Corrigido

- quando o Aplicativo was started a second Tempo it raise the Primeiro Aplicativo's Janela but not always focused

## [0.7.4] (2008-11-03)

### Não categorizado

- if there is already a GUI instance running raise it

### Adicionado

- Spanish Tradução (Francisco Manuel García Claramonte <franciscomanuel.garcia@hispalinux.es>)

## [0.7.2] (2008-10-28)

### Não categorizado

- better integration com gnome icons (Usar mime-types)
- Lembrar Último Caminho
- capitalize month in timeline (bug in french Tradução)

## [0.7] (2008-10-22)

### Corrigido

- cron segfault
- a crush when launched the very Primeiro Tempo (not configured)

### Não categorizado

- multi-lingual Suporte

### Adicionado

- French Tradução

## [0.6.4] (2008-10-20)

### Removido

- About & Configurações Diálogos de the pager

### Não categorizado

- Permitir only one instance of the Aplicativo

## [0.6.2] (2008-10-16)

### Não categorizado

- Lembrar Janela position & Tamanho

## [0.6] (2008-10-13)

### Não categorizado

- when it make a Snapshot it display an icon in systray area
- the Segundo plano color for Grupo items in timeline and places reflect Mais 
- durante Restaurar only Restaurar Botão is grayed ( even if everything is blocked )

## [0.5.1] (2008-10-10)

### Adicionado

- Tamanho & Data columns in Arquivos view

### Alterado

- Alguns texts

## [0.5] (2008-10-03)

### Não categorizado

- This is the Primeiro Versão.

<!-- Template
## Unreleased
### Alterado
### Adicionado
### Removido
### Corrigido
-->

[2.0.0]: https://github.com/bit-team/backintime/releases/tag/v2.0.0
[2.0.0-rc1]: https://github.com/bit-team/backintime/releases/tag/v2.0.0-rc1
[1.6.2]: https://github.com/bit-team/backintime/releases/tag/v1.6.2
[1.6.1]: https://github.com/bit-team/backintime/releases/tag/v1.6.1
[1.6.0]: https://github.com/bit-team/backintime/releases/tag/v1.6.0
[1.5.6]: https://github.com/bit-team/backintime/releases/tag/v1.5.6
[1.5.5]: https://github.com/bit-team/backintime/releases/tag/v1.5.5
[1.5.4]: https://github.com/bit-team/backintime/releases/tag/v1.5.4
[1.5.3]: https://github.com/bit-team/backintime/releases/tag/v1.5.3
[1.5.2]: https://github.com/bit-team/backintime/releases/tag/v1.5.2
[1.5.1]: https://github.com/bit-team/backintime/releases/tag/v1.5.1
[1.5.0]: https://github.com/bit-team/backintime/releases/tag/v1.5.0
[1.4.3]: https://github.com/bit-team/backintime/releases/tag/v1.4.3
[1.4.1]: https://github.com/bit-team/backintime/releases/tag/v1.4.1
[1.4.0]: https://github.com/bit-team/backintime/releases/tag/v1.4.0
[1.3.3]: https://github.com/bit-team/backintime/releases/tag/v1.3.3
[1.3.2]: https://github.com/bit-team/backintime/releases/tag/v1.3.2
[1.3.1]: https://github.com/bit-team/backintime/releases/tag/v1.3.1
[1.3.0]: https://github.com/bit-team/backintime/releases/tag/v1.3.0
[1.2.1]: https://github.com/bit-team/backintime/releases/tag/v1.2.1
[1.2.0]: https://github.com/bit-team/backintime/releases/tag/v1.2.0
[1.1.24]: https://github.com/bit-team/backintime/releases/tag/v1.1.24
[1.1.22]: https://github.com/bit-team/backintime/releases/tag/v1.1.22
[1.1.20]: https://github.com/bit-team/backintime/releases/tag/v1.1.20
[1.1.18]: https://github.com/bit-team/backintime/releases/tag/v1.1.18
[1.1.16]: https://github.com/bit-team/backintime/releases/tag/v1.1.16
[1.1.14]: https://github.com/bit-team/backintime/releases/tag/v1.1.14
[1.1.12]: https://github.com/bit-team/backintime/releases/tag/v1.1.12
[1.1.10]: https://github.com/bit-team/backintime/releases/tag/v1.1.10
[1.1.8]: https://github.com/bit-team/backintime/releases/tag/v1.1.8
[1.1.6]: https://github.com/bit-team/backintime/releases/tag/v1.1.6
[1.1.4]: https://github.com/bit-team/backintime/releases/tag/v1.1.4
[1.1.2]: https://github.com/bit-team/backintime/releases/tag/v1.1.2
[1.1.0]: https://github.com/bit-team/backintime/releases/tag/v1.1.0
[1.0.40]: https://github.com/bit-team/backintime/releases/tag/v1.0.40
[1.0.38]: https://github.com/bit-team/backintime/releases/tag/v1.0.38
[1.0.36]: https://github.com/bit-team/backintime/releases/tag/v1.0.36
[1.0.34]: https://github.com/bit-team/backintime/releases/tag/v1.0.34
[1.0.32]: https://github.com/bit-team/backintime/releases/tag/v1.0.32
[1.0.30]: https://github.com/bit-team/backintime/releases/tag/v1.0.30
[1.0.28]: https://github.com/bit-team/backintime/releases/tag/v1.0.28
[1.0.26]: https://github.com/bit-team/backintime/releases/tag/v1.0.26
[1.0.24]: https://github.com/bit-team/backintime/releases/tag/v1.0.24
[1.0.22]: https://github.com/bit-team/backintime/releases/tag/v1.0.22
[1.0.20]: https://github.com/bit-team/backintime/releases/tag/v1.0.20
[1.0.18]: https://github.com/bit-team/backintime/releases/tag/v1.0.18
[1.0.16]: https://github.com/bit-team/backintime/releases/tag/v1.0.16
[1.0.14]: https://github.com/bit-team/backintime/releases/tag/v1.0.14
[1.0.12]: https://github.com/bit-team/backintime/releases/tag/v1.0.12
[1.0.10]: https://github.com/bit-team/backintime/releases/tag/v1.0.10
[1.0.8]: https://github.com/bit-team/backintime/releases/tag/v1.0.8
[1.0.6]: https://github.com/bit-team/backintime/releases/tag/v1.0.6
[1.0.4]: https://github.com/bit-team/backintime/releases/tag/v1.0.4
[1.0.2]: https://github.com/bit-team/backintime/releases/tag/v1.0.2
[1.0]: https://github.com/bit-team/backintime/releases/tag/v1.0
[0.9.26]: https://github.com/bit-team/backintime/releases/tag/v0.9.26
[0.9.24]: https://github.com/bit-team/backintime/releases/tag/v0.9.24
[0.9.22.1]: https://github.com/bit-team/backintime/releases/tag/v0.9.22.1
[0.9.22]: https://github.com/bit-team/backintime/releases/tag/v0.9.22
[0.9.20]: https://github.com/bit-team/backintime/releases/tag/v0.9.20
[0.9.18]: https://github.com/bit-team/backintime/releases/tag/v0.9.18
[0.9.16.1]: https://github.com/bit-team/backintime/releases/tag/v0.9.16.1
[0.9.16]: https://github.com/bit-team/backintime/releases/tag/v0.9.16
[0.9.14]: https://github.com/bit-team/backintime/releases/tag/v0.9.14
[0.9.12]: https://github.com/bit-team/backintime/releases/tag/v0.9.12
[0.9.10]: https://github.com/bit-team/backintime/releases/tag/v0.9.10
[0.9.8]: https://github.com/bit-team/backintime/releases/tag/v0.9.8
[0.9.6]: https://github.com/bit-team/backintime/releases/tag/v0.9.6
[0.9.4]: https://github.com/bit-team/backintime/releases/tag/v0.9.4
[0.9.2]: https://github.com/bit-team/backintime/releases/tag/v0.9.2
[0.9]: https://github.com/bit-team/backintime/releases/tag/v0.9
[0.8.20]: https://github.com/bit-team/backintime/releases/tag/v0.8.20
[0.8.18]: https://github.com/bit-team/backintime/releases/tag/v0.8.18
[0.8.16]: https://github.com/bit-team/backintime/releases/tag/v0.8.16
[0.8.14]: https://github.com/bit-team/backintime/releases/tag/v0.8.14
[0.8.12]: https://github.com/bit-team/backintime/releases/tag/v0.8.12
[0.8.10]: https://github.com/bit-team/backintime/releases/tag/v0.8.10
[0.8.8]: https://github.com/bit-team/backintime/releases/tag/v0.8.8
[0.8.6]: https://github.com/bit-team/backintime/releases/tag/v0.8.6
[0.8.2]: https://github.com/bit-team/backintime/releases/tag/v0.8.2
[0.8.1]: https://github.com/bit-team/backintime/releases/tag/v0.8.1
[0.8]: https://github.com/bit-team/backintime/releases/tag/v0.8
[0.7.4]: https://github.com/bit-team/backintime/releases/tag/v0.7.4
[0.7.2]: https://github.com/bit-team/backintime/releases/tag/v0.7.2
[0.7]: https://github.com/bit-team/backintime/releases/tag/v0.7
[0.6.4]: https://github.com/bit-team/backintime/releases/tag/v0.6.4
[0.6.2]: https://github.com/bit-team/backintime/releases/tag/v0.6.2
[0.6]: https://github.com/bit-team/backintime/releases/tag/v0.6
[0.5.1]: https://github.com/bit-team/backintime/releases/tag/v0.5.1
[0.5]: https://github.com/bit-team/backintime/releases/tag/v0.5
