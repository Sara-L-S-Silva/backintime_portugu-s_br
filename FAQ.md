<!--
SPDX-FileCopyrightText: © 2022 Back In Time Team
SPDX-FileCopyrightText: © 2024 Paul Worrall (@Silver-Saucepan)

SPDX-License-Identifier: GPL-2.0-or-later

This file is part of the program "Back In Time" which is released under GNU
General Public License v2 (GPLv2). See LICENSES directory or go to
<https://spdx.org/licenses/GPL-2.0-or-later.html>
-->

<sub>Junho de 2026</sub>

# FAQ - Perguntas frequentes

<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

* [Geral](#geral)

  * [O que aconteceu com os perfis criptografados e o EncFS?](#o-que-aconteceu-com-os-perfis-criptografados-e-o-encfs)
  * [O *Back in Time* oferece suporte a backups completos do sistema?](#o-back-in-time-oferece-suporte-a-backups-completos-do-sistema)
  * [O *Back in Time* oferece suporte a backups em armazenamento na nuvem, como OneDrive ou Google Drive?](#o-back-in-time-oferece-suporte-a-backups-em-armazenamento-na-nuvem-como-onedrive-ou-google-drive)
  * [Onde está o arquivo de log?](#onde-esta-o-arquivo-de-log)
  * [Como ler as entradas do log?](#como-ler-as-entradas-do-log)
  * [Como mover backups para um novo disco rígido?](#como-mover-backups-para-um-novo-disco-rigido)
  * [Como mover um diretório grande na origem do backup sem duplicar os arquivos no backup?](#como-mover-um-diretorio-grande-na-origem-do-backup-sem-duplicar-os-arquivos-no-backup)
  * [Como o *Back In Time* se compara ao *Timeshift*?](#como-o-back-in-time-se-compara-ao-timeshift)
  * [Recursos adicionais além da GUI e benefícios de usar o BIT](#recursos-adicionais-alem-da-gui-e-beneficios-de-usar-o-bit)
* [Backups (snapshots)](#backups-snapshots)

  * [Backup ou snapshot?](#backup-ou-snapshot)
  * [O *Back In Time* cria backups incrementais ou completos?](#o-back-in-time-cria-backups-incrementais-ou-completos)
  * [Como funcionam os backups com hard-links?](#como-funcionam-os-backups-com-hard-links)
  * [Como posso verificar se meus backups estão usando hard-links?](#como-posso-verificar-se-meus-backups-estao-usando-hard-links)
  * [Como usar checksum para encontrar arquivos corrompidos periodicamente?](#como-usar-checksum-para-encontrar-arquivos-corrompidos-periodicamente)
  * [Qual é o significado dos 11 caracteres iniciais (por exemplo, "cf...p.....") nos meus logs de backup?](#qual-e-o-significado-dos-11-caracteres-iniciais-por-exemplo-cfp-nos-meus-logs-de-backup)
  * [Backup "COM ERROS": [E] 'rsync' terminou com código de saída 23: consulte 'man rsync' para mais detalhes](#backup-com-erros-e-rsync-terminou-com-codigo-de-saida-23-consulte-man-rsync-para-mais-detalhes)
  * [O que acontece quando removo um backup?](#o-que-acontece-quando-removo-um-backup)
  * [Como posso excluir pastas de cache para melhorar a velocidade do backup e reduzir o armazenamento?](#como-posso-excluir-pastas-de-cache-para-melhorar-a-velocidade-do-backup-e-reduzir-o-armazenamento)
  * [Como usar atributos estendidos do sistema de arquivos (xattr) para excluir arquivos/diretórios?](#como-usar-atributos-estendidos-do-sistema-de-arquivos-xattr-para-excluir-arquivosdiretorios)
  * [Como o Back In Time lida com arquivos abertos ou alterados durante o backup?](#como-o-back-in-time-lida-com-arquivos-abertos-ou-alterados-durante-o-backup)
* [Restauração](#restauracao)

  * [Após a restauração, tenho duplicatas com a extensão ".backup.20131121"](#apos-a-restauracao-tenho-duplicatas-com-a-extensao-backup20131121)
  * [O Back In Time não encontra meus backups antigos no meu novo computador](#o-back-in-time-nao-encontra-meus-backups-antigos-no-meu-novo-computador)
* [Agendamento](#agendamento)

  * [Como funciona o agendamento "Repetidamente (anacron)"?](#como-funciona-o-agendamento-repetidamente-anacron)
  * [Se eu editar meu crontab e adicionar entradas adicionais, haverá algum problema para o BIT desde que eu não altere as entradas dele? O que ele procura no crontab para encontrar suas próprias entradas?](#se-eu-editar-meu-crontab-e-adicionar-entradas-adicionais-havera-algum-problema-para-o-bit-desde-que-eu-nao-altere-as-entradas-dele-o-que-ele-procura-no-crontab-para-encontrar-suas-proprias-entradas)
  * [Posso usar um systemd timer em vez de cron?](#posso-usar-um-systemd-timer-em-vez-de-cron)
* [Problemas, erros e soluções](#problemas-erros-e-solucoes)

  * [Erros críticos sobre "`snapshots.ssh_check_commands` ou `snapshots.ssh.check_ping` não definidos como padrão..."](#erros-criticos-sobre-snapshotsssh_check_commands-ou-snapshotssshcheck_ping-nao-definidos-como-padrao)
  * [OverflowError: Value 1702441408 out of range for UInt32](#overflowerror-value-1702441408-out-of-range-for-uint32)
  * [`SettingsDialog` object has no attribute `cbCopyUnsafeLinks`](#settingsdialog-object-has-no-attribute-cbcopyunsafelinks)
  * [WARNING: A backup is already running](#warning-a-backup-is-already-running)
  * [*Back in Time* não inicia e mostra: The application is already running! (pid: 1234567)](#back-in-time-nao-inicia-e-mostra-the-application-is-already-running-pid-1234567)
  * [A mudança para o modo escuro ou claro no ambiente desktop é ignorada pelo BIT](#a-mudanca-para-o-modo-escuro-ou-claro-no-ambiente-desktop-e-ignorada-pelo-bit)
  * [A versão >= 1.2.0 funciona muito lentamente / arquivos inalterados são copiados](#a-versao--120-funciona-muito-lentamente--arquivos-inalterados-sao-copiados)
  * [O que acontece se eu colocar o computador em hibernação enquanto um backup está sendo executado?](#o-que-acontece-se-eu-colocar-o-computador-em-hibernacao-enquanto-um-backup-esta-sendo-executado)
  * [O que acontece se eu desligar o computador enquanto um backup está sendo executado ou se ocorrer uma queda de energia?](#o-que-acontece-se-eu-desligar-o-computador-enquanto-um-backup-esta-sendo-executado-ou-se-ocorrer-uma-queda-de-energia)
  * [O que acontece se não houver espaço suficiente em disco para o backup atual?](#o-que-acontece-se-nao-houver-espaco-suficiente-em-disco-para-o-backup-atual)
  * [Compatibilidade com NTFS](#compatibilidade-com-ntfs)
  * [A GUI não é dimensionada corretamente em monitores de alta resolução ou 4K](#a-gui-nao-e-dimensionada-corretamente-em-monitores-de-alta-resolucao-ou-4k)
  * [Ícone da bandeja ou outros ícones não são exibidos corretamente](#icone-da-bandeja-ou-outros-icones-nao-sao-exibidos-corretamente)
  * [Cofre de senhas não funciona e o BiT esquece as senhas (problemas com o backend do keyring)](#cofre-de-senhas-nao-funciona-e-o-bit-esquece-as-senhas-problemas-com-o-backend-do-keyring)
  * [Desatualizado](#desatualizado)

    * [Segmentation fault ao sair](#segmentation-fault-ao-sair)
    * [Incompatibilidade com rsync >= 3.2.4](#incompatibilidade-com-rsync-324-ou-superior)
* [Configuração específica de hardware](#configuracao-especifica-de-hardware)

  * [Como usar o BIT com um NAS Ugreen?](#como-usar-o-bit-com-um-nas-ugreen)
  * [Como usar um NAS QNAP QTS com o BIT via SSH](#como-usar-um-nas-qnap-qts-com-o-bit-via-ssh)
  * [Como usar o Synology DSM 5 com o BIT via SSH](#como-usar-o-synology-dsm-5-com-o-bit-via-ssh)
  * [Como usar o Synology DSM 6 com o BIT via SSH](#como-usar-o-synology-dsm-6-com-o-bit-via-ssh)

  * [Usando uma porta não padrão](#usando-uma-porta-nao-padrao)
  * [Como usar o Synology DSM 7 com o BIT via SSH](#como-usar-o-synology-dsm-7-com-o-bit-via-ssh)

    * [Usando uma porta SSH não padrão com um NAS Synology](#usando-uma-porta-ssh-nao-padrao-com-um-nas-synology)
    * ["sshfs: No such file or directory" ao usar o BIT, mas o SSH manual com rsync funciona](#sshfs-no-such-file-or-directory-ao-usar-o-bit-mas-o-ssh-manual-com-rsync-funciona)
  * [Synology: usar um volume diferente para o backup](#synology-usar-um-volume-diferente-para-o-backup)
  * [Como usar o Western Digital MyBook World Edition com o BIT via ssh?](#como-usar-o-western-digital-mybook-world-edition-com-o-bit-via-ssh)
* [Projeto, contribuição e mais](#projeto-contribuicao-e-mais)

  * [Por que preciso me apresentar?](#por-que-preciso-me-apresentar)
  * [Posso contribuir sem usar o software?](#posso-contribuir-sem-usar-o-software)
  * [Vocês podem atribuir isso a mim?](#voces-podem-atribuir-isso-a-mim)
  * [Posso usar menções com @ livremente em issues ou PRs?](#posso-usar-mencoes-com-livremente-em-issues-ou-prs)
  * [Posso aumentar minha contagem de commits?](#posso-aumentar-minha-contagem-de-commits)
  * [Posso enviar contribuições geradas por IA?](#posso-enviar-contribuicoes-geradas-por-ia)
  * [Opções alternativas de instalação](#opcoes-alternativas-de-instalacao)
  * [Suporte a formatos específicos de pacotes (deb, rpm, Flatpack, AppImage, Snaps, PPA, …)](#suporte-a-formatos-especificos-de-pacotes-deb-rpm-flatpack-appimage-snaps-ppa-)

  - [O BIT realmente não é suportado pelo Canonical Ubuntu?](#o-bit-realmente-nao-e-suportado-pelo-canonical-ubuntu)

  * [Mover o projeto para um host de código alternativo (por exemplo, Codeberg, GitLab, …)](#mover-o-projeto-para-um-host-de-codigo-alternativo-por-exemplo-codeberg-gitlab-)
  * [Como revisar um Pull Request](#como-revisar-um-pull-request)
* [Testes e compilação](#testes-e-compilacao)

  * [Testes relacionados a SSH são ignorados](#testes-relacionados-a-ssh-sao-ignorados)
  * [Configurar um servidor SSH para executar testes unitários](#configurar-um-servidor-ssh-para-executar-testes-unitarios)

<!-- TOC end -->

# Geral

## O que aconteceu com os perfis criptografados e o EncFS?

Consulte este documento adicional sobre a [transição do recurso de
criptografia](doc/ENCRYPT_TRANSITION.md). Nele você também encontrará uma
[FAQ](doc/ENCRYPT_TRANSITION.md#faq---frequently-asked-questions).

## O *Back in Time* oferece suporte a backups completos do sistema?

O *Back in Time* é adequado para backups baseados em arquivos.

Um backup completo do sistema não é suportado nem recomendado
(mesmo que você pudesse usar o *Back in Time (root)* e incluir sua
pasta raiz `\`) porque

* Sistemas de arquivos montados (até mesmo locais remotos)
* o backup precisaria ser feito de dentro do sistema em execução
* arquivos especiais do kernel Linux (por exemplo, /proc) precisam ser excluídos
* arquivos bloqueados ou abertos (em um estado inconsistente) precisam ser tratados
* backups de partições de disco adicionais (bootloader, EFI...) são necessários para que seja possível inicializar
* uma restauração não pode sobrescrever o sistema em execução (onde o software de backup está sendo executado) sem o risco de travamentos ou perda de dados (normalmente, para isso, a restauração precisa ser feita a partir de um dispositivo de inicialização separado)
* ...

Para backups completos do sistema, procure por

* uma solução de criação de imagem de disco ("clonagem") (por exemplo, [Clonezilla](https://clonezilla.org/))
* ferramentas de backup baseadas em arquivos que foram projetadas para isso (por exemplo, [`Timeshift`](https://github.com/linuxmint/timeshift))

## O *Back in Time* oferece suporte a backups em armazenamento na nuvem, como OneDrive ou Google Drive?

O armazenamento na nuvem como origem ou destino do backup não é suportado porque o *Back in Time*
usa `rsync` como backend para transferência de arquivos e, portanto, é necessário um sistema de arquivos
montado localmente ou uma conexão `ssh`. Isso ocorre por causa do suporte limitado ao acesso a arquivos
"especiais" que é usado pelo BiT (por exemplo, Linux hardlinks, atime).

Normalmente, o armazenamento em nuvem "montado localmente" usa uma API baseada na web (REST-API)
que não oferece suporte ao `rsync`.

Para uma discussão sobre esse tópico, consulte [Backup on OneDrive or Google Drive](https://github.com/bit-team/backintime/issues/1166).

## Onde está o arquivo de log?

Existem três logs distintos gerados:

1. O *log de backup* contém mensagens específicas de um determinado backup em um
   determinado momento. Ele é armazenado dentro de cada backup e pode ser acessado pela
   GUI.

2. O *log de restauração* contém mensagens específicas de um determinado processo de restauração.
   Ele é exibido na GUI após cada restauração. Ele também está localizado na pasta
   `~/.local/share/backintime/` e é chamado de `restore_.log` para o perfil principal,
   `restore_2.log` para o segundo perfil e assim por diante.

3. O *log da aplicação* é gerado usando o recurso syslog do sistema operacional.
   Consulte [Como ler as entradas do log?](#como-ler-as-entradas-do-log) para
   obter mais detalhes.

## Como ler as entradas do log?

Tanto os arquivos de *log de backup* quanto os de *log de restauração* são arquivos de texto simples
e podem ser lidos dessa forma. Consulte [Onde está o arquivo de log?](#onde-esta-o-arquivo-de-log).
O *log da aplicação* é gerado por meio do [syslog](https://en.wikipedia.org/wiki/Syslog)
usando o identificador `backintime`. Dependendo da versão do *Back In Time* e da
distribuição GNU/Linux utilizada, há três maneiras de obter as entradas do log.

1. Em sistemas modernos:

   `journalctl --identifier backintime`

2. Com uma versão mais antiga do *Back In Time* (1.4.2 ou anterior):

   `journalctl --grep backintime`

3. Se aparecer a mensagem de erro `journalctl: command not found`, examine diretamente os arquivos do syslog:

   `sudo grep backintime /var/log/syslog`

## Como mover backups para um novo disco rígido?

Existem três soluções diferentes:

1. Clone o disco com `dd` e aumente a partição no novo disco para
   usar todo o espaço. Isso **destruirá todos os dados** no disco de destino!

   ```bash
    sudo dd if=/dev/sdbX of=/dev/sdcX bs=4M
   ```

   onde `/dev/sdbX` é a partição no disco de origem e
   `/dev/sdcX` é o disco de destino.

   Por fim, use `gparted` para redimensionar a partição.

2. Copie todos os arquivos usando `rsync -H`

   ```bash
    rsync -avhH --info=progress2 /SOURCE /DESTINATION
   ```

3. Copie todos os arquivos usando `tar`

   ```bash
   cd /SOURCE; tar cf - * | tar -C /DESTINATION/ -xf -
   ```

Certifique-se de que seu `/DESTINATION` contenha uma pasta chamada `backintime`,
que contém todos os backups. O BIT espera encontrar essa pasta e precisa dela
para importar backups existentes.

## Como mover um diretório grande na origem do backup sem duplicar os arquivos no backup?

Se você mover um arquivo/pasta no local de origem ("include") que é copiado pelo
BIT, ele tratará isso como um novo arquivo/pasta e criará um novo arquivo de backup
para ele (não fará hard-link com o antigo). Com diretórios grandes, isso pode ocupar
seu disco de backup muito rapidamente.

Você pode evitar isso movendo o arquivo/diretório também no último backup:

1. Crie um novo backup.

2. Mova o diretório original.

3. Mova manualmente a mesma pasta dentro do último backup do BiT da mesma maneira
   que você fez com a pasta original.

4. Crie um novo backup.

5. Remova o penúltimo backup (aquele em que você moveu o diretório manualmente) para
   evitar problemas de permissões ao tentar restaurar a partir desse backup.

## Como o *Back In Time* se compara ao *Timeshift*?

Back In Time e Timeshift são aplicações Linux que fornecem funcionalidades de backup.

1. Semelhanças

   * Ambos os programas são ferramentas de backup para Linux e criam backups em um momento específico.
   * Em ambos os programas, os backups são feitos usando rsync e hard-links, enquanto
     arquivos comuns são compartilhados entre os backups, o que economiza espaço em disco.
   * Ambos os programas oferecem GUI e CLI.
   * Ambos os programas permitem agendar backups regulares. Você também pode desabilitar
     completamente os backups agendados e criar backups manualmente quando necessário.

2. Back In Time

   * Ele foi projetado para proteger dados do usuário, incluindo quaisquer pastas ou arquivos.
   * Ele faz backup de determinadas pastas e arquivos que você deseja proteger. Arquivos modificados
     são transferidos, enquanto arquivos inalterados são vinculados à nova pasta. Você pode restaurar
     determinados arquivos e pastas.
   * É excelente para proteger seus dados pessoais.

3. Timeshift

   * Ele foi projetado para backups do sistema, permitindo restaurar todo o sistema Linux
     para um estado anterior sem afetar os dados do usuário.
   * Ele faz backup dos arquivos do sistema, não incluindo dados pessoais, a menos que o usuário
     configure isso explicitamente.
   * É bom para restaurar seu sistema após uma falha de atualização ou alteração de configuração.

## Recursos adicionais além da GUI e benefícios de usar o BIT

*Back In Time* armazena o nome do usuário e do grupo, o que torna possível restaurar as permissões
mesmo que o UID/GID tenha sido alterado. O usuário atual também é armazenado. Portanto, se o
Usuário/Grupo não existir no sistema durante a restauração, ele restaurará para o UID/GID antigo.

* Impedir suspensão/hibernação durante a criação do backup
* Desligar o sistema após o término
* Políticas de remoção e retenção para manter/remover backups antigos de acordo com regras razoáveis
* Suporte a Plugins e scripts de callback definidos pelo usuário

# Backups (snapshots)

## Backup ou snapshot?

Até a versão 1.6.0 do *Back In Time*, o termo *snapshot* era usado em vez de
*backup*. A partir da versão 1.6.0, esse termo foi alterado para *backup*. O motivo
foi não dar a impressão de que o *Back In Time* cria imagens de volumes de armazenamento.
Não se confunda com o tamanho de cada backup. Se você clicar com o botão direito
nas preferências de um backup em um gerenciador de arquivos e verificar seu tamanho,
parecerá que todos são backups completos (não incrementais). Mas esse não é
(necessariamente) o caso.

Para obter o tamanho correto de cada backup levando em consideração os
hard-links, você pode executar:

```bash
du -chd0 /media/<USER>/backintime/<HOST>/<USER>/1/*
```

Compare com a opção `-l` para contar os hard-links várias vezes:

```bash
du -chld0 /media/<USER>/backintime/<HOST>/<USER>/1/*
```

(`ncdu` não vem instalado por padrão, portanto não recomendo utilizá-lo.)

## Como usar checksum para encontrar arquivos corrompidos periodicamente?

A partir da versão 1.0.28 do BIT, existe uma nova opção de linha de comando
`--checksum` que faz o mesmo que *Use checksum to detect changes* nas
Options. Ela calculará checksums tanto para os arquivos de origem quanto para os
arquivos do último backup e usará somente esse checksum para decidir se um arquivo
foi alterado ou não. O modo normal (sem checksums) compara as datas de modificação
e os tamanhos dos arquivos, o que é muito mais rápido para detectar arquivos
alterados.

Como isso leva muito tempo, talvez você queira usar essa opção somente aos domingos
ou somente no primeiro domingo de cada mês. Nesse caso, desative o agendamento
do seu perfil. Em seguida, execute `crontab -e`

Para backups diários às 2h e `--checksum` todos os domingos, adicione:

```text
# min hour day month dayOfWeek command
0 2 * * 1-6 nice -n 19 ionice -c2 -n7 /usr/bin/backintime --backup-job >/dev/null 2>&1
0 2 * * Sun nice -n 19 ionice -c2 -n7 /usr/bin/backintime --checksum --backup-job >/dev/null 2>&1
```

Para usar `--checksum` somente no primeiro domingo de cada mês, adicione:

```text
# min hour day month dayOfWeek command
0 2 * * 1-6 nice -n 19 ionice -c2 -n7 /usr/bin/backintime --backup-job >/dev/null 2>&1
0 2 * * Sun [ "$(date '+\%d')" -gt 7 ] && nice -n 19 ionice -c2 -n7 /usr/bin/backintime --backup-job >/dev/null 2>&1
0 2 * * Sun [ "$(date '+\%d')" -le 7 ] && nice -n 19 ionice -c2 -n7 /usr/bin/backintime --checksum --backup-job >/dev/null 2>&1
```

Pressione <kbd>CTRL</kbd> + <kbd>O</kbd> para salvar e <kbd>CTRL</kbd> + <kbd>X</kbd> para sair
(se o seu editor for `nano`. Isso pode ser diferente dependendo do seu editor de
texto padrão).

## Qual é o significado dos 11 caracteres iniciais (por exemplo, "cf...p.....") nos meus logs de backup?

Eles vêm do `rsync` e indicam o que foi alterado e por quê. Consulte a seção
`--itemize-changes` na
[página de manual](https://download.samba.org/pub/rsync/rsync.1#opt--itemize-changes)
do `rsync`. Consulte também algumas
[explicações reformuladas no Stack Overflow](https://stackoverflow.com/a/36851784/4865723).

## Backup "COM ERROS": [E] 'rsync' terminou com código de saída 23: consulte 'man rsync' para mais detalhes

A [versão 1.4.0 do BiT (2023-09-14)](https://github.com/bit-team/backintime/releases/tag/v1.4.0)
introduziu a **avaliação dos códigos de saída do `rsync` para melhor reconhecimento
de erros**:

Antes dessa versão, os códigos de saída do `rsync` eram ignorados e somente os
arquivos de backup eram analisados em busca de erros (o que não encontra todos
os erros, por exemplo, links simbólicos quebrados registrados como
`symlink has no referent`).

Essa mensagem de "código de saída 23" pode aparecer no final dos logs de backup e
nos logs do BiT quando o `rsync` não conseguiu transferir alguns (ou até mesmo
todos) os arquivos. Consulte
[este comentário na issue 1587](https://github.com/bit-team/backintime/issues/1587#issuecomment-1856490208)
para obter uma lista de todos os motivos conhecidos para o código de saída 23
do `rsync`.

Atualmente, você pode ignorar esse erro depois de verificar o log completo do
backup para descobrir qual erro está oculto por trás do "código de saída 23"
(e possivelmente corrigi-lo — por exemplo, excluindo ou atualizando links
simbólicos quebrados).

Planejamos implementar um tratamento aprimorado do código de saída 23 no futuro
(provavelmente introduzindo avisos no log de backup).

## O que acontece quando removo um backup?

Cada backup é armazenado em um subdiretório com data dentro do "caminho completo
do backup" mostrado em Settings. Ele contém um diretório `backup` com todos
os arquivos, bem como um log da criação do backup e alguns outros detalhes.
Remover o backup remove esse diretório inteiro. Cada backup é independente
dos demais, portanto os outros backups não são afetados. No entanto, os dados
de arquivos idênticos não são armazenados de forma redundante em vários backups,
portanto remover um backup só recuperará o espaço utilizado pelos arquivos que
são exclusivos daquele backup.

## Como posso excluir pastas de cache para melhorar a velocidade do backup e reduzir o armazenamento?

**Por que excluir pastas de cache?**

As pastas de cache normalmente contêm arquivos temporários que não são necessários
para backups. Excluí-las pode melhorar significativamente a velocidade do backup
e reduzir o uso de armazenamento.

**Como excluir pastas de cache:**

1. Abra o Back in Time.

2. Vá para as configurações de **Exclude Patterns**:

   * Clique na aba "Exclude" na janela de configuração.
   * Clique no botão **Add** para criar um novo padrão de exclusão.

3. Adicione os seguintes padrões para excluir diretórios de cache comuns:

   ```plaintext
   .var/app/**/[Cc]ache/
   .var/app/**/media_cache/
   .mozilla/firefox/**/cache/
   .config/BraveSoftware/Brave-Browser/Default/Service Worker/CacheStorage/
   ```

**Explicação**:

* `/**/` corresponde a qualquer estrutura de diretórios que leve à pasta especificada.
* `[Cc]ache` corresponde a nomes de pastas com "Cache" em maiúsculas ou minúsculas.

4. Decida se deseja incluir ou excluir a própria pasta:

   * Para excluir apenas o conteúdo da pasta, use `/*` no final do padrão:

     ```plaintext
     .var/app/**/[Cc]ache/*
     ```
   * Para excluir a pasta e seu conteúdo, omita o `/*`:

     ```plaintext
     .var/app/**/[Cc]ache/
     ```

**Dicas para obter melhores resultados:**

* **Verifique os logs de backup**:
  Após executar um backup, examine os logs para identificar pastas adicionais
  que podem deixar o processo mais lento. Exemplos de entradas de log para
  arquivos de cache:

  ```plaintext
  [E] Skipping file /path/to/cache/file: Too many small files.
  ```

* **Personalize os padrões**:
  Ajuste os padrões de acordo com os aplicativos específicos que você utiliza.
  Por exemplo, modifique os caminhos para os navegadores ou outros softwares
  que você usa.

* **Teste os padrões de exclusão**:
  Teste seu backup depois de adicionar os padrões para garantir que eles
  funcionem conforme esperado.

## Como usar atributos estendidos do sistema de arquivos (xattr) para excluir arquivos/diretórios?

Consulte a [Issue #817](https://github.com/bit-team/backintime/issues/817) para
obter detalhes.

## Os compartilhamentos Samba são suportados? / O Samba oferece suporte a hard-links?

Não há uma resposta curta para isso. Depende da configuração do servidor Samba
e do sistema de arquivos do volume/disco rígido que ele utiliza.

Em geral, não é recomendado usar compartilhamentos Samba como destino de backup.
Use um perfil SSH em vez disso.

Leitura adicional:

* https://superuser.com/q/855946/486099
* https://github.com/bit-team/backintime/issues/1883

Se você encontrar regras claras para configurar o Samba de forma que ele funcione
com o *Back In Time* de maneira confiável, informe-nos os detalhes. Nós os
integraremos à documentação.

## Como o *Back In Time* lida com arquivos abertos ou alterados durante o backup?

**Explicação**

O Back In Time usa rsync para copiar os arquivos e diretórios especificados
na configuração para backup. O Rsync não bloqueia arquivos que estão abertos
ou sendo modificados e, portanto, o backup pode ser copiado em um estado
inconsistente. O Rsync lê um arquivo somente uma vez quando passa por ele e,
como resultado, apenas algumas alterações são capturadas pelo rsync. Isso pode
afetar arquivos como logs, caches de navegadores, bancos de dados ou imagens
de máquinas virtuais, nos quais inconsistências podem até mesmo levar à
corrupção de dados.

**Para reduzir esse risco, as seguintes abordagens podem ser consideradas:**

* **Snapshots do sistema de arquivos**
  Se estiver usando um sistema de arquivos como btrfs ou ZFS que tenha uma
  função de snapshot, ela pode ser usada em conjunto com o Back In Time.
  Snapshots do sistema de arquivos fornecem uma cópia somente leitura de um
  sistema de arquivos congelada em um ponto específico no tempo, o que garante
  a integridade dos dados mesmo para arquivos abertos/em alteração. Configure
  o Back In Time para fazer backup a partir do snapshot somente leitura desse
  sistema de arquivos.

* **Use exclusões**
  Se o sistema de arquivos não tiver snapshots disponíveis, uma solução pode
  ser excluir arquivos que são frequentemente abertos ou modificados ativamente.
  O comando `lsof` no GNU/Linux apresenta os arquivos abertos e os processos
  que os abriram como uma lista. Use essa lista como base para configurar
  a lista de exclusões do BIT.

* **Tratamento específico por aplicativo**
  Para aplicativos que abrem e modificam arquivos frequentemente, como bancos
  de dados ou máquinas virtuais, podem ser necessárias soluções específicas.
  Use a própria função de backup do banco de dados para criar uma cópia
  consistente e inclua essa cópia no backup do BIT. Produtos de máquinas
  virtuais normalmente têm a capacidade de criar snapshots do estado delas,
  que podem ser incluídos no BIT.

* **Escolha quando realizar o backup**
  Faça o backup em horários em que haja menos arquivos abertos, por exemplo,
  durante a noite.

# Restauração

## Após a restauração, tenho duplicatas com a extensão ".backup.20131121"

Isso acontece porque *Backup files on restore* em Options estava habilitado.
Essa é a configuração padrão para evitar a substituição de arquivos durante
a restauração.

Se você não precisar mais desses arquivos, poderá excluí-los. Abra um terminal
e execute:

```bash
find /path/to/files -regextype posix-basic -regex ".*\.backup\.[[:digit:]]\{8\}"
```

Verifique se esse comando listou corretamente todos os arquivos que você deseja
excluir e então execute:

```bash
find /path/to/files -regextype posix-basic -regex ".*\.backup\.[[:digit:]]\{8\}" -delete
```

## O Back In Time não encontra meus backups antigos no meu novo computador

O Back In Time anterior à versão 1.1.0 tinha uma opção chamada
*Auto Host/User/Profile ID* (oculta em *General* > *Advanced*) que sempre
usava o host e o nome de usuário atuais para o caminho completo do backup.

Ao (re)instalar seu computador, provavelmente você escolheu um nome de host ou
nome de usuário diferente daquele utilizado na máquina antiga. Com
*Auto Host/User/Profile ID* ativado, o Back In Time agora tenta encontrar
seus backups usando o novo host e nome de usuário dentro do caminho
`/path/to/backintime/`.

A opção *Auto Host/User/Profile ID* foi removida na versão 1.1.0 e posteriores.
Ela era bastante confusa e não acrescentava nada de útil.

Você tem três opções para corrigir isso:

* Desative *Auto Host/User/Profile ID* e altere *Host* e *User* para corresponderem
  à sua máquina antiga.

* Renomeie o caminho dos backups
  `/path/to/backintime/OLDHOSTNAME/OLDUSERNAME/profile_id` para corresponder ao
  novo host e nome de usuário.

* Atualize para uma versão mais recente do Back In Time (1.1.0 ou posterior).
  A opção *Auto Host/User/Profile ID* foi removida e a versão também inclui um
  assistente para restaurar a configuração a partir de um backup antigo na
  primeira inicialização.

# Agendamento

## Como funciona o agendamento 'Repeatedly'?

O *Back In Time* criará uma entrada no crontab que iniciará
`backintime --backup-job` a cada 15 minutos (ou uma vez por hora se o
agendamento estiver configurado para *weeks*). Com o comando
`--backup-job`, o *Back In Time* verificará se o perfil deve ser executado
nesse momento ou sairá imediatamente. Para isso, ele lerá o horário da última
execução bem-sucedida de
`~/.local/share/backintime/anacron/ID_PROFILENAME`.

Se esse horário for anterior ao período configurado, ele continuará criando
um backup.

Se o backup for concluído com sucesso e sem erros, o *Back In Time* gravará
o horário atual em `~/.local/share/backintime/anacron/ID_PROFILENAME`
(mesmo que *Repeatedly* não esteja selecionado). Portanto, se ocorrer um erro,
o *Back In Time* tentará novamente no próximo quarto de hora.

`backintime --backup` sempre criará um novo backup, independentemente de
quanto tempo tenha passado desde o último backup bem-sucedido.

## Se eu editar meu crontab e adicionar entradas adicionais, haverá algum problema para o BIT desde que eu não altere as entradas dele? O que ele procura no crontab para encontrar suas próprias entradas?

Você pode adicionar suas próprias entradas ao crontab como quiser. O
*Back In Time* não as modificará.

Ele identificará suas próprias entradas pela linha de comentário
`#Back In Time system entry, this will be edited by the gui:` e pelo comando
seguinte. Você não deve remover/alterar essa linha.

Se não houver agendamentos automáticos definidos, o *Back In Time* adicionará
uma linha de comentário extra:
`#Please don't delete these two lines, or all custom backintime entries are going to be deleted next time you call the gui options!`
que impedirá o *Back In Time* de remover agendamentos definidos pelo usuário.

## Posso usar um systemd timer em vez de cron?

Embora não exista suporte dentro do *Back In Time* para criar diretamente
um systemd timer, os usuários podem criar um timer e unidades de serviço
do usuário. Modelos são fornecidos abaixo. Opcionalmente, ajuste o valor
de `OnCalendar=` usando uma configuração válida. Consulte
[`man systemd.timer`](https://manpages.debian.org/testing/systemd/systemd.timer.5)
para obter mais informações.

**Timer**:

```ini
# ~/.config/systemd/user/backintime-backup-job.timer
[Unit]
Description=Start a backintime backup once daily

[Timer]
OnCalendar=daily
AccuracySec=1m
Persistent=true

[Install]
WantedBy=timers.target
```

**Service**:

```ini
# ~/.config/systemd/user/backintime-backup-job.service
[Unit]
Description=Run backintime backup generation

[Service]
Type=oneshot
ExecStart=/usr/bin/nice -n19 /usr/bin/ionice -c2 -n7 /usr/bin/backintime backup --background
```

# Problemas, erros e soluções

## Erros críticos sobre "`snapshots.ssh_check_commands` ou `snapshots.ssh.check_ping` não definidos como padrão..."

O *Back In Time* pode exibir erros críticos como estes no terminal, no syslog
ou na GUI:

```
CRITICAL DEPRECATED setting "profile1.snapshots.ssh.check_commands" not set
to default "true" detected in profile "Main profile" (1). Please contact 
the project and describe your use case and why you need this setting be disabled.

CRITICAL DEPRECATED setting "profile1.snapshots.ssh.check_ping" not set ...
```

Para perfis SSH, a aba *Expert Options* da caixa de diálogo *Manage profiles*
fornece estas duas opções, que são habilitadas por padrão:

* Check if remote host is online
* Check if remote host supports all necessary commands

Parece não haver um bom motivo para desabilitar essas opções. De acordo com a
issue [#2482](https://github.com/bit-team/backintime/issues/2482), essas opções
estão obsoletas e serão removidas.

O usuário tem a [opção de
entrar em contato](https://github.com/bit-team/backintime#contact--social) com
o projeto e apresentar objeções contra essa decisão. Faça isso se tiver um
bom motivo para desabilitar essas opções.

Para desabilitar os erros críticos, o arquivo de configuração precisa ser
editado manualmente. O arquivo normalmente está localizado em
`~/.config/backintime/config`. Depois de criar um backup desse arquivo,
abra-o em um editor de texto de sua escolha. Procure linhas como estas:

```ini
profile1.snapshots.ssh.check_commands=false
profile1.snapshots.ssh.check_ping=false
```

Altere o valor de `false` para `true` (em letras minúsculas!).

## OverflowError: Value 1702441408 out of range for UInt32

A GUI do *Back In Time* trava e essa exceção aparece na saída do terminal.
Sabe-se que isso acontece durante a restauração (#2084) e remoção (#2192)
de backups. Presume-se que também possa acontecer durante a criação de backups.

A hipótese atual é que o problema foi introduzido ou passou a ocorrer com
mais frequência desde a migração da versão 5 para a versão 6 do PyQt
(versão `1.5.0` do BIT).

A correção (PR #2099) foi lançada com a versão `1.6.0`.
Para usuários de versões anteriores, há uma pequena solução alternativa
descrita naquele [comentário da issue](https://github.com/bit-team/backintime/issues/2084#issuecomment-2787602155).

## `SettingsDialog` object has no attribute `cbCopyUnsafeLinks`

Ao adicionar um arquivo ou diretório que, na verdade, é um symlink à aba
*Include* da caixa de diálogo *Manage profiles*, a GUI do BIT trava e apresenta
o seguinte erro no terminal.

```pytb
Traceback (most recent call last):
  File "/usr/share/backintime/qt/manageprofiles/tab_include.py", line 185, in btn_include_add_clicked
    self._parent_dialog.cbCopyUnsafeLinks.isChecked() or
    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
AttributeError: 'SettingsDialog' object has no attribute 'cbCopyUnsafeLinks'
```

Introduzido na versão `1.5.3`. Corrigido na versão `1.6.0`. Consulte a issue
[#2279](https://github.com/bit-team/backintime/issues/2279).

Solução alternativa: não use um symlink, mas sim o destino para o qual ele aponta.

## WARNING: A backup is already running

O *Back In Time* usa arquivos de sinal como `worker<PID>.lock` para evitar
iniciar o mesmo backup duas vezes.

Normalmente, esse arquivo é excluído assim que o backup termina. Em alguns
casos, algo dá errado e o *Back In Time* é encerrado à força sem ter a
oportunidade de excluir esse arquivo de sinal.

Como o *Back In Time* só inicia um novo backup (para o mesmo perfil) se o
arquivo de sinal não existir, esse arquivo precisa ser excluído primeiro.
Mas, antes de fazer isso manualmente, é necessário garantir que o
*Back In Time* realmente não esteja mais em execução.

Isso pode ser verificado com:

```bash
ps aux | grep -i backintime
```
Se o comando mostrar algum processo do `backintime` que esteja realmente executando
um backup, **não exclua o arquivo de lock**. Aguarde o processo terminar.

Se não houver nenhum processo de backup em execução, procure o arquivo de lock
no diretório de dados do Back In Time e remova-o. Depois disso, o backup poderá
ser iniciado novamente.

## *Back in Time* não inicia e mostra: The application is already running! (pid: 1234567)

O *Back in Time* utiliza um arquivo de lock para impedir que várias instâncias
da aplicação sejam executadas simultaneamente.

Se a aplicação tiver sido encerrada de maneira inesperada, o arquivo de lock
pode permanecer no sistema mesmo depois que o processo terminou. Nesse caso,
o *Back in Time* acredita que ainda existe uma instância em execução.

Primeiro, verifique se realmente existe um processo do *Back in Time* em execução:

```bash
ps aux | grep -i backintime
```

Se não houver nenhum processo relevante em execução, remova o arquivo de lock
correspondente e tente iniciar o *Back in Time* novamente.

**Importante:** não remova arquivos de lock enquanto houver uma instância
realmente em execução, pois isso pode permitir que duas instâncias da aplicação
trabalhem simultaneamente sobre os mesmos dados.

## A mudança para o modo escuro ou claro no ambiente desktop é ignorada pelo BIT

O *Back In Time* utiliza o toolkit Qt para sua GUI. Dependendo do ambiente
desktop, do tema utilizado e da versão do Qt instalada, a alteração do tema
do sistema pode não ser detectada automaticamente.

Se a GUI do *Back In Time* não acompanhar a mudança entre o modo claro e o
modo escuro, tente reiniciar o *Back In Time*.

Se isso não resolver, verifique qual tema Qt está sendo utilizado pelo sistema
e se há alguma configuração ou variável de ambiente que esteja forçando um
tema específico.

Em alguns ambientes, variáveis como `QT_STYLE_OVERRIDE` podem influenciar
a aparência das aplicações Qt.

## A versão >= 1.2.0 funciona muito lentamente / arquivos inalterados são copiados

A partir da versão 1.2.0, o *Back In Time* passou a utilizar uma abordagem
diferente para verificar se os arquivos foram alterados.

Isso pode resultar em um comportamento mais lento em determinadas situações,
especialmente quando há uma grande quantidade de arquivos.

Primeiro, verifique se os arquivos estão realmente sendo copiados ou se o
`rsync` está apenas verificando os arquivos.

Observe o log do backup. As linhas produzidas pelo `rsync` podem ajudar a
identificar o que está acontecendo.

Uma das causas possíveis é a utilização de sistemas de arquivos ou destinos
de backup que não preservam corretamente informações como timestamps, tamanhos
de arquivo ou outros atributos necessários para que o `rsync` determine se
um arquivo foi alterado.

Também é possível utilizar a opção de checksum para fazer uma comparação
baseada no conteúdo dos arquivos, mas isso normalmente é significativamente
mais lento.

## O que acontece se eu colocar o computador em hibernação enquanto um backup está sendo executado?

Não é recomendado colocar o computador em hibernação enquanto um backup está
sendo executado.

O *Back In Time* tenta impedir que o sistema entre em suspensão ou hibernação
durante determinadas operações de backup, dependendo da configuração e do
ambiente utilizado.

Se o computador entrar em hibernação mesmo assim, o backup será interrompido
temporariamente. Depois que o computador voltar a funcionar, o processo poderá
continuar ou poderá ser necessário executá-lo novamente, dependendo de em que
ponto o backup estava quando o sistema foi suspenso.

Como o `rsync` trabalha arquivo por arquivo, arquivos que já foram transferidos
normalmente não precisam ser transferidos novamente durante uma nova execução.

## O que acontece se eu desligar o computador enquanto um backup está sendo executado ou se ocorrer uma queda de energia?

Se o computador for desligado de maneira inesperada enquanto um backup está
sendo executado, o backup poderá ficar incompleto.

Isso normalmente não significa que os backups anteriores serão corrompidos.
Cada backup é armazenado separadamente.

Ao executar o próximo backup, o *Back In Time* poderá continuar o trabalho
usando os dados existentes, dependendo do estado em que o backup interrompido
foi deixado.

Se o backup incompleto não puder ser utilizado, ele poderá ser removido
manualmente e um novo backup poderá ser criado.

Uma queda de energia também pode causar problemas no sistema de arquivos
ou no dispositivo de armazenamento. Nesse caso, o problema não é específico
do *Back In Time* e o sistema de arquivos deve ser verificado de acordo com
as ferramentas apropriadas para ele.

## O que acontece se não houver espaço suficiente em disco para o backup atual?

Se o destino do backup ficar sem espaço, o `rsync` não conseguirá copiar
todos os arquivos.

O backup será marcado como contendo erros e o log deverá indicar que não foi
possível concluir determinadas operações.

O *Back In Time* não pode criar espaço adicional no dispositivo de destino.
É necessário liberar espaço ou utilizar um dispositivo com capacidade maior.

Antes de excluir backups antigos, lembre-se de que backups diferentes podem
compartilhar os mesmos dados por meio de hard-links. Portanto, remover um
backup não necessariamente liberará uma quantidade de espaço equivalente ao
tamanho aparente daquele backup.

## Compatibilidade com NTFS

O NTFS pode ser utilizado como destino para determinados tipos de backup,
mas existem limitações importantes.

O *Back In Time* depende de recursos do sistema de arquivos Linux, incluindo
hard-links e metadados de arquivos. Dependendo da forma como o NTFS está
montado e do driver utilizado, alguns desses recursos podem não funcionar
corretamente.

Isso pode resultar em problemas durante a criação ou restauração de backups.

Para obter a melhor compatibilidade, recomenda-se utilizar um sistema de
arquivos nativo do Linux no destino do backup, como `ext4`.

Se o dispositivo precisar permanecer compatível com Windows, considere utilizar
um destino Linux acessível por SSH em vez de montar diretamente uma partição
NTFS.

## A GUI não é dimensionada corretamente em monitores de alta resolução ou 4K

Em monitores de alta resolução, a GUI pode aparecer muito pequena ou apresentar
problemas de dimensionamento.

O comportamento depende do ambiente desktop, da versão do Qt e da configuração
de escala utilizada pelo sistema.

O Qt possui variáveis de ambiente que podem ser utilizadas para ajustar o
dimensionamento de aplicações.

Por exemplo:

```bash
export QT_SCALE_FACTOR=2
```

O valor adequado depende da resolução e da configuração do monitor.

Se o problema ocorrer somente no *Back In Time*, verifique também se alguma
variável de ambiente ou configuração específica está sendo aplicada à aplicação.

## Ícone da bandeja ou outros ícones não são exibidos corretamente

A aparência dos ícones da bandeja do sistema depende do ambiente desktop e
do suporte a tray icons fornecido por ele.

Em alguns ambientes, especialmente aqueles que utilizam implementações
diferentes da área de notificação, o ícone do *Back In Time* pode não aparecer
ou pode aparecer incorretamente.

Isso não necessariamente indica um problema no *Back In Time*.

Verifique se o ambiente desktop oferece suporte à área de notificação utilizada
pela versão do Qt instalada.

Também pode ser necessário instalar um componente adicional do ambiente desktop
responsável pela área de notificação ou pelo suporte a StatusNotifierItem.

## Cofre de senhas não funciona e o BiT esquece as senhas (problemas com o backend do keyring)

O *Back In Time* utiliza um `keyring` para armazenar determinadas credenciais
de maneira segura.

O backend utilizado depende do sistema operacional e do ambiente desktop.

Se o *Back In Time* esquecer uma senha após ser reiniciado, pode haver um
problema com o backend do `keyring`.

Primeiro, verifique se existe um serviço de gerenciamento de credenciais
funcionando no seu ambiente desktop.

Dependendo do sistema, isso pode ser, por exemplo:

* GNOME Keyring
* KWallet
* outro backend compatível com o Python `keyring`

Também pode ser útil verificar qual backend o Python está selecionando:

```bash
python3 -c "import keyring; print(keyring.get_keyring())"
```

Se o resultado indicar um backend que não está funcionando corretamente,
a configuração do `keyring` poderá precisar ser corrigida.

Não é recomendado armazenar senhas diretamente em arquivos de configuração
sem criptografia apenas para contornar um problema no `keyring`.

# Desatualizado

As seções abaixo descrevem problemas que podem afetar versões antigas do
*Back In Time* ou versões antigas de suas dependências.

## Segmentation fault ao sair

Versões antigas do *Back In Time* podiam apresentar um `segmentation fault`
ao sair da aplicação.

Esse problema foi corrigido em versões posteriores.

Se você encontrar esse problema, primeiro atualize o *Back In Time* para uma
versão atual.

Caso continue ocorrendo, consulte as issues existentes no projeto e forneça
informações sobre a versão do *Back In Time*, a distribuição GNU/Linux, a
versão do Python e do Qt e o traceback ou mensagem de erro disponível.

## Incompatibilidade com rsync >= 3.2.4

Algumas versões antigas do *Back In Time* apresentavam problemas de
compatibilidade com versões mais recentes do `rsync`.

Se você estiver utilizando uma versão antiga do *Back In Time* junto com
`rsync` 3.2.4 ou superior, poderá encontrar erros durante a criação ou
restauração de backups.

A solução recomendada é atualizar o *Back In Time* para uma versão que
ofereça suporte à versão do `rsync` instalada no sistema.

# Configuração específica de hardware

## Como usar o BIT com um NAS Ugreen?

O *Back In Time* pode fazer backup para um NAS Ugreen utilizando uma conexão
SSH.

Primeiro, certifique-se de que o servidor SSH esteja habilitado no NAS.

Depois, crie um perfil SSH no *Back In Time*:

1. Abra **Manage profiles**.
2. Crie um novo perfil.
3. Selecione **SSH** como o tipo de conexão.
4. Informe o endereço IP ou hostname do NAS.
5. Informe o usuário utilizado para acessar o NAS.
6. Configure a autenticação SSH.
7. Escolha o diretório de destino do backup.

Teste a conexão SSH antes de executar o primeiro backup.

Você também pode verificar a conexão manualmente:

```bash
ssh USER@NAS
```

Depois de confirmar que o SSH funciona, teste o `rsync` para garantir que o
usuário utilizado tenha as permissões necessárias no diretório de destino.

## Como usar um NAS QNAP QTS com o BIT via SSH

Para utilizar um QNAP como destino SSH, primeiro habilite o serviço SSH no
QNAP QTS.

No QNAP, abra as configurações de rede/serviços e habilite o acesso SSH.

Em seguida, configure um perfil SSH no *Back In Time*.

Use o endereço do NAS, o usuário e a porta SSH configurada no QNAP.

Teste primeiro:

```bash
ssh USER@NAS
```

Depois teste se o `rsync` está disponível no servidor:

```bash
ssh USER@NAS rsync --version
```

Se o comando não estiver disponível, o *Back In Time* não poderá utilizar
esse host como destino SSH até que um `rsync` compatível esteja disponível.

## Como usar o Synology DSM 5 com o BIT via SSH

Para utilizar um Synology NAS como destino, habilite o serviço SSH no DSM.

No DSM 5, isso pode ser encontrado nas configurações de **Control Panel**
relacionadas ao terminal/SSH.

Depois de habilitar o SSH, configure um perfil SSH no *Back In Time*.

Teste a conexão manualmente:

```bash
ssh USER@SYNOLOGY
```

Depois verifique se o `rsync` pode ser executado no Synology:

```bash
ssh USER@SYNOLOGY rsync --version
```

O usuário utilizado pelo *Back In Time* precisa ter permissão de leitura nas
pastas de origem remotas e de escrita no destino do backup.

## Como usar o Synology DSM 6 com o BIT via SSH

No DSM 6, habilite o SSH em:

**Control Panel → Terminal & SNMP → Enable SSH service**

Depois configure o perfil SSH no *Back In Time*.

Teste:

```bash
ssh USER@SYNOLOGY
```

E verifique o `rsync`:

```bash
ssh USER@SYNOLOGY rsync --version
```

### Usando uma porta não padrão

Se o SSH do Synology estiver configurado para utilizar uma porta diferente
da porta padrão `22`, informe essa porta nas configurações do perfil SSH
do *Back In Time*.

Por exemplo, se o servidor estiver utilizando a porta `2222`, o teste manual
seria:

```bash
ssh -p 2222 USER@SYNOLOGY
```

No *Back In Time*, configure a mesma porta no campo correspondente.

## Como usar o Synology DSM 7 com o BIT via SSH

No DSM 7, habilite o SSH no Synology e configure o perfil correspondente no
*Back In Time*.

Teste a conexão:

```bash
ssh USER@SYNOLOGY
```

Depois confirme que o `rsync` está disponível:

```bash
ssh USER@SYNOLOGY rsync --version
```

### Usando uma porta SSH não padrão com um NAS Synology

Se você estiver utilizando uma porta SSH diferente da `22`, configure essa
porta no perfil SSH do *Back In Time*.

O teste manual pode ser feito com:

```bash
ssh -p PORT USER@SYNOLOGY
```

Substitua `PORT` pela porta configurada no Synology.

### "sshfs: No such file or directory" ao usar o BIT, mas o SSH manual com rsync funciona

Se o SSH funcionar manualmente e o `rsync` também puder ser executado,
mas o *Back In Time* apresentar:

```text
sshfs: No such file or directory
```

pode haver um problema relacionado ao `sshfs` ou à forma como o Synology
está configurado.

O *Back In Time* pode utilizar `sshfs` para determinadas operações.

Verifique se o `sshfs` está instalado no computador cliente:

```bash
which sshfs
```

Se o comando não retornar um caminho, instale o pacote `sshfs` utilizando
o gerenciador de pacotes da sua distribuição.

# Synology: usar um volume diferente para o backup

Se o Synology possuir vários volumes, o caminho utilizado no perfil SSH precisa
apontar para o volume correto.

Por exemplo:

```text
/volume1/backintime
```

ou:

```text
/volume2/backintime
```

Verifique o caminho real do volume no Synology antes de configurar o perfil.

O usuário utilizado pelo *Back In Time* também precisa ter as permissões
necessárias nesse volume.

## Como usar o Western Digital MyBook World Edition com o BIT via ssh?

O Western Digital MyBook World Edition utiliza uma versão antiga de seu
software e possui limitações importantes.

Para utilizar o dispositivo como destino do *Back In Time*, o SSH precisa
estar habilitado e o sistema remoto precisa disponibilizar um `rsync`
compatível.

Teste primeiro:

```bash
ssh USER@MYBOOK
```

Depois:

```bash
ssh USER@MYBOOK rsync --version
```

Se o `rsync` não estiver disponível ou for incompatível, será necessário
instalá-lo ou utilizar outro método de acesso compatível.

Como esse dispositivo é antigo e seu software não é mais mantido como os
sistemas NAS atuais, podem existir limitações que não podem ser resolvidas
pelo *Back In Time*.

# Projeto, contribuição e mais

## Por que preciso me apresentar?

O *Back In Time* é um projeto open source mantido por colaboradores.

Ao contribuir com o projeto, é útil que os demais colaboradores saibam quem
está participando e quais são seus interesses.

Uma apresentação também ajuda a comunidade a entender o contexto de uma
contribuição, especialmente quando a pessoa ainda não participou anteriormente
do projeto.

## Posso contribuir sem usar o software?

Sim.

Você não precisa ser um usuário avançado do *Back In Time* para contribuir.

Existem muitas maneiras de ajudar, incluindo:

* melhorar a documentação;
* traduzir textos;
* testar novas versões;
* relatar problemas;
* revisar Pull Requests;
* melhorar testes;
* ajudar outros usuários;
* contribuir com código.

Contribuições que não envolvem programação também são muito úteis.

## Vocês podem atribuir isso a mim?

Sim, quando fizer sentido.

Se você encontrou uma issue que deseja resolver, informe isso na própria issue
para que os demais colaboradores saibam que você está trabalhando nela.

Isso ajuda a evitar que várias pessoas trabalhem simultaneamente na mesma tarefa.

Entretanto, uma issue atribuída não significa necessariamente que ninguém mais
possa contribuir. Se você não puder continuar trabalhando nela, informe a equipe
para que outra pessoa possa assumir.

## Posso usar menções com @ livremente em issues ou PRs?

Use menções com `@` somente quando houver um motivo para chamar a atenção
de uma pessoa específica.

Menções desnecessárias podem gerar notificações para pessoas que não precisam
participar da discussão.

Se uma pessoa já estiver acompanhando uma issue ou Pull Request, normalmente
não há necessidade de mencioná-la repetidamente.

## Posso aumentar minha contagem de commits?

Não faça commits artificiais apenas para aumentar sua contagem.

O número de commits não é uma métrica importante para avaliar a qualidade
da contribuição.

É preferível fazer commits que representem mudanças reais, claras e úteis.

## Posso enviar contribuições geradas por IA?

Contribuições produzidas com auxílio de ferramentas de IA devem seguir as
mesmas regras das demais contribuições.

O autor continua sendo responsável pelo conteúdo enviado.

Antes de criar um Pull Request, revise cuidadosamente o resultado gerado
pela IA, verifique sua correção e certifique-se de que você entende a alteração.

Não envie automaticamente grandes quantidades de código ou documentação
geradas por IA sem verificar seu conteúdo.

Também devem ser respeitadas as licenças e os direitos autorais aplicáveis.

## Opções alternativas de instalação

O *Back In Time* é disponibilizado em diferentes formatos dependendo da
distribuição GNU/Linux.

Além dos pacotes fornecidos oficialmente pela distribuição, podem existir
repositórios ou métodos de instalação mantidos por terceiros.

Tenha cuidado ao instalar pacotes de fontes não oficiais.

Pacotes de terceiros podem estar desatualizados, conter alterações próprias
ou utilizar versões diferentes das dependências.

## Suporte a formatos específicos de pacotes (deb, rpm, Flatpack, AppImage, Snaps, PPA, …)

O projeto *Back In Time* fornece suporte aos formatos de pacotes que são
necessários e mantidos pelo projeto.

Não é possível garantir que todos os formatos de empacotamento existentes
sejam suportados oficialmente.

Para saber quais métodos de instalação estão disponíveis atualmente, consulte
a documentação de instalação do projeto e os arquivos de configuração de
empacotamento correspondentes.

## O BIT realmente não é suportado pelo Canonical Ubuntu?

O *Back In Time* é um projeto independente e não é desenvolvido pela
Canonical.

A disponibilidade de um pacote nos repositórios do Ubuntu não significa que
o projeto *Back In Time* seja mantido pela Canonical.

Problemas relacionados ao pacote distribuído pelo Ubuntu podem precisar ser
tratados com os responsáveis pelo empacotamento da distribuição.

## Mover o projeto para um host de código alternativo (por exemplo, Codeberg, GitLab, …)

O código-fonte do *Back In Time* é hospedado atualmente em uma plataforma
de desenvolvimento que fornece Git, issues, Pull Requests e outros recursos
necessários ao projeto.

A possibilidade de mover o projeto para outro host de código depende de
diversos fatores, incluindo recursos disponíveis, histórico, comunidade,
integrações e manutenção.

Uma mudança desse tipo não é uma decisão simples e precisa ser discutida
pela equipe do projeto.

## Como revisar um Pull Request

Ao revisar um Pull Request, primeiro leia a descrição e entenda qual problema
a alteração pretende resolver.

Depois:

1. Leia as alterações apresentadas no diff.
2. Verifique se o comportamento implementado corresponde à descrição.
3. Procure possíveis efeitos colaterais.
4. Verifique se testes existentes continuam funcionando.
5. Quando apropriado, execute os testes localmente.
6. Verifique alterações na documentação.
7. Confira se os novos arquivos seguem as convenções do projeto.
8. Informe claramente qualquer problema encontrado.

Uma revisão não precisa encontrar problemas obrigatoriamente. Se a alteração
estiver correta, você também pode informar isso.

# Testes e compilação

## Testes relacionados a SSH são ignorados

Alguns testes relacionados a SSH são ignorados por padrão porque precisam
de um servidor SSH disponível.

Para executar esses testes, é necessário configurar um servidor SSH adequado
para os testes.

Consulte a seção seguinte para obter instruções sobre como configurar esse
ambiente.

## Configurar um servidor SSH para executar testes unitários

Para executar os testes que dependem de SSH, configure um servidor SSH local
ou outro servidor de teste acessível pelo computador onde os testes estão
sendo executados.

O servidor precisa permitir a autenticação utilizada pelos testes e fornecer
um ambiente no qual o `rsync` possa ser executado.

Certifique-se de que o servidor de teste não contenha dados importantes.
Os testes podem criar, alterar e remover arquivos no diretório utilizado.

Depois de configurar o servidor, atualize a configuração dos testes para
apontar para ele e execute a suíte de testes correspondente.

Antes de executar os testes, confirme manualmente que a conexão SSH funciona:

```bash
ssh USER@HOST
```

E confirme que o `rsync` está disponível:

```bash
ssh USER@HOST rsync --version
```
Se a saída mostrar uma instância do *Back In Time* em execução, é necessário
aguardar até que ela termine ou encerrá-la usando `kill <process id>`.

Para obter mais detalhes, consulte a documentação para desenvolvedores:
[Usage of control files (locks, flocks, logs and others)](doc/maintain/4_Control_files_usage_%28locks_flocks_logs_and_others%29.md)

## *Back in Time* não inicia e mostra: The application is already running! (pid: 1234567)

Essa mensagem ocorre quando o *Back In Time* já está em execução ou não foi
encerrado normalmente (por exemplo, devido a uma falha) e não conseguiu
excluir seu arquivo de lock da aplicação.

Antes de excluir esse arquivo manualmente, certifique-se de que nenhum processo
do `backintime` esteja em execução usando:

```bash
ps aux | grep -i backintime
```

Caso contrário, encerre o processo. Depois disso, procure na pasta
`~/.local/share/backintime` o arquivo `app.lock.pid` e exclua-o.

Para obter mais detalhes, consulte a documentação para desenvolvedores:
[Usage of control files (locks, flocks, logs and others)](doc/maintain/4_Control_files_usage_%28locks_flocks_logs_and_others%29.md)

## A mudança para o modo escuro ou claro no ambiente desktop é ignorada pelo BIT

Depois de reiniciar o *Back In Time*, ele deverá se adaptar ao tema de cores
atualmente utilizado pelo desktop.

Isso acontece porque o Qt não detecta alterações de tema automaticamente.
[Existem soluções alternativas conhecidas](https://stackoverflow.com/q/75457687),
mas elas geram uma quantidade relativamente grande de código e, em nossa
opinião, não valem o esforço.

## A versão >= 1.2.0 funciona muito lentamente / Arquivos inalterados são incluídos no backup

Depois de atualizar para a versão >= 1.2.0, o BiT faz um backup
(quase) completo porque as permissões dos arquivos são tratadas de maneira
diferente. Antes da versão 1.2.0, todas as permissões dos arquivos de destino
eram definidas como `-rw-r--r--`. Na versão 1.2.0, o `rsync` é executado com
a opção `--perms`, que instrui o `rsync` a preservar as permissões do arquivo
de origem.

É por isso que tantos arquivos parecem ter sido alterados.

Se você não gostar desse novo comportamento, pode usar **"Expert Options"**
→ **"Paste additional options to rsync"** para adicionar o valor
`--no-perms --no-group --no-owner` nesse campo.

## O que acontece se eu colocar o computador em hibernação enquanto um backup está sendo executado?

O *Back In Time* impedirá a suspensão/hibernação automática enquanto um
backup/restauração estiver em execução. Se você forçar manualmente a
hibernação, isso congelará o processo atual. Ele continuará assim que você
reativar o sistema.

## O que acontece se eu desligar o computador enquanto um backup está sendo executado ou se ocorrer uma queda de energia?

Isso encerrará o processo atual. O novo backup permanecerá na pasta
`new_snapshot`. Dependendo do estado em que o processo estava no momento
do encerramento, o próximo backup agendado poderá continuar o
`new_snapshot` restante ou removê-lo primeiro e iniciar um novo.

## O que acontece se não houver espaço suficiente em disco para o backup atual?

O *Back In Time* tentará criar um novo backup, mas o `rsync` falhará quando
não houver espaço suficiente.

Dependendo da configuração **`Continue on errors`**, o backup que falhou
será mantido e marcado como **`With Errors`**, ou será removido.

Por padrão, o *Back In Time* finalmente removerá os backups mais antigos até
que haja novamente mais de 1 GiB de espaço livre.

## Compatibilidade com NTFS

Embora dispositivos formatados com o sistema de arquivos NTFS possam, em geral,
ser utilizados com o *Back In Time*, existem algumas limitações que devem ser
levadas em consideração.

Sistemas de arquivos NTFS não oferecem suporte aos seguintes caracteres em
nomes de arquivos ou diretórios:

```text
< (less than)
> (greater than)
: (colon)
" (double quote)
/ (forward slash)
\ (backslash)
| (vertical bar or pipe)
? (question mark)
* (asterisk)
```

Se o *Back In Time* tentar copiar arquivos cujo nome contenha esses caracteres,
uma mensagem de erro "Invalid argument (22)" será exibida.

É recomendado utilizar somente dispositivos formatados com sistemas de
arquivos no estilo Unix (como ext4).

Para obter mais informações, consulte [esta página da Microsoft](https://learn.microsoft.com/en-us/windows/win32/fileio/naming-a-file#naming-conventions).

## A GUI não é dimensionada corretamente em monitores de alta resolução ou 4K

Os detalhes técnicos são complexos e muitos componentes do sistema operacional
estão envolvidos. O próprio BIT não está envolvido nisso e também não é
responsável pelo problema.

Várias abordagens podem ajudar:

* Verifique as configurações do seu ambiente desktop ou window manager
  relacionadas ao dimensionamento.
* Como o BIT utiliza Qt para sua GUI, modificar as variáveis de ambiente
  `QT_SCALE_FACTOR` ou `QT_AUTO_SCREEN_SCALE_FACTOR` pode ajudar.

Consulte [este artigo](https://doc.qt.io/qt-6/highdpi.html) e a
[Issue #1946](https://github.com/bit-team/backintime/issues/1946) para obter
mais detalhes.

## O ícone da bandeja ou outros ícones não são exibidos corretamente

**Status: Corrigido na v1.4.0**

A ausência de temas e ícones compatíveis com Qt instalados pode causar esse
efeito. O *Back In Time* pode ativar o tema incorreto nesse caso, fazendo com
que alguns ícones não sejam exibidos. Uma correção para a próxima versão
estava sendo preparada.

Como solução adequada, verifique as configurações do Linux (**Appearance,
Styles, Icons**) e instale todos os pacotes de temas e ícones correspondentes
ao estilo que você prefere por meio do seu gerenciador de pacotes.

Consulte as issues [#1306](https://github.com/bit-team/backintime/issues/1306)
e [#1364](https://github.com/bit-team/backintime/issues/1364).

## O cofre de senhas não funciona e o BiT esquece as senhas (problemas com o backend do keyring)

**Status: Corrigido na v1.3.3 (em sua maior parte) e na v1.4.0**

O *Back in Time* oferece suporte somente a determinados backends
"conhecidos como bons" para definir e consultar senhas armazenadas no cofre
de senhas da sessão do usuário, utilizando a biblioteca
[`keyring`](https://github.com/jaraco/keyring).

Habilitar um `keyring` compatível requer configuração manual de um arquivo
de configuração até que, por exemplo, exista uma GUI de configurações para
isso.

Os problemas do `keyring` podem ser reconhecidos na saída DEBUG (com o
argumento de linha de comando `--debug`) por mensagens como:

```text
DEBUG: [common/tools.py:829 keyringSupported] No appropriate keyring found. 'keyring.backends...' can't be used with BackInTime
DEBUG: [common/tools.py:829 keyringSupported] No appropriate keyring found. 'keyring.backends.chainer' can't be used with BackInTime
```

Para diagnosticar e solucionar o problema, siga estas etapas em um terminal:

```bash
# Show default backend
python3 -c "import keyring.util.platform_; print(keyring.get_keyring().__module__)"

# List available backends:
keyring --list-backends

# Find out the config file folder:
python3 -c "import keyring.util.platform_; print(keyring.util.platform_.config_root())"

# Create a config file named "keyringrc.cfg" in this folder with one of the available backends (listed above)
[backend]
default-keyring=keyring.backends.kwallet.DBusKeyring
```

Consulte também a issue [#1321](https://github.com/bit-team/backintime/issues/1321).

## Desatualizado

### Segmentation fault ao sair

Esse problema existia pelo menos desde a versão 1.2.1 e, espera-se, tenha
sido corrigido na versão 1.5.0.

Em todas as versões afetadas, ele não impacta a funcionalidade do
*Back In Time* nem compromete a integridade dos backups. Pode ser ignorado
com segurança.

No entanto, relate o erro caso ele ocorra na versão 1.5.0 ou mais recente.

Consulte também:

* [#1768](https://github.com/bit-team/backintime/pull/1768)
* [#1095](https://github.com/bit-team/backintime/issues/1095)

### Incompatibilidade com rsync 3.2.4 ou mais recente

**Status: Corrigido na v1.3.3**

A versão (`1.3.2`) e versões anteriores do *Back In Time* são incompatíveis
com `rsync >= 3.2.4`
([#1247](https://github.com/bit-team/backintime/issues/1247)).

Se você usa `rsync >= 3.2.4` e `backintime <= 1.3.2`, existe uma solução
alternativa. Adicione `--old-args` em
[*Expert Options* / *Additional options to rsync*](https://backintime.readthedocs.io/en/latest/settings.html#expert-options).

Observe que algumas distribuições GNU/Linux (por exemplo, Manjaro) utilizam
uma solução alternativa com a variável de ambiente `RSYNC_OLD_ARGS` em seus
pacotes específicos da distribuição para o *Back In Time*. Nesse caso, talvez
você não encontre nenhum problema.

# Configuração específica de hardware

## Como usar o BIT com um NAS Ugreen?

Consulte [esta publicação de blog](https://www.ruinelli.ch/how-to-use-backintime-with-an-ugreen-nas)
de George Ruinelli @caco3.

## Como usar um NAS QNAP QTS com o BIT via SSH

Para usar o *BackInTime* via SSH com um NAS QNAP, ainda é necessário realizar
algumas etapas no terminal.

**AVISO**:

**NÃO** use as alterações para `sh` sugeridas em `man backintime`.
Isso danificará a conta de administrador do QNAP (e ainda mais).
Alterar `sh` para outro usuário também não faz sentido, pois o SSH funciona
somente com a conta de administrador do QNAP!

Teste este tutorial e forneça feedback!

1. Ative o prefixo SSH: `PATH=/opt/bin:/opt/sbin:\$PATH` em `Expert
   Options`

2. Use `admin` (administrador padrão do QNAP) como usuário remoto. Somente
   esse usuário pode se conectar por SSH. Ative também o `SFTP` no QNAP,
   na página de configurações de SSH.

3. O caminho deve ser algo como `/share/Public/`

4. Crie o par de chaves pública/privada para o login sem senha com o usuário
   que você utiliza para o *BackInTime* e copie a chave pública para o NAS.

   ```bash
   ssh-keygen -t rsa
   ssh-copy-id -i ~/.ssh/id_rsa.pub  <REMOTE_USER>@<HOST>
   ```

Para corrigir a mensagem sobre `find PATH -type f -exec` não ser suportado,
é necessário instalar o `Entware-ng`. O QNAP QTS é baseado em Linux, mas
alguns de seus pacotes possuem funcionalidades limitadas. O mesmo acontece
com alguns dos pacotes necessários ao *BackInTime*.

Siga [estas instruções de instalação](https://github.com/Entware-ng/Entware-ng/wiki/Install-on-QNAP-NAS)
para instalar o `Entware-ng` no seu NAS QNAP.

Como ainda não existe uma interface web para o `Entware-ng`, você precisa
configurá-lo por SSH no NAS.

Alguns pacotes serão instalados por padrão, por exemplo, `findutils`.

Faça login no NAS e atualize o banco de dados e os pacotes do `Entware-ng` com:

```bash
ssh <REMOTE_USER>@<HOST>
opkg update
opkg upgrade
```

Por fim, instale as versões atuais dos pacotes `bash`, `coreutils` e
`rsync`:

```bash
opkg install bash coreutils rsync
```

Agora a mensagem de erro deverá desaparecer e você deverá conseguir fazer
o primeiro backup com o *BackInTime*.

O *BackInTime* altera as permissões no caminho do backup. O proprietário do
backup possui permissão de leitura; os outros usuários não têm acesso.

Isso pode mudar com versões mais recentes do *BackInTime* ou do QNAP QTS!

## Como usar o Synology DSM 5 com o BIT via SSH

**Problema**

O *BackInTime* não pode usar o Synology DSM 5 diretamente porque a conexão
SSH com o NAS aponta para um sistema de arquivos raiz diferente daquele usado
pelo SFTP. Com SSH, você acessa a raiz real; com SFTP, acessa uma raiz falsa
(`/volume1`).

**Solução**

Monte `/volume1/backups` em `/volume1/volume1/backups`.

**Sugestão**

O DSM 5 já não está realmente atualizado e pode representar um risco de
segurança. É altamente recomendado atualizar para o DSM 6! Além disso,
a configuração com DSM 6 é muito mais fácil!

1. Crie um novo volume chamado `volume1` (ele já deveria existir; caso
   contrário, crie-o).

2. Ative o **User Home Service** (**Control Panel / User**).

3. Crie um novo compartilhamento chamado `backups` em `volume1`.

4. Crie um novo compartilhamento chamado `volume1` em `volume1`
   (ele deve ter o mesmo nome).

5. Crie um novo usuário chamado `backup`.

6. Dê ao usuário `backup` permissões de **Read/Write** nos compartilhamentos
   `backups` e `volume1` e também permissão para FTP.

7. Ative o SSH (**Control Panel / Terminal & SNMP / Terminal**).

8. Ative o SFTP (**Control Panel / File Service / FTP / SFTP**).

9. Ative o serviço rsync (**Control Panel / File Service / rsync**).

10. A partir do DSM 5.1: ative o **Backup Service**
    (**Backup & Replication / Backup Service**).
    (Isso aparentemente não está mais disponível/não é mais necessário
    no DSM 6!)

11. Faça login como root via SSH.

12. Modifique o shell do usuário `backup`. Defina-o como `/bin/sh`
    (`vi /etc/passwd`; depois navegue até a linha que começa com `backup`,
    pressione :kbd:`I` para entrar no **Insert Mode**, substitua
    `/sbin/nologin` por `/bin/sh` e, finalmente, salve e saia pressionando
    :kbd:`ESC` e digitando `:wq` seguido de :kbd:`Enter`).

    Essa etapa pode precisar ser repetida após uma atualização importante
    do Synology DSM!

    **Observação:** este é um hack bastante inadequado! É recomendado atualizar
    para o DSM 6, que não precisa mais disso!

13. Crie um novo diretório `/volume1/volume1/backups`:

    ```bash
    mkdir /volume1/volume1/backups
    ```

14. Monte `/volume1/backups` em `/volume1/volume1/backups`:

    ```bash
    mount -o bind /volume1/backups /volume1/volume1/backups
    ```

15. Para montá-lo automaticamente, crie o script
    `/usr/syno/etc/rc.d/S99zzMountBind.sh`:

    ```bash
    #!/bin/sh

     start()
     {
            /bin/mount -o bind /volume1/backups /volume1/volume1/backups
     }

     stop()
     {
            /bin/umount /volume1/volume1/backups
     }

     case "$1" in
            start) start ;;
            stop) stop ;;
            *) ;;
     esac
    ```

    **Observação:** se a pasta `/usr/syno/etc/rc.d` não existir, verifique
    se `/usr/local/etc/rc.d/` existe. Se existir, coloque o arquivo lá.
    (Depois que atualizei para o Synology DSM 6.0beta, a primeira pasta já não
    existia.)

    Certifique-se de que a permissão de execução do arquivo esteja definida;
    caso contrário, ele não será executado na inicialização!

    Para torná-lo executável, execute:

    `chmod +x /usr/local/etc/rc.d/S99zzMountBind.sh`

16. Na workstation em que você pretende usar o BIT, crie chaves SSH para
    o usuário `backup` e envie a chave pública para o NAS:

    ```bash
    ssh-keygen -t rsa -f ~/.ssh/backup_id_rsa
    ssh-add ~/.ssh/backup_id_rsa
    ssh-copy-id -i ~/.ssh/backup_id_rsa.pub backup@<synology-ip>
    ssh backup@<synology-ip>
    ```

17. Você poderá receber o seguinte erro:

    ```text
    /usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
    /usr/bin/ssh-copy-id: WARNING: All keys were skipped because they already exist on the remote system.
    ```

18. Nesse caso, copie manualmente a chave pública para o NAS como root usando:

    ```bash
    scp ~/.ssh/id_rsa.pub backup@<synology-ip>:/var/services/homes/backup/
    ssh backup@<synology-ip> cat /var/services/homes/backup/id_rsa.pub >> /var/services/homes/backup/.ssh/authorized_keys
    # you'll still be asked for your password on these both commands
    # after this you should be able to login password-less
    ```

19. E prossiga para a próxima etapa.

20. Se ainda for solicitada sua senha ao executar
    `ssh backup@<synology-ip>`, verifique as permissões do arquivo
    `/var/services/homes/backup/.ssh/authorized_keys`.

    Ele deve ser `-rw-------`.

    Caso contrário, execute:

    ```bash
    ssh backup@<synology-ip> chmod 600 /var/services/homes/backup/.ssh/authorized_keys
    ```

21. Agora você pode usar o *BackInTime* para realizar seu backup no NAS
    utilizando o usuário `backup`.

## Como usar o Synology DSM 6 com o BIT via SSH

1. Ative o **User Home Service** (**Control Panel / User / Advanced**).
   Não é necessário criar um volume, pois tudo é armazenado no diretório
   home.

2. Crie um novo usuário chamado `backup` (ou use sua conta existente).
   Adicione esse usuário ao grupo de usuários `Administrators`.
   Sem isso, você não conseguirá fazer login!

3. Ative o SSH (**Control Panel / Terminal & SNMP / Terminal**).

4. Ative o SFTP (**Control Panel / File Service / FTP / SFTP**).

5. A partir do DSM 5.1: ative o **Backup Service**
   (**Backup & Replication / Backup Service**).
   (Isso aparentemente não está mais disponível/não é mais necessário
   no DSM 6!) (Testes necessários!)

6. No DSM 6, você pode editar o diretório raiz do usuário para SFTP:
   **Control Panel → File Services → FTP → General → Advanced Settings
   → Security Settings → Change user root directories → Select User.**

   Agora selecione o usuário `backup` e altere o diretório raiz para
   `User home`.


1. Na estação de trabalho em que você pretende usar o BIT, crie chaves SSH para o usuário
   `backup` e envie a chave pública para o NAS:

   ```bash
   	ssh-keygen -t rsa -f ~/.ssh/backup_id_rsa
   	ssh-add ~/.ssh/backup_id_rsa
   	ssh-copy-id -i ~/.ssh/backup_id_rsa.pub backup@<synology-ip>
   	ssh backup@<synology-ip>
   ```

2. Você pode receber o seguinte erro:

   ```bash
   	/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
   	/usr/bin/ssh-copy-id: WARNING: All keys were skipped because they already exist on the remote system.
   ```

3. Nesse caso, copie manualmente a chave pública para o NAS como root com:

   ```bash
    scp ~/.ssh/id_rsa.pub backup@<synology-ip>:/var/services/homes/backup/
    ssh backup@<synology-ip> cat /var/services/homes/backup/id_rsa.pub >> /var/services/homes/backup/.ssh/authorized_keys
    # you'll still be asked for your password on these both commands
    # after this you should be able to login password-less
   ```

4. E prossiga para a próxima etapa.

5. Se ainda for solicitada sua senha ao executar `ssh
   backup@<synology-ip>`, verifique as permissões do arquivo
   `/var/services/homes/backup/.ssh/authorized_keys`. Ele deve estar como
   `-rw-------`. Caso contrário, execute o comando:

   ```bash
   ssh backup@<synology-ip> chmod 600 /var/services/homes/backup/.ssh/authorized_keys
   ```

6. Na caixa de diálogo de configurações do *BackInTime*, deixe o campo *Path* vazio.

7. Agora você pode usar o *BackInTime* para realizar seu backup no NAS com o usuário
   `backup`.

### Usando uma porta não padrão

Se você quiser usar o Synology NAS com uma porta SSH/SFTP não padrão
(a padrão é 22), será necessário alterar a porta em 3 lugares:

1. Control Panel > Terminal: Port = <PORT_NUMBER>

2. Control Panel > FTP > SFTP: Port = <PORT_NUMBER>

3. Backup & Replication > Backup Services > Network Backup Destination: SSH
   encryption port = <PORT_NUMBER>

Somente se os 3 estiverem configurados para a mesma porta o *BackInTime* conseguirá
estabelecer a conexão. Como teste, você pode executar o comando

```bash
rsync -rtDHh --checksum --links --no-p --no-g --no-o --info=progress2 --no-i-r --rsh="ssh -p <PORT_NUMBER> -o IdentityFile=/home/<USER>/.ssh/id_rsa" --dry-run --chmod=Du+wx /tmp/<AN_EXISTING_FOLDER> "<USER_ON_DISKSTATION>@<SERVER_IP>:/volume1/Backups/BackinTime"
```

em um terminal (no PC cliente).

## Como usar o Synology DSM 7 com BIT via SSH

1. Ative o *User Home Service* (Control Panel > User & Group > Advanced).

2. Crie um novo usuário chamado `backup` (ou use sua conta existente) e adicione esse
   usuário ao grupo de usuários `Administrators`.

3. Ative o *SSH* (Control Panel > Terminal & SNMP > Terminal).

4. Ative o *SFTP* (Control Panel > File Services > FTP > SFTP).

5. Ative o *rsync* (Control Panel > File Services > rsync).

6. Edite o diretório raiz do usuário para SFTP: Control Panel > File Services > FTP >
   General > Advanced Settings > Security Settings > Change user root directories >
   Select User > selecione o usuário `backup` > Edit e altere o diretório raiz para
   `User home`.

7. Certifique-se de que a pasta compartilhada 'homes' tenha as permissões padrão e que
   usuários e grupos que não sejam administradores não tenham permissões de leitura ou
   gravação atribuídas à pasta 'homes'. As permissões padrão estão descritas
   [neste guia](https://kb.synology.com/DSM/tutorial/default_permissions_of_homes).

8. Na estação de trabalho em que você precisa usar o BIT, crie um par de chaves SSH para
   o usuário `backup` e envie a chave pública para o NAS:

   ```bash
   	ssh-keygen -t rsa -f ~/.ssh/backup_id_rsa
   	ssh-copy-id -i ~/.ssh/backup_id_rsa.pub backup@<synology-ip>
   	ssh backup@<synology-ip>
   ```

9. Embora não seja estritamente necessário, a Synology recomenda definir as permissões
   do diretório `.ssh` e do arquivo `authorized_keys` como `700` e `600`,
   respectivamente:

   ```bash
   backup@NAS:~$ chmod 700 .ssh
   backup@NAS:~$ chmod 600 .ssh/authorized_keys
   ```

10. Na caixa de diálogo de configurações do *BackInTime*, deixe o campo *Path* vazio.

11. Agora você pode usar o *BackInTime* para realizar seu backup no NAS com o usuário
    `backup`.

### Usando uma porta SSH não padrão com um Synology NAS

Se você quiser usar o Synology NAS com uma porta SSH/SFTP não padrão, conforme recomendado
pelo pacote Security Advisor, será necessário alterar a porta em 3 lugares (o número da
porta padrão para os três é 22):

1. Control Panel > Terminal & SNMP > Terminal: Port = <PORT_NUMBER>

2. Control Panel > File Services > FTP > SFTP: Port number = <PORT_NUMBER>

3. Control Panel > File Services > rsync > SSH encryption port = <PORT_NUMBER>

Somente se os 3 estiverem configurados para a mesma porta o *BackInTime* conseguirá
estabelecer a conexão (não se esqueça de configurar o novo número da porta nos perfis
do BIT).

Para fazer login com ssh usando o novo número da porta:

```bash
ssh -p PORT_NUMBER backup@<synology-ip>
```

ou, para maior conveniência, você pode editar ou criar `~/.ssh/config` com o seguinte:

```
Host <synology-ip>
    Port PORT_NUMBER
```

e então usar apenas:

```bash
ssh backup@<synology-ip>
```

### "sshfs: No such file or directory" ao usar o BIT, mas ssh manual com rsync funciona

O motivo (conhecido para a versão 7 do DSM) é que a configuração de ssh e sftp é
personalizada pela Synology.

Solução ([Screenshot in Issue #1674](https://github.com/bit-team/backintime/issues/1674#issuecomment-2106059151)):

1. Acesse: *Control Panel* > *File Services* > *Advanced Settings* > *Change user root directories* > *Select User*
2. Adicione o nome do usuário utilizado para SSH no Synology à lista.
3. Em *Change root directory to:* selecione *User home*.

Veja também:

* [Issue #1674](https://github.com/bit-team/backintime/issues/1674)
* ["Change the default folder in a Synology NAS" - StackOverflow](https://stackoverflow.com/a/77454561/4865723)

## Synology: usar um volume diferente para o backup

Isso foi testado e está relacionado à versão 7 do Synology DSM, mas pode funcionar
também com outras versões. Fique à vontade para relatar os resultados.

Se você quiser usar um volume diferente como destino do backup, siga estas etapas adicionais:

1. Siga todas as etapas em **Howto (como criar um usuário adicional no exemplo com o
   nome de usuário 'backup')**

2. Crie na GUI do Synology DSM, no Control panel, uma nova pasta compartilhada e dê a ela,
   por exemplo, o nome de "backup".

   ![Synology DSM7 Basic Setup](doc/images.misc/faq_synology7_separate_dest_volume01.png)

3. Opcionalmente, na etapa 2, ative a criptografia da pasta compartilhada (dependendo
   das suas necessidades; não perca sua chave de criptografia). Vantagem: a pasta
   de backup (volume) fica criptografada, mesmo em caso de roubo do seu Synology NAS.
   Desvantagem: a cada Reboot você precisará montar a pasta manualmente.

   ![Synology DSM7 Additional Security Measure](doc/images.misc/faq_synology7_separate_dest_volume02.png)

4. Como usuário root ou usando sudo, edite o arquivo: `/etc/passwd`
   (Cuidado: se você danificá-lo, poderá danificar seu NAS.)

   * `vi /etc/passwd`
   * Edite a linha referente ao seu usuário backup, para que o diretório home fique na
     pasta recém-criada:
     `backup:x:1038:100:Back in Time User:/volume1/backup:/bin/sh`

5. Continue com sua configuração normal do BIT.

## Como usar o Western Digital MyBook World Edition com BIT via ssh?

Dispositivo: *WesternDigital MyBook World Edition (white light) versão 01.02.14 (WD MBWE)*

O BusyBox utilizado pela WD no MBWE para fornecer comandos básicos como `cp`
(copy) não oferece suporte a hardlinks. Essa é uma função rudimentar utilizada
pela forma como o BackInTime cria backups incrementais. Como solução alternativa,
você pode instalar o Optware no MBWE.

Antes de prosseguir, faça um backup do seu MBWE. Existe uma possibilidade significativa
de danificar seu dispositivo e perder todos os seus dados. Há uma boa documentação
sobre o Optware em http://mybookworld.wikidot.com/optware.

1. Você precisa fazer login na administração web do MBWE e mudar para o *Advanced Mode*.
   Em *System | Advanced*, você precisa ativar o *SSH Access*. Agora você pode fazer
   login como root via ssh e instalar o Optware (supondo que `<MBWE>` seja o endereço
   do seu MyBook).

   Digite no terminal:

   ```bash
   	ssh root@<MBWE> #enter 'welc0me' for password (you should change this by typing 'passwd')
   	wget http://mybookworld.wikidot.com/local--files/optware/setup-whitelight.sh
   	sh setup-whitelight.sh
   	echo 'export PATH=$PATH:/opt/bin:/opt/sbin' >> /root/.bashrc
   	echo 'export PATH=/opt/bin:/opt/sbin:$PATH' >> /etc/profile
   	echo 'PermitUserEnvironment yes' >> /etc/sshd_config
   	/etc/init.d/S50sshd restart
   	/opt/bin/ipkg install bash coreutils rsync nano
   	exit
   ```

2. De volta à administração web do MBWE, acesse *Users* e adicione um novo usuário
   (`<REMOTE_USER>` neste How-to) com *Create User Private Share* definido como *Yes*.

   No terminal:

   ```bash
   	ssh root@<MBWE>
   	chown <REMOTE_USER> /shares/<REMOTE_USER>
   	chmod 700 /shares/<REMOTE_USER>
   	/opt/bin/nano /etc/passwd
   	#change the line
   	#<REMOTE_USER>:x:503:1000:Linux User,,,:/shares:/bin/sh
   	#to
   	#<REMOTE_USER>:x:503:1000:Linux User,,,:/shares/<REMOTE_USER>:/opt/bin/bash
   	#save and exit by press CTRL+O and CTRL+X
   	exit
   ```

3. Em seguida, crie a ssh-key para seu usuário local.
   No terminal:

   ```bash
   	ssh <REMOTE_USER>@<MBWE>
   	mkdir .ssh
   	chmod 700 .ssh
   	echo 'PATH=/opt/bin:/opt/sbin:/usr/bin:/bin:/usr/sbin:/sbin' >> .ssh/environment
   	exit
   	ssh-keygen -t rsa #enter for default path
   	ssh-add ~/.ssh/id_rsa
   	scp ~/.ssh/id_rsa.pub <REMOTE_USER>@<MBWE>:./ #enter password from above
   	ssh <REMOTE_USER>@<MBWE> #you will still have to enter your password
   	cat id_rsa.pub >> .ssh/authorized_keys
   	rm id_rsa.pub
   	chmod 600 .ssh/*
   ```
# Projeto, contribuição e mais

## Por que preciso me apresentar?

Isso ajuda os mantenedores a entender quem você é e como se comunicar com você. Isso evita
esforços desnecessários de ambos os lados, evitando mal-entendidos que poderiam levar a
contribuições rejeitadas. Também ajuda a distinguir contribuidores genuínos de contas que
enviam alterações de baixa qualidade ou geradas por IA apenas para aumentar artificialmente
as estatísticas de commits ou o número de estrelas, sem um envolvimento real com o projeto.

Aqui está uma pequena sugestão e orientação para sua apresentação:

* Há quanto tempo e de que forma você utiliza o BIT?
* Que experiência e habilidades você possui em desenvolvimento de software?
* Quais são seus objetivos atuais de aprendizado?
* Como você tomou conhecimento desta issue?

## Posso contribuir sem usar o software?

Não, na maioria dos casos. Os contribuidores precisam ser usuários do *Back In Time*.
Contribuições reais exigem familiaridade com o software, seu comportamento e seus
workflows. Contribuições reais vêm de uso real.

## Vocês podem atribuir isso a mim?

Não. Não pergunte. Primeiro, comente manifestando sua intenção ou apresentando um plano.
Caso contrário, isso é apenas ruído.

Seu comportamento desrespeita contribuidores com uma intenção real e sobrecarrega os
mantenedores que trabalham neste projeto em seu tempo livre. Não desperdice nosso tempo.

## Posso usar @ mentions livremente em issues ou PRs?

Não. Nunca. Evite-as em todos os casos. Mentions acionam notificações e criam ruído.
Mantenedores e contribuidores inscritos já conseguem ver toda a atividade.

## Posso aumentar minha contagem de commits?

Não. Fazer isso pode fazer com que sua conta seja bloqueada ou excluída, porque os
mantenedores irão denunciá-lo à equipe de abuso da Microsoft. Este projeto não existe
para coletar estrelas ou commits. Talvez assistir a
[Don't Contribute to Open Source](https://www.youtube.com/watch?v=5nY_cy8zcO4)
ajude você a entender e aprender.

## Posso enviar contribuições geradas por IA?

Não. Contribuições geradas por IA são proibidas. Tentar fazer isso será denunciado à
equipe de abuso da Microsoft, e sua conta poderá ser bloqueada ou excluída.

## Opções alternativas de instalação

Além dos repositórios das distribuições GNU/Linux oficiais, existem outras opções
alternativas de instalação fornecidas e mantidas por terceiros. Use-as por sua própria
conta e risco e entre em contato com os mantenedores terceiros caso encontre problemas.
**Novamente**: recomendamos fortemente não utilizar repositórios de terceiros devido a
possíveis problemas de segurança.

* [@jean-christophe-manciot](https://github.com/jean-christophe-manciot)'s PPA distribuindo
  [*Back In Time* para a versão estável mais recente do Ubuntu](https://git.sdxlive.com/PPA/about).
  Veja [PPA requirements](https://git.sdxlive.com/PPA/about/#requirements) e
  [install instructions](https://git.sdxlive.com/PPA/about/#installing-the-ppa).
* O Arch User Repository ([AUR](https://aur.archlinux.org/)) oferece
  [alguns pacotes](https://aur.archlinux.org/packages?K=backintime).

## Suporte para formatos específicos de pacotes (deb, rpm, Flatpack, AppImage, Snaps, PPA, …)

Nós auxiliamos e damos suporte a outros projetos que fornecem pacotes específicos para
distribuições. Portanto, sugerimos que você crie seu próprio repositório para gerenciar
e manter esses pacotes. Ele será mencionado em nossa documentação como uma fonte
alternativa para instalação.

Nós não oferecemos suporte diretamente a canais de distribuição de terceiros associados
a distribuições GNU/Linux específicas, repositórios não oficiais (por exemplo, Arch AUR,
Launchpad PPA) ou FlatPack & Co. Uma das razões é nossa falta de recursos e a necessidade
de priorizar tarefas. Outra razão é que existem mantenedores das distribuições com muito
mais experiência e conhecimento em empacotamento. Sempre recomendamos utilizar os
repositórios oficiais das distribuições GNU/Linux e entrar em contato com seus
mantenedores caso o *Back In Time* não esteja disponível ou esteja desatualizado.

## O BIT realmente não é suportado pelo Canonical Ubuntu?

O Ubuntu consiste em
[vários repositórios](https://help.ubuntu.com/community/Repositories), cada um
oferecendo diferentes níveis de suporte. O repositório `main` é mantido pela Canonical
e recebe atualizações de segurança e correções de bugs regularmente durante o período
de suporte de 5 anos das versões LTS.

Em contraste, o repositório `universe` é gerenciado pela comunidade, o que significa
que atualizações de segurança e correções de bugs não são garantidas e dependem muito
da atividade da comunidade e de voluntários. Portanto, os pacotes em `universe` podem
nem sempre estar atualizados em comparação com os mesmos pacotes, bem mantidos, do
Debian GNU/Linux e podem não conter correções importantes.

O *Back In Time* é um desses pacotes no repositório `universe`. Esse
[package](https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=backintime)
é copiado do
[Debian GNU/Linux repository](https://packages.debian.org/search?searchon=sourcenames&keywords=backintime).
Pode-se dizer que o *Back In Time* não é mantido pelo Canonical Ubuntu, mas por
voluntários da Community of Ubuntu.

## Mover o projeto para outro code hoster (por exemplo, Codeberg, GitLab, …)

Também acreditamos que permanecer no Microsoft GitHub não é uma boa ideia. O Microsoft
GitHub não oferece nenhuma funcionalidade exclusiva para nosso projeto que outro hoster
também não poderia oferecer. Porém, uma migração depende de tempo e recursos que
atualmente não temos. Mas isso está em nossa lista. E, considerando o estado atual das
discussões, parece que nosso alvo será o [Codeberg.org](https://codeberg.org).

Para mais detalhes, consulte
[este tópico na mailing list](https://mail.python.org/archives/list/bit-dev@python.org/message/O5XZ5SPW6WIFBFKWUBHSOUIBKEUIBPNM/).

## Como revisar um Pull Request

Revisar um Pull Request (PR) não envolve apenas o código — também envolve
funcionalidade. As alterações podem ser testadas instalando o *Back In Time* e
experimentando-as, mesmo sem ler o código. Isso permite identificar problemas do ponto
de vista do usuário. Um segundo par de olhos ajuda a encontrar erros, identificar
problemas que passaram despercebidos e melhorar a qualidade geral. Novas perspectivas,
compartilhamento de conhecimento e melhor manutenção contribuem para a estabilidade
do projeto a longo prazo.

Verifique as PRs marcadas com
[PR: Waiting for
review](https://github.com/bit-team/backintime/pulls?q=is%3Aopen+is%3Apr+label%3A%22PR%3A+Waiting+for+review%22).
Verificar o [milestone](https://github.com/bit-team/backintime/milestones)
atribuído à PR também pode ajudar a avaliar sua prioridade e urgência.

* Comece lendo cuidadosamente a descrição da PR para entender as alterações propostas.
  Pergunte caso algo não esteja claro.
* Ao fornecer feedback, considere o nível de experiência e as habilidades do contribuidor.
  Seja educado e construtivo — todo iniciante pode se tornar um futuro mantenedor.

Para **testar a funcionalidade**,
[faça checkout do código da PR localmente](https://docs.github.com//pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/checking-out-pull-requests-locally)
em uma máquina virtual ou em sua máquina local. Executar o *Back In Time* em um
ambiente de teste fornece informações que podem ser compartilhadas como descobertas,
observações ou sugestões de melhoria.

Sobre a **revisão de código**:

* O código deve seguir os
  [padrões do projeto](CONTRIBUTING.md#best-practice-and-recommendations)
  e ser estruturado visando à manutenção a longo prazo.
* Se uma PR for grande ou complexa demais, sugira dividi-la em partes menores.
* Como está a documentação?
* Existem testes unitários?
* É necessário adicionar uma entrada ao changelog?

# Testes e Build

## Testes relacionados a SSH são ignorados

Eles são ignorados caso nenhum servidor SSH esteja disponível. Consulte a seção
[Testing & Building](CONTRIBUTING.md#testing--building) para saber como configurar
um servidor SSH em seu sistema.

## Configurar o servidor SSH para executar testes unitários

Consulte a seção [Testing - SSH](CONTRIBUTING.md#ssh).
