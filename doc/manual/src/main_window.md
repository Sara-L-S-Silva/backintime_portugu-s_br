# Janela principal
<!--
SPDX-FileCopyrightText: © 2016 Germar Reitze

SPDX-License-Identifier: GPL-2.0-or-later

This file is part of the program "Back In Time" which is released under GNU
General Public License v2 (GPLv2). See LICENSES directory or go to
<https://spdx.org/licenses/GPL-2.0-or-later.html>
-->
![Janela principal do Back In Time](_images/light/main_window_sections.png#only-light)
![Janela principal do Back In Time](_images/dark/main_window_sections.png#only-dark)

## Barra de ferramentas principal

**_Criar um backup_**

Cria um novo backup em background. A janela principal pode ser fechada durante
a criação. Normalmente, apenas o tamanho e o horário de modificação dos arquivos
são comparados. Como alternativa, você pode criar um novo backup com a opção
`checksums` ativada. Isso calculará checksums de cada arquivo para determinar se
ele foi alterado. Criar um backup com a opção `checksums` leva muito mais tempo,
mas garante que os arquivos de destino não estarão corrompidos.

**_Atualizar a lista de backups_**

Atualiza os backups na [Linha do tempo](#linha-do-tempo).

**_Nomear backup_**

Adiciona um nome a um backup para que você possa identificá-lo facilmente mais
tarde. Se `Don't remove named backups` em **Manage profile \--\> Remote & Retention**
estiver ativado, isso também impedirá que o backup seja removido.

**_Remover backup_**

Remove um ou mais backups da Linha do tempo. `Now` não pode ser removido, pois
não é um backup, mas uma visualização ao vivo do file-system local. Se este
botão estiver desabilitado, você precisará selecionar um backup na
[Linha do tempo](#linha-do-tempo).

**_Visualizar o log do backup selecionado_**

Exibe o log do backup selecionado.

**_Abrir o log do último backup_**

Exibe o log da última tentativa de backup.

**_Gerenciar profiles_**

Abre [*Manage profiles*](manage-profiles.md).

**_Desligar_**

Desliga o computador após a conclusão de um backup. Para isso, a janela
principal precisa permanecer aberta. Se o desligamento não for compatível com
o sistema, este botão ficará desabilitado.

## Barra de ferramentas de arquivos

**_Acima_**

Vai para o diretório pai.

**_Exibir arquivos ocultos_**

Alterna a exibição de arquivos ocultos (que começam com um ponto) na
visualização de arquivos.

**_Restaurar_**

Restaura os arquivos ou diretórios selecionados. Este botão tem um submenu
(mantenha o botão pressionado). A ação padrão é `Restore`.

Ou restaura os arquivos ou diretórios selecionados no destino original.

Ou restaura os arquivos ou diretórios selecionados em um novo destino.

Ou restaura o diretório exibido no momento e todo o seu conteúdo no destino
original.

Ou restaura o diretório exibido no momento e todo o seu conteúdo em um novo
destino.

**_Comparar backups_**

Abre o [diálogo de backups](backups-dialog.md).

## Linha do tempo

A Linha do tempo lista todos os backups que já foram criados. Você pode navegar
por eles para ver o conteúdo na [Visualização de arquivos](#visualização-de-arquivos),
à direita. O primeiro item, `Now`, não é um backup. Ele é uma visualização ao
vivo do file-system local e exibe exatamente o mesmo conteúdo que o navegador
de arquivos habitual. É possível fazer uma seleção múltipla para remover vários
backups de uma vez.

## Visualização de arquivos

Dependendo da seleção na [Linha do tempo](#linha-do-tempo), à esquerda, esta
visualização mostrará os arquivos originais ou os arquivos do backup selecionado.
Em `Shortcuts`, você pode ir diretamente para seu diretório home ou para os
diretórios incluídos.

## Barra de status

Exibe o status atual. Enquanto um backup estiver em execução, mostrará uma
barra de progresso junto com a velocidade atual, os dados já transferidos e a
última mensagem do `rsync`.