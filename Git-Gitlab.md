# Introdução

Este documento contém tudo que você precisa saber para começar a usar o Git com o GitLab. Aqui, estão reunidas informações sobre comandos, padronizações, organização, estrutura e nomenclaturas. Para saber mais, leias as documentações do [Git](https://git-scm.com/doc) e [GitLab](https://docs.gitlab.com/ee/).

# Sumário

1. [O que é Controle de Versão?](#content1);
2. [Instalando e configurando o Git Bash](#content2);
3. [Acessando o GitLab](#content3);
4. [Projeto ou repositório: qual usar?](#content4);
5. [Clonando um projeto ou repositório](#content5);
6. [Criando um board](#content6);
7. [Aplicando Metodologias Ágeis](#content7);
8. [Como usar issues](#content8);
9. [Gitflow](#content9);
10. [Trunk based development](#content10);
11. [Subindo Alterações](#content11);
12. [Gerenciamento de Conflitos](#content12);

# Conteúdo

### O que é Controle de Versão?<a name="content1"></a>

O controle de versão é a prática de rastrear e gerenciar as alterações em um código de software. Os sistemas de controle de versão são ferramentas de software que ajudam as equipes de software a gerenciar as alterações no código ao longo do tempo.

Usar o software de controle de versão é uma prática recomendada para software de alto desempenho e equipes. O controle de versão também ajuda os desenvolvedores a se mover mais rápido e permite que as equipes preservem a eficiência e a agilidade à medida que a equipe é escalonada para incluir mais desenvolvedores.

Neste documento usaremos o [Git](https://git-scm.com/doc) e para versionar todas as aplicações e o [GitLab](https://docs.gitlab.com/ee/) para guardar a aplicação na nuvem e ficar disponível a todos os membros da equipe. Com esta ferramenta é necessário criar um repositório local, que será na memória do seu computador pessoal e um repositório remoto na nuvem que será no GitLab.

### Instalando e configurando o Git Bash<a name="content2"></a>

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

### Acessando GitLab<a name="content3"></a>

(EM CONSTRUÇÃO)

### Projeto ou repositório: qual usar?<a name="content4"></a>

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

### Clonando um projeto ou repositório<a name="content5"></a>

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
### Criando um board<a name="content6"></a>

### Aplicando Metodologias Ágeis<a name="content7"></a>

Para implementar uma Métodologia Ágil no seu board serão necessarios usar as labels e . As Labels servem para "linkar" as issues de modo a facilitar a localização, registro, acompanhamento e identificação das atividades realizadas.

##### Orientações gerais:
1. Não usar mais de uma Label de um mesmo grupo para classificar uma mesma issue
2. Usar o máximo de grupos de labels possíveis para classificar uma mesma issue
3. Usar recursos adicionais na descrição das issues como prints, documentos, checklist de itens a serem cumpridos e dados para consulta em banco para facilitar a compreensão e realização destas

##### Workflow Label Group:
* "Workflow: ready for development" Quando a issue está pronta para ser desenvolvida
* "Workflow: in Dev" Quando a issue está em desenvolvimento
* "Workflow: ieady for testing" Quando a issue está finalizada e pronta para ser testada
* "Workflow: blocked" Quando a atividade está impedida por algum motivo

**OBS:** Quando a issue for bloqueada ela deve conter um comentário justificando o bloqueio.

##### Type Label Group:
* "feature" Funcionalidade a ser implementada
* "bug Bug" reportado pelo cliente
* "enhancement" Melhoria
* "documentation" Construção, melhoria, incremento de documentação
* "QA: failed" Erros encontrados pela equipe de qualidade

##### Priority Label Group:
As Labels de prioridade nos ajudam a definir o tempo em que uma issue deve ser concluída. Se houver várias issues, as labels de prioridade orientam qual deve ser corrigido prioritariamente. Com isso é possível ter registro cronológico das atividades realizadas.
* "P1" Prioridade 1 - Urgente - Arrumar tão logo seja possível, na release atual e com menos de 2 dias)
* "P2" Prioridade 2 - Alta - Arrumar em até 5 dias)
* "P3" Prioridade 3 - Média - Arrumar em até 10 dias)
* "P4" Prioridade 4 - Baixa - Arrumar em até 30 dias)

##### Specialization Label Group:
As Labels de Specialization são par orientar que tipo de especialização a issue se refere.
* "frontend" Issues que envolvem aspectos do frontend (crud, integração com API, estilo, etc)
* "backend" Issues que envolvem aspectos do backend (API, etc)
* "database" Issues que envolvem Banco de dados (dumps, busca por dados, etc)
* "devops" Issues que envolvem devops (deploys automatizados, pipelines, etc)
* "designer" Issues que envolvem designer (prototipação, UX/UI, usabilidade, etc)

##### Enviroment Label Group:
* "Testing" A issue deve ser analisada em ambiente de teste
* "Homologation" A issue deve ser analisada em ambiente de homologação
* "Production" A issue deve ser analisada em ambiente de produção

##### Status Label Group:
* "Canceled" Quando a issue é cancelada

**OBS:** Quando a issue for cancelada ela deve conter um comentário justificando o cancelamento.

### Como usar issues<a name="content8"></a>
(EM CONSTRUÇÃO)

### Gitflow<a name="content9"></a>

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

1. Criar lógica de diálogo: ``#dialogue-logic``;
2. Criar lógica de filtros: ``#filter-logic``;
3. Criar lógica de pesquisa: ``#search-logic``

- __Desenvolver API ou parte dela:__ o nome da API e suas especificações.

Exemplos:

1. Desenvolver API de login: ``#login-API``;
2. Desenvolver API de pagamento: ``#payment-API``;
3. Desenvolver API de controles de usuário: ``#user-controllers-API``.

Demais casos, devem seguir padrões similares.

<img alt="gitflow" src="https://uploads.toptal.io/blog/image/129305/toptal-blog-image-1551794424851-b3d5928bc33edfc954ef460062e5cbcc.png">

Caso tenha ficado com dúvidas, assista a este [vídeo](https://www.youtube.com/watch?v=wzxBR4pOTTs).

##### Merges de aplicações

Merge é o processo responsável por unificar branchs criadas em uma única para obter uma determinada versão da aplicação. Toda vez que uma feature é criada, precisamos fazer um ``merge request`` que é basicamente uma solicitação de merge para o master da equipe. Essa medida visa reduzir merges de branchs com conflitos que definicam a aplicação.

Para solicitar um ``merge request`` siga os passos a seguir:

1. Após o <code>git push</code>, vá até a GitLab e localize no repositório na parte superior um botão para solicitação de merge (Ele aparecerá junto ao um aviso de commit realizado)</li>
2. Verifique se todas as alterações que você fez estão em conformidade com o que vc deseja</li>
3. Selecione a branch <code>develop</code> para receber as alterações da branch <code>feature/</code></li>
4. Em <i></i>, selecione o master para valiar o <code>merge request</code></li>
5. E como boa prática, envie uma mensagem de lembrete ao master para ele verificar o repositório

Há também a possibilidade de merge via terminal.

##### Para desenvolvedores _masters_

Volte para a branch develop com o seguinte comando:

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

### Trunk based development<a name="content10"></a>

<p>(EM CONSTRUÇÃO)</p>

<img alt="gitflow" src="https://uploads.toptal.io/blog/image/129304/toptal-blog-image-1551794413174-f4139c4be533dc592d49f9a0bcc330f0.png">

### Subindo Alterações<a name="content11"></a>

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

### Gerenciamento de Conflitos<a name="content12"></a>

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
