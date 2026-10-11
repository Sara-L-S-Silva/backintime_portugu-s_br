<!--
SPDX-FileCopyrightText: © 2024 Back In Time Team

SPDX-License-Identifier: GPL-2.0-or-later

This file is part of the program "Back In Time" which is released under GNU
General Public License v2 (GPLv2). See directory LICENSES or go to
<https://spdx.org/licenses/GPL-2.0-or-later.html>
-->
- [Visão geral](#visão-geral)
- [Compilar o manual do usuário](#compilar-o-manual-do-usuário)
- [Como reduzir o tamanho dos arquivos de imagem](#como-reduzir-o-tamanho-dos-arquivos-de-imagem)

# Visão geral
Este diretório contém os arquivos-fonte de vários tipos de documentação
do _Back In Time_.

- `manual`: Manual do usuário
- `manpages`: Arquivos-fonte das páginas de manual
- `maintain`: Vários documentos sobre a manutenção do projeto _Back In Time_
  e quase todos os outros documentos que não se encaixam em nenhuma das outras
  categorias.

# Compilar o manual do usuário
O manual do usuário é compilado a partir de arquivos markdown (no diretório `src`) e convertido
em HTML (diretório `html`). A ferramenta `mkdocs` é usada para isso.

```sh
$ cd backintime/doc/manual
$ mkdocs build
INFO    -  Cleaning site directory
INFO    -  Building documentation to directory: XYZ
INFO    -  Documentation built in 2.66 seconds 
$
```
Abra `html/index.html` para inspecionar o resultado.

Como alternativa, `mkdocs` pode fornecer uma prévia ao vivo da documentação enquanto
os arquivos markdown estão sendo editados. Um servidor web local é usado para isso.

```sh
$ cd backintime/doc/manual
$ mkdocs serve
INFO    -  Building documentation...
INFO    -  Cleaning site directory
INFO    -  Documentation built in 1.40 seconds
INFO    -  [10:17:21] Watching paths for changes: 'src', 'mkdocs.yml'
INFO    -  [10:17:21] Serving on http://127.0.0.1:8000/     
```

Inspecione o resultado no navegador: [127.0.0.1:8000](http://127.0.0.1:8000).

# Como reduzir o tamanho dos arquivos de imagem
Para imagens PNG, `optipng` pode ser usado. *Atenção*: Por padrão, ele sobrescreve
os arquivos originais. O comando a seguir usa o nível mais alto de otimização
possível e grava o resultado em uma subpasta.

    $ optipng --dir subfolder -o7 *.png

Como alternativa, `pngcrush` pode ser usado. O comando a seguir determina
o melhor algoritmo por conta própria.

    $ pngcrush -d subfolder -brute *.png

Quando aplicados a um conjunto de capturas de tela do modo escuro do _Back In Time_,
o tamanho dos arquivos foi reduzido em aproximadamente 13%. Ambos os aplicativos
apresentam diferenças insignificantes. O resultado visual é indistinguível do original.