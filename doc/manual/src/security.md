# Segurança
<!--
SPDX-FileCopyrightText: © 2025 Christian BUHTZ <c.buhtz@posteo.jp>

SPDX-License-Identifier: GPL-2.0-or-later

This file is part of the program "Back In Time" which is released under GNU
General Public License v2 (GPLv2). See LICENSES directory or go to
<https://spdx.org/licenses/GPL-2.0-or-later.html>
-->
## Permissões de diretório ao criar backups
<!--
Consulte esta issue para informações de contexto e histórico das decisões:
- https://github.com/bit-team/backintime/issues/377
-->
!!! note inline end 
    Esta seção é destinada a *usuários avançados* ou *administradores de sistema*
    que desejam informações detalhadas. **Em configurações típicas, nenhuma ação
    ou alteração é necessária.**

Os novos diretórios de backup criados pelo **Back In Time** recebem
automaticamente suas permissões (por meio do `rsync`) de acordo com o
[`umask`](https://wikipedia.org/wiki/Umask) atual do sistema ou do usuário que
executa o programa. Dependendo desse `umask`, os diretórios podem ser criados
com permissões como `0775` (acesso de leitura, gravação e execução para o
proprietário e o grupo; acesso de leitura e execução para outros usuários).

No entanto, as permissões do diretório pai também se aplicam. Na maioria dos
casos, os backups são armazenados no diretório pessoal do usuário, que, por
padrão, não é acessível a outras pessoas. Isso significa que, mesmo que o
próprio diretório de backup pareça aberto, geralmente outros usuários não
conseguem acessá-lo.

Se for desejável um isolamento mais rigoroso, pode-se definir um **umask** mais
restritivo antes de iniciar o **Back In Time**, por exemplo, `0750` (acesso de
leitura, gravação e execução para o proprietário; acesso de leitura e execução
para o grupo; nenhuma permissão para outros usuários). Como alternativa, as
permissões podem ser ajustadas manualmente após a criação, ou o diretório pai
pode ser protegido de forma apropriada.

Portanto, as permissões efetivas do diretório dependem do `umask` e da
configuração dos diretórios pai.