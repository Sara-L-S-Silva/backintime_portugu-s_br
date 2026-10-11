# Manage profiles
<!--
SPDX-FileCopyrightText: © 2016 Germar Reitze

SPDX-License-Identifier: GPL-2.0-or-later

This file is part of the program "Back In Time" which is released under GNU
General Public License v2 (GPLv2). See LICENSES directory or go to
<https://spdx.org/licenses/GPL-2.0-or-later.html>
-->
## General

Você pode escolher qual modo o *Back in Time* deve usar para armazenar backups.

Modos disponíveis:

- [Local](#local)
- [Local Encrypted](#local-encrypted)
- [SSH](#ssh)
- [SSH Encrypted](#ssh-encrypted)

### Local

Backups locais podem ser armazenados em discos rígidos internos ou externos, ou
em compartilhamentos montados. O file-system de destino deve oferecer suporte a
hard-links. O protocolo usado para montar o compartilhamento remoto também deve
oferecer suporte a hard-links e symlinks. Por padrão, servidores Samba (SMB/CIFS)
não oferecem suporte a symlinks (isso pode ser ativado com `follow
symlinks = yes` e `wide links = yes` em `/etc/samba/smb.conf`). Compartilhamentos
montados com sshfs não oferecem suporte a hard-links.

![Settings - General](_images/light/settings_general.png#only-light)
![Settings - General](_images/dark/settings_general.png#only-dark)

Escolha o caminho de destino dos backups usando o botão
_directory_ (para exibir arquivos ocultos, use
CTRL + H ou o menu de contexto, aberto com o botão direito do mouse). O Back in Time criará
subdiretórios `backintime/<HOST>/<USER>/<PROFILE>/` dentro desse diretório.
Os backups serão colocados dentro do diretório `<PROFILE>/`.

### Local Encrypted

[Local Encrypted](#local-encrypted) funciona como [Local](#local), mas os backups
serão armazenados criptografados com `gocryptfs`. O diretório criptografado será
criado automaticamente dentro da pasta selecionada.

![Manage profiles - General](_images/light/settings_general_local_encrypted.png#only-light)
![Manage profiles - General](_images/dark/settings_general_local_encrypted.png#only-dark)

Informe a senha do `gocryptfs` em `Encryption`. A senha pode ser armazenada
no keyring do usuário. O keyring é desbloqueado com a senha do usuário durante
o login. Se um backup-job agendado for executado enquanto o usuário não estiver
conectado, o keyring não estará disponível. Nesse caso, o Back In Time pode
manter a senha em cache na memória.

### SSH

Este modo armazena backups em um host remoto acessível por
`SSH`. O `rsync` será executado diretamente no host remoto, o que torna esse modo
muito mais rápido do que sincronizar com um compartilhamento montado localmente.

Para usar esse modo, o host remoto precisa estar no seu arquivo `known_hosts`.
Lembre-se de que os nomes dos hosts nesse arquivo diferenciam maiúsculas de
minúsculas. Você precisa ter um par de chaves pública/privada SSH instalado no
host remoto. A partir da versão 1.2.0 do Back in Time, isso será feito
automaticamente. Em versões anteriores à 1.2.0, você precisa fazer isso
manualmente:

- Se você ainda não fez login no host remoto, execute `ssh
  USER@HOST` no Terminal. Será solicitado que confirme a fingerprint da
  host-key remota com `yes`. Para comparar a host-key, faça login localmente
  no host remoto e execute `ssh-keygen -l -f
  /etc/ssh/ssh_host_ecdsa_key.pub`. A fingerprint exibida nessa saída deve
  corresponder à fingerprint solicitada anteriormente. Depois disso, você pode
  sair imediatamente.
- Gere um novo par de chaves pública/privada SSH com `ssh-keygen`. Pressione Enter para
  aceitar o caminho padrão e informe uma senha para a nova chave (ela não tem
  relação com a senha do seu usuário no host remoto).
- Execute `ssh-copy-id -i ~/.ssh/id_rsa.pub USER@HOST` para instalar a chave recém-criada
  no host remoto. Esta será a última vez que você precisará informar a senha de
  login do usuário remoto. Se tudo der certo, você poderá fazer login sem que
  sua senha de login seja solicitada.

![Settings - General](_images/light/settings_general_ssh.png#only-light)
![Settings - General](_images/dark/settings_general_ssh.png#only-dark)

Informe o nome ou o endereço IP do host remoto em `Host` e a porta do
servidor SSH remoto em `Port` (o padrão é `22`). `User` deve ser o usuário
remoto. `Path` pode ficar vazio para colocar o diretório de backups diretamente
na pasta home do usuário remoto. Caminhos relativos sem barra inicial (`foo/bar/`)
serão subdiretórios da pasta home do usuário. Caminhos com barra inicial
(`/mnt/foo/bar/`) serão absolutos.

Em `Cipher`, você pode escolher o cipher (algoritmo usado para criptografar) na
transferência SSH. Dependendo dos sistemas envolvidos, pode ser mais rápido
selecionar um cipher diferente do padrão. Alguns deles podem não funcionar
porque são considerados inseguros.

Em `Private Key`, selecione sua chave privada SSH. Se ela ainda não existir,
você pode criar um novo par de chaves pública/privada SSH sem senha clicando
no botão _add_.

Informe a senha da chave privada em `SSH private key` (esta é a senha escolhida
anteriormente durante a criação do par de chaves pública/privada, não a senha
de login do usuário remoto). A senha pode ser armazenada no keyring do usuário.
O keyring é desbloqueado com a senha do usuário durante o login. Se um
backup-job agendado for executado enquanto o usuário não estiver conectado,
o keyring não estará disponível. Nesse caso, o Back In Time pode manter a senha
em cache na memória.

### SSH Encrypted

SSH Encrypted](#ssh-encrypted) funciona como [SSH](#ssh), mas os backups
serão armazenados criptografados usando `gocryptfs`. O Back in Time montará uma
visualização criptografada do file-system e a sincronizará com `rsync` para
o host remoto.

![Settings - General](_images/light/settings_general_ssh_encrypted.png#only-light)
![Settings - General](_images/dark/settings_general_ssh_encrypted.png#only-dark)

Além das configurações de [SSH](#ssh), você precisa informar uma senha
para a criptografia.

### Advanced

`Host`, `User` e `Profile` serão preenchidos automaticamente (não podem ficar
vazios). Eles são usados no caminho de backup
`backintime/<HOST>/<USER>/<PROFILE>/`. O caminho completo do backup será exibido
abaixo. Você pode alterá-los para corresponder aos caminhos de outras máquinas.

### Schedule

Há diferentes tipos de agendamento disponíveis para diferentes fluxos de
trabalho de backup, dependendo de como os backups devem ser acionados.

A maioria dos agendamentos executa backups em **horários fixos**. Se o computador
estiver desligado no horário agendado, o backup será ignorado e não será
iniciado posteriormente.
Outros agendamentos podem **recuperar execuções perdidas**. Se o computador estava
desligado quando chegou a hora de um backup, ele será iniciado na próxima vez
que o _Back In Time_ puder verificar o agendamento.
Além disso, agendamentos **baseados em eventos** iniciam backups em resposta a
eventos específicos, como a inicialização do sistema ou a conexão de uma unidade
de backup via USB.

**Modos de agendamento por horário fixo**:

- **Every Day**: inicia um novo backup todos os dias em um horário configurável.
- **Every Week**: inicia um novo backup toda semana em um dia da semana e horário configuráveis.
- **Every Month**: inicia um novo backup todo mês em um dia e horário configuráveis.
- **Every Year**: inicia um novo backup no primeiro dia do primeiro mês de cada ano,
  em um horário configurável.
- **Every X minutes**: inicia um novo backup a cada 5, 10 ou 30 minutos. Isso
  adicionará uma linha `*/<X> * * * * <COMMAND>` ao `crontab`.
- **Every hour**: inicia um novo backup a cada hora cheia. Isso adicionará uma linha
  `0 * * * * <COMMAND>` ao `crontab`.
- **Every X hours**: inicia um novo backup a cada 2, 4, 6 ou 12 horas, na hora cheia
  (por exemplo, às 0:00, 6:00, 12:00 e 18:00 com o agendamento "Every 6 hours"). Isso
  adicionará uma linha `0 */<X> * * * <COMMAND>` ao `crontab`.
- **Custom Hours**: define um padrão personalizado para o `crontab`. Pode ser uma
  lista de horas separadas por vírgulas (por exemplo, `0,10,13,15,17,20,23`) ou
  `*/<X>` (por exemplo, `*/3`) para agendamentos periódicos. Isso adicionará uma linha
  `0 0,10,13,15,17,20,23 * * * <COMMAND>` ao `crontab`.

**Modo de agendamento com recuperação de execuções perdidas**:

- **Repeatedly**: este agendamento aciona backups quando passa um número configurado de
  unidades do calendário (horas, dias, semanas ou meses) desde o último
  backup bem-sucedido.
  Um backup fica pendente quando uma nova unidade do calendário começa. Por
  exemplo, "1 hour" significa que o backup é executado quando começa a próxima
  hora do relógio, e não após um período fixo de 60 minutos.
  O _Back In Time verifica_ o agendamento periodicamente por meio de uma entrada no crontab
  (normalmente a cada 15 minutos, ou a cada hora para intervalos mais longos). Se não
  houver backup pendente, o processo é encerrado imediatamente.
  Se o sistema estiver desligado ou o _Back In Time_ não estiver em execução quando
  um backup ficar pendente, ele será realizado na próxima verificação do agendamento.
  Se um backup falhar, haverá uma nova tentativa na próxima verificação.

**Modos de agendamento baseados em eventos**:

- **At every boot/reboot**: inicia um novo backup imediatamente após a
  inicialização. Isso adicionará uma linha `@reboot <COMMAND>` ao `crontab`. Sair
  dos modos suspend/hibernate não acionará este agendamento.
- **When drive gets connected (udev)**: este agendamento inicia um novo backup assim
  que uma unidade USB/eSATA/Firewire é conectada. Você pode configurar um
  atraso (horas, dias ou semanas) para que o backup não seja iniciado a cada
  nova conexão. Isso adicionará uma nova regra udev em
  `/etc/udev/rules.d/99-backintime-<USER>.rules`, usando o UUID da partição.
  Certifique-se de que o auto-mount esteja ativado no sistema.

**Detalhes técnicos**:

A maioria dos modos usa `crontab` para configurar novos agendamentos. Você pode usar
`crontab -l` para visualizá-los ou `crontab -e` para editá-los manualmente.

## Include

![Settings - Include](_images/light/settings_include.png#only-light)
![Settings - Include](_images/dark/settings_include.png#only-dark)

## Exclude

![Settings - Exclude](_images/light/settings_exclude.png#only-light)
![Settings - Exclude](_images/dark/settings_exclude.png#only-dark)

## Remove & Retention
Também conhecido como _Auto-remove_ em versões anteriores do _Back In Time_.

![Settings - Auto Remove](_images/light/settings_autoremove.png#only-light)
![Settings - Auto Remove](_images/dark/settings_autoremove.png#only-dark)

## Options

![Settings - Options](_images/light/settings_options.png#only-light)
![Settings - Options](_images/dark/settings_options.png#only-dark)

## Expert Options

![Settings - Expert Options](_images/light/settings_expert_options.png#only-light)
![Settings - Expert Options](_images/dark/settings_expert_options.png#only-dark)

## User-callback

Para mais informações sobre user callback, consulte [este documento](user-callback.md).