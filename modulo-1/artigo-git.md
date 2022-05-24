# Padronização das terminações de linha no Git

Tenho alternado entre Windows e Linux nos últimos meses, e as diferenças realmente são enormes em relação a Java. Mas o que realmente me deixou surpresa foi descobrir que o sistema operacional também impacta no Git.

Ao pesquisar por esse aviso descobri que existem dois tipos de controle de caracteres para terminação de linha em arquivos: LF (Line Feed), equivalente ao início de uma nova linha para Linux e Mac, e CRLF (Carriage Return +LF), que move o cursor para o início de uma nova linha no Windows.

Se você está apenas estudando e desenvolve seus projetos de forma individual, isso não vai gerar nenhum conflito, mas para trabalhar em um ambiente colaborativo onde os desenvolvedores utilizam sistemas operacionais diferentes, é impossível não padronizar. Então por que já não aprender da forma como realmente funciona na prática?

A solução mais recomendada atualmente, é criar um arquivo *.gitattributes* na pasta raiz do repositório com as seguintes configurações:

`* text=auto`

`(*)`_: o arquivo não vai ser ignorado._

`atributo`_: normaliza todas as terminações de linha do repositório para LF._

`text=auto`_: padroniza apenas as terminações de linha de arquivos de texto para LF, enquanto os arquivos binários permanecem inalterados._

É possível consultar a terminações de linha com o seguinte comando:

`git ls-files --eol`

O resultado vai trazer sempre: **i/lf** _(git)_ | **w/crlf** _(working tree)_ | **attr/text=auto** _(atributo)_ | **nome do arquivo**.

Caso as alterações não tenham efeito imediato, é possível forçar a atualização com o seguinte comando:

`git add --renormalize .`

Incrível, não é?! Se você quer aprender mais sobre o tema, é só acessar esse artigo [aqui](https://www.aleksandrhovhannisyan.com/blog/crlf-vs-lf-normalizing-line-endings-in-git/#a-simple-gitattributes-config).

Publicado em: [DIO](https://web.dio.me/articles/padronizacao-das-terminacoes-de-linha-no-git) | [LinkedIn](https://www.linkedin.com/feed/update/urn:li:activity:6934397560233041920/)
