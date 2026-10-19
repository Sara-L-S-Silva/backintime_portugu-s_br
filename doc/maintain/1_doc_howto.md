Organização e compilação da documentação do Back In Time
Este arquivo descreve brevemente os diversos tipos de documentação existentes para o Back In Time (BIT), como eles são mantidos, estruturados e compilados.

[!TIP] Sinta-se à vontade para abrir issues ou entrar em contato com a equipe de manutenção na lista de discussão caso este texto seja difícil de entender ou não seja útil.

Índice
# visão-geral
[Compilar e visualizar o manual do usuário mkdocs
[Dicas e Exemplos
Visão Geral
O projeto distingue três tipos de documentação:

O Manual do usuário pode ser encontrado em backintime.readthedocs.io e é gerado usando o MkDocs com base em arquivos simples em Markdown.
A documentação de Manutenção e Desenvolvimento consiste em um conjunto de arquivos Markdown, como este que você está lendo agora.
Compilar e visualizar o manual do usuário (MkDocs)
Instale as dependências relacionadas:

mkdocs
mkdocs-material
Consulte o arquivo ../../CONTRIBUTING.md neste repositório para obter uma lista completa e atualizada de dependências.
Visualização HTML em tempo real durante a edição:

# Entrar na pasta
$ cd doc/manual

# Iniciar o servidor integrado
$ mkdocs serve
Abra [127.0.0.1:80001:8000 em seu navegador. Sempre que os arquivos Markdown subjacentes forem modificados, o servidor gerará novas páginas HTML dinamicamente.

Gerar arquivos HTML:

# Entrar na pasta
$ cd doc/manual

# Compilar
$ mkdocs build

# Abrir o resultado no navegador padrão
$ xdg-open html/index.html
Dicas e Exemplos
#markdown
[caixas-de-anotação--caixas-coloridas-de-destaque
Markdown
Caixas de anotação / Caixas coloridas de destaque
> [!NOTE]
> Destaca informações que os usuários devem levar em consideração, mesmo
> durante uma leitura rápida.

> [!TIP]
> Informações opcionais para ajudar o usuário a obter melhores resultados.

> [!IMPORTANT]
> Informações cruciais necessárias para que os usuários tenham sucesso.

> [!WARNING]
> Conteúdo crítico que exige atenção imediata do usuário devido a riscos potenciais.

> [!CAUTION]
> Possíveis consequências negativas de uma ação.
[!NOTE] Destaca informações que os usuários devem levar em consideração, mesmo durante uma leitura rápida.

[!TIP] Informações opcionais para ajudar o usuário a obter melhores resultados.

[!IMPORTANT] Informações cruciais necessárias para que os usuários tenham sucesso.

[!WARNING] Conteúdo crítico que exige atenção imediata do usuário devido a riscos potenciais.

[!CAUTION] Possíveis consequências negativas de uma ação.

<sub>Junho de 2026</sub>