# Script de callback do usuário
<!--
SPDX-FileCopyrightText: © 2015 Germar Reitze
SPDX-FileCopyrightText: © 2024 Kosta Vukicevic (stcksmsh)
SPDX-FileCopyrightText: © 2024 Christian BUHTZ <c.buhtz@posteo.jp>

SPDX-License-Identifier: GPL-2.0-or-later

This file is part of the program "Back In Time" which is released under GNU
General Public License v2 (GPLv2). See LICENSES directory or go to
<https://spdx.org/licenses/GPL-2.0-or-later.html>
-->
## Introdução

Durante o processo de backup, o _Back In Time_ pode chamar um script definido
pelo usuário em resposta a vários eventos. Esse script é chamado `user-callback`.

Por padrão, o caminho é `$XDG_CONFIG_HOME/backintime/user-callback`. Ele sempre
fica no mesmo local que o próprio arquivo de configuração. Portanto, se a opção
`--config` for usada para definir um arquivo de configuração em outro local, o
_Back In Time_ procurará o script user-callback nesse local.

O arquivo precisa ser executável. O nome do arquivo não pode ser alterado.
O conteúdo do arquivo pode ser editado pela GUI: _Manage profiles_ >
_Options_ > _Edit user-callback_ (consulte também
[aba Options no diálogo Manage profiles](manage-profiles.md#options)).

## Argumentos e valor de retorno

O script pode receber **três argumentos**. Em caso de eventos de erro, haverá um
quarto argumento com um código de erro e, às vezes, um quinto argumento com
informações adicionais.

O **valor de retorno** do script deve ser `0` se o backup deve continuar.
Valores de retorno diferentes de `0` interromperão o backup.

1. O ID do profile (1=Main Profile, ...).
2. Nome do profile.
3. Motivo do callback:

| Valor | Motivo                                                             |
| ----- | -------------------------------------------------------------------|
| **1** | Um processo de backup está prestes a começar.                      |
| **2** | Um processo de backup foi encerrado.                                |
| **3** | Um novo backup foi criado. Os dois argumentos extras seguintes são o ID do backup e o caminho do backup. |
| **4** | Ocorreu um erro. Consulte a próxima tabela para ver os [códigos de erro](#errorcodes). |
| **5** | O aplicativo (gráfico) foi iniciado.                                |
| **6** | O aplicativo (gráfico) foi fechado.                                 |
| **7** | Pode ser necessário montar um filesystem para o profile.            |
| **8** | Pode ser necessário desmontar um filesystem para o profile.         |

<a id="errorcodes"></a>
Os possíveis **códigos de erro** (consulte _Motivo do callback_ **4**) são fornecidos como quarto argumento:

| Código | Erro                                                              |
| ------| -------------------------------------------------------------------|
| **1** | A configuração está ausente ou é inválida.                         |
| **2** | Já há um processo de backup em execução.[^1]                       |
| **3** | Não foi possível encontrar o diretório de backups.[^2]             |
| **4** | Já existe um backup para "agora". O quinto argumento é o ID do backup. |
| **5** | Erro ao criar um backup.[^3] O quinto argumento contém mais informações sobre o erro. |
| **6** | Novo backup criado, mas com erros.[^3] O quinto argumento é o ID do backup. |

## Implementação

`UserCallbackPlugin` é uma classe definida em
[`common/plugins/usercallbackplugin.py`](https://github.com/bit-team/backintime/blob/dev/common/plugins/usercallback.plugin.py).
Ela é uma classe filha de `Plugin`, que pode ser encontrada em
[`common/pluginmanager.py`](https://github.com/bit-team/backintime/blob/dev/common/pluginmanager.py).

## Exemplos

Vários scripts de exemplo podem ser encontrados no diretório
`/usr/share/doc/backintime` ou no
[repositório do projeto](https://github.com/bit-team/backintime/tree/dev/doc/user-callback-examples).

[^1]: Certifique-se de que backups manuais e automáticos não sejam executados ao mesmo tempo.
    
[^2]: Por exemplo, se o diretório de backups estiver em uma unidade removível
    que não esteja montada ou esteja montada em um local diferente.
    
[^3]: Suporte adicionado na versão 1.4.0 do _Back In Time_.