# Introdução

Este documento contém tudo que você precisa saber para começar a usar o Git com o GitLab. Aqui, estão reunidas informações sobre comandos, padronizações, organização, estrutura e nomenclaturas. Para saber mais, leias as documentações do [Git](https://git-scm.com/doc) e [GitLab](https://docs.gitlab.com/ee/).

# Sumário

<ol>

```
<li><a href="#content0">O que é Controle de Versão?</a>;</li>
<li><a href="#content1">Instalando Git Bash</a>;</li>
<li><a href="#content2">Acessando o GitLab</a>;</li>
<li><a href="#content3">Criando um projeto</a>;</li>
<li><a href="#content4">Clonando um projeto</a>;</li>
<li><a href="#content5">Como usar Issues</a>;</li>
<li><a href="#content6">Tipos de organização de trabalho</a>;</li>
<li><a href="#content7">Gitflow</a>;</li>
<li><a href="#content8">Trunk based development</a>;</li>
<li><a href="#content9">Subindo Alterações</a>;</li>
<li><a href="#content10">Gerenciamento de Conflitos</a>;</li>
```

</ol>

# Conteúdo

<h3>O que é Controle de Versão?<a name="content0"></a></h3>

O controle de versão é a prática de rastrear e gerenciar as alterações em um código de software. Os sistemas de controle de versão são ferramentas de software que ajudam as equipes de software a gerenciar as alterações no código ao longo do tempo.

Usar o software de controle de versão é uma prática recomendada para software de alto desempenho e equipes. O controle de versão também ajuda os desenvolvedores a se mover mais rápido e permite que as equipes preservem a eficiência e a agilidade à medida que a equipe é escalonada para incluir mais desenvolvedores.

Neste documento usaremos o [Git](https://git-scm.com/doc) e para versionar todas as aplicações e o [GitLab](https://docs.gitlab.com/ee/) para guardar a aplicação na nuvem e ficar disponível a todos os membros da equipe. Com esta ferramenta é necessário criar um repositório local, que será na memória do seu computador pessoal e um repositório remoto na nuvem que será no GitLab.

<h3>Instalando e configurando o Git Bash<a name="content1"></a></h3>

Esse programa será fundamental para o uso do repositório local da máquina e sua integração com a GitLab. 

##### Para Windows

1. Acesse o [site](https://git-scm.com/downloads) do Git;
2. Selecione o seu sistema operacional, ele irá baixar automaticamente uma versão adequada para você;
3. Execute o arquivo como administrador.

##### Para Mac

Existem várias opções para instalar o Git no MacOS, inclusive a forma para Windows também funciona para Mac. Observe que todas as distribuições não originais são fornecidas por terceiros e podem não estar atualizadas com a versão de origem mais recente.

##### Via Homebrew

1. Intale o [Homebrew](https://brew.sh/);
2. Execute no terminal `$ brew install git`.

##### Via Xcode

A Apple fornece um pacote binário do Git com o [Xcode](https://developer.apple.com/xcode/).

##### Outras formas

Existem outras formas possíveis, se você quiser saber mais, [clique aqui](https://git-scm.com/download/mac).

##### Para Linux

É mais fácil instalar o Git no Linux usando o gerenciador de pacotes preferido de sua distribuição Linux, mas é também possível seguir o mesmo passo descrito para o Windows.

##### Debian / Ubuntu

```shell
$ apt-get install git
```

Para Ubuntu, este PPA fornece a versão _upstream_ estável mais recente do Git:

```shell
$ add-apt-repository ppa:git-core/ppa
$ apt update; apt install git
```

Para outras distros, [clique aqui](https://git-scm.com/download/linux).

<h3>Acessando GitLab<a name="content2"></a></h3>

(EM CONSTRUÇÃO)

<h3>Criando um projeto<a name="content3"></a></h3>

Todo repositório Git armazena as informações dentro de uma pasta oculta chamada /.git. Para que os arquivos de uma pasta possam ser versionados, é preciso iniciar o repositório. Para criar um repositório novo, você pode criar um no repositório remoto e clonar este para um repositório local em sua máquina, ou criar um repositório via terminal.

Via repositório local:

1. Crie um diretório (pasta) para comportar sua aplicação;
2. Abra o terminal e localize esse diretório;
3. Digite o seguinte comeando:

```shell
$ git init
```

Via repositório remoto:

1. Abra o GitLab, faça login com a sua conta e clique em New repository;
2. Coloque o nome e descrição do repositório que você está criando e clicar em Create repository;
3. Depois, aparecerá na tela: O repositório foi criado, só que ainda está vazio.

<h3>Clonando um projeto<a name="content4"></a></h3>

clonar repositórios, siga os seguintes passos:

1. Acesse o repositório e copie o link que preferir (para acessar via ssh ou via http);
2. Prepare um diretório (pasta) em sua máquina para receber o diretório da aplicação;
3. Abra um prompt de comandos ou terminal shell e localize seu diretório.

Agora, digite a linha de comando a seguir:

```shell
$ git clone link-do-repositorio
```

Uma senha poderá ser solicitada para válidar o acesso.

Uma vez realizado a clonagem do repositório, será necessário instalar todas as dependências do pacote. Portanto, utilize a linha de comando a seguir:

```shell
$ npm install
```

Se preferir usar outro gerenciador de pacotes, digite a seguinte linha:

```shell
$ yarn install
```

<h3>Como usar issues<a name="content5"></a></h3>

(EM CONSTRUÇÃO)

<h3>Tipos de organização de trabalho<a name="content6"></a></h3>

(EM CONSTRUÇÃO)

<h3>Gitflow<a name="content7"></a></h3>

É definido que toda aplicação deve possuir, por padrão, 2 branchs inicialmente:

- Develop: é a branch na qual, a partir dela, são feitas as branchs feature;
- Main (master): é a branch intocável, somente deve ser alterada quando a branch develop contiver uma versão usável e em pleno funcionamento.

##### Quando deve fazer uma nova branch feature

É definido que para cada alteração uma nova feature deve ser criada. Pois dessa forma, é mais fácil localizar uma alteração indesejada e removê-la da aplicação. Segue exemplos de situações que necessitam de uma branch feature nova:

1. Criar um _component_
2. Estilizar um _component_
3. Criar uma lógica específica

É considerado uma boa prática separa o quanto for possível as alterações que serão feitas. Para auxiliar nesse entendimento, reflita se a alteração é um conjunto coerente e voltado para uma mesma ação. A seguir, exemplos de práticas ruins de criação de novas branch feature.

1. Dividir a criação de um _component_
2. Dividir a estilização de um _component_
3. Dividir a criação de uma lógica específica

##### Criação e nomeação de novas branch feature

Certifique-se de que está na branch develop. Para criar uma nova branch, use a seguinte linha de comando:

```shell
$ git checkout -b #nome-apropriado
```

É definido, para cada ação citada abaixo, como padrão para o ``nome-apropriado`` ela ser o número da issue "#" e um nome. Veja os exemplos a seguir.

- __Criar um _component_:__ o nome do _component_;

Exemplos:

1. Criar balloon de diálogo: ``#balloon``;
2. Criar botão: ``#button``;
3. Criar menu: ``#menu``.

- __Estilizar um _component_:__ o nome do _component-style_;

Exemplos:

1. Estilizar balloon de diálogo: ``#balloon-style``;
2. Estilizar botão: ``#button-style``;
3. Estilizar menu: ``#menu-style``.

- __Criar lógica específica:__ o nome da lógica;

Exemplos:

<ol>

```
<li>Criar lógica de diálogo: <code>#dialogue-logic</code>;</li>
<li>Criar lógica de filtros: <code>#filter-logic</code>;</li>
<li>Criar lógica de pesquisa: <code>#search-logic</code>.</li>
```

</ol>

<ul>

```
<li><b>Desenvolver API ou parte dela: o nome da API e suas especificações.</b></li>
```

</ul>

<p>Exemplos:</p>

<ol>

```
<li>Desenvolver API de login: <code>#login-API</code>;</li>
<li>Desenvolver API de pagamento: <code>#payment-API</code>;</li>
<li>Desenvolver API de controles de usuário: <code>#user-controllers-API</code>.</li>
```

</ol>

<p>Demais casos, devem seguir padrões similares.</p>

<img alt="gitflow" src="https://uploads.toptal.io/blog/image/129305/toptal-blog-image-1551794424851-b3d5928bc33edfc954ef460062e5cbcc.png">

Caso tenha ficado com dúvidas, assista a este [vídeo](https://www.youtube.com/watch?v=wzxBR4pOTTs).

##### Merges de aplicações

Merge é o processo responsável por unificar branchs criadas em uma única para obter uma determinada versão da aplicação. Toda vez que uma feature é criada, precisamos fazer um ``merge request`` que é basicamente uma solicitação de merge para o master da equipe. Essa medida visa reduzir merges de branchs com conflitos que definicam a aplicação.

Para solicitar um ``merge request`` siga os passos a seguir:

<ol>

```
<li>Após o <code>git push</code>, vá até a GitLab e localize no repositório na parte superior um botão para solicitação de merge (Ele aparecerá junto ao um aviso de commit realizado)</li>
<li>Verifique se todas as alterações que você fez estão em conformidade com o que vc deseja</li>
<li>Selecione a branch <code>develop</code> para receber as alterações da branch <code>feature/</code></li>
<li>Em <i></i>, selecione o master para valiar o <code>merge request</code></li>
<li>E como boa prática, envie uma mensagem de lembrete ao master para ele verificar o repositório</li>
```

</ol>

<p>Há também a possibilidade de merge via terminal.</p>

<h5>Para desenvolvedores <i>masters</i></h5>

<p>Volte para a branch develop com o seguinte comando:</p>

```shell
$ git checkout develop
```

<p>Realize o merge digitando no terminal:</p>

```shell
$ git merge #nome-apropriado
```

<p>Neste momento, ou o merge é feito por completo ou aparecem conflitos que deverão ser resolvidos para a finalização do procedimento</p>

<h5>Para desenvolvedores não <i>masters</i></h5>

<p>(EM CONSTRUÇÃO)</p>

<h3>Trunk based development<a name="content8"></a></h3>

<p>(EM CONSTRUÇÃO)</p>

<img alt="gitflow" src="https://uploads.toptal.io/blog/image/129304/toptal-blog-image-1551794413174-f4139c4be533dc592d49f9a0bcc330f0.png">

<h3>Subindo Alterações<a name="content9"></a></h3>

<p>Para subir as alterações via terminal, adicione as alterações que você fez ao seu repositório local com o seguinte comando:</p>

```shell
$ git add *
```

<p>Depois, você precisa dar um commit utilizando o seguinte comando (lembrar de add o número da issue correspondente sempre "#: conteúdo do commit"):</p>

```shell
$ git commit -m "#: Comentário curto, direto e claro sobre o que você fez"
```

<p>Depois, você precisa pedir que tudo isso vá para o repositório remoto usando o seguinte comando:</p>

```shell
$ git push
```

<p>Caso você precise subir uma branch nova, vai precisar trocar o comando anterior pelo:</p>

```shell
$ git push origin #feature/nome-apropriado
```

<p>Existem vários outros comandos de terminal além dos utilizados aqui, para saber mais, leia a documentação do <a href='https://git-scm.com/doc'>Git</a>.</p>

<h3>Gerenciamento de Conflitos<a name="content10"></a></h3>

<p>No VScode é mostrado em cor diferente as linhas de conflito. Para solucioná-las, temos as seguintes opções:</p>

<ul>

```
<li><b><i>Accept Current Change</i></b>: deve ser usada para manter a linha de código da brach develop</li>
<li><b><i>Accept Incoming Change</i></b>: deve ser usada para manter a linha de código da branch feature nova</li>
<li><b><i>Accept Both Change</i></b>: deve ser usada para manter as duas linhas de código das branchs</li>
<li><b><i>Compare Changes</i></b>: deve ser usada para comparar as mudanças entre os dois commits (develop e feature)</li>
```

</ul>

<p>No caso de haver conflitos e eles serem resolvidos, será necessário subir novamente as alterações.</p>

<h1>Referências</h1>

<ul>

```
<li><a href="https://www.atlassian.com/br/git/tutorials/what-is-version-control"><strong>O que é controle de versão?</strong></a> por Atlassian Bitbucket;</li>
<li><a href="https://www.toptal.com/software/trunk-based-development-git-flow"><strong>Trunk-based Development vs. Git Flow</strong></a> por Konrad Gadzinowski;</li>
<li><a href="https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow"><strong>Fluxo de trabalho de Gitflow</strong></a> por Atlassian Bitbucket;</li>
<li><a href="https://www.atlassian.com/br/continuous-delivery/continuous-integration/trunk-based-development"><strong>Desenvolvimento baseado em tronco</strong></a> por Kev Zettler;</li>
```

</ul>