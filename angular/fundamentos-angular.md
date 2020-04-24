### Fundamentos de Angular
- Foca em evergreen browsers, suportando sempre as duas últimas versões vigentes dos navegadores do mercado
    - apenas remove os testes de integração com navegadores não suportados
- Possui 8 blocos principais
    - componentes: basicamente, são a view; encapsulam template, metadata, dado a ser mostrado na tela (data binding) e comportamento da view
    - diretivas: responsável por modificar elementos do DOM e/ou seu comportamento; os componentes também são diretivas
    - roteamento: responsável pela navegação entre diferentes telas de um sistema
    - serviços: contém a lógica de negócio e podem se conectar com o backend
    - templates
    - metadata
    - data binding: associar informações entre o template e o componente
    - injeção de dependência
- Em Angular tudo é um componente; existe um componente raiz que contém tudo que tem na aplicação
    - cada componente pode ter outros componentes dentro dele
    - isso facilita testar a aplicação
- Os componentes podem se conectar ao backend, independente da linguagem dele, por meio de serviços
    - os serviços podem ser injetados em outras classes
- O Angular 2 ainda trabalha com o conceito de Single Page Applications (SPA), mas isso não impede que existam várias telas no sistema
    - a aplicação pode ser divida em módulos para facilitar a organização
- O module (NgModule) ajuda a organizar e modularizar a aplicação
    - as declarations consistem em todos os componentes, diretivas e pipes que serão utilizadas no módulo
    - os imports consistem em outros módulos que serão utilizados pelo módulo em questão ou pelos componentes que o compõem
    - os providers consistem nos serviços que estaram disponíveis para todos os componentes
        - serviços declarados no AppModule (o mais geral) ficam disponíveis para toda a aplicação
    - o metadado boostrap indica o componente que deve ser instanciado quando a aplicação for rodada
        - só está presente no módulo raiz
    - o exports define quais diretivas devem ser expostas para outros módulos
- Módulos de funcionalidades ajudam na organização do código, impedindo que o módulo raiz fique muito cheio de componentes
    - só o módulo é importado para o módulo raiz, no lugar de todos os componentes que ele contém
- Existem 4 formas de fazer o data binding
    - interpolação (interpolation): mostra o valor de um atributo ou um método do componente no template
        - {{ valor }}
    - binding de propriedade (property binding): também mostra o valor de um atributo ou um método do componente no template
        - [propriedade] = "valor"
        - por baixo dos panos o Angular chama um bind-propriedade="valor"
        - class binding é um tipo de property binding
    - event binding: permite escutar eventos no template (clique no botão, foco em campos de input) e executar um métod no componente
        - (evento) = "handler"
        - por baixo dos panos isso é um on-evento="handler"
    - two way data binding: template e componente são atualizados ao mesmo tempo
        - [(ngModel)] = "propriedade"
            - binding de evento e propriedade juntos
            - o ngModel é uma representação de uma entidade, uma diretiva de FormsModule
- Um componente possui os seguintes metadados:
    - selector: o nome do seletor que será usado para referenciar esse módulo
    - template/templateUrl: caminho para o arquivo html associado ao componente ou pequeno trecho de arquivo html hardcoded
    - styles: caminho para o arquivo css do componente ou estilo hardcoded
        - se for só um estilo, pode deixar hardcoded lembrando de utilizar templates de string (crase)
- Os estilos declarados em styles.css do módulo app estão dísponíveis para todos os componentes da aplicação
- O operador Elvis ("?" logo após o nome de uma variável que pode ou não ser nula como em cliente.endereco?.estado) checa se o valor da variável em questão é nulo e a exibe caso não seja, evitando que a chamada a uma variável nula levante erros na hora de executar
- Para fazer injeção de dependências, é preciso adicionar o decorator @Injectable à classe que será injetada, adicioná-la como um provider no app module e passa-la no construtor da classe que a injetará
    - no padrão singleton só há uma instância da classe para toda a aplicação
- A anotação @Input permite que um componente-pai possa passar informações para o componente-filho
- A anotação @Output permite que um componente-filho possa passar informações para o componente-pai
- O EventEmitter é utilizado para passr informações entre componentes
    - um componente é o emissor e todos aqueles componentes que estiverem "inscritos" no evento são assinantes e serão notificados sempre que um valor for emitido
    - para passar informações entre componentes utilizando instâncias diferentes de um serviço através do EventEmitter é preciso declarar a variável associada ao EventEmitter como estática

- As diretivas são formas de passar instruções para o template
    - os componentes também são diretivas, dizendo-se que são diretivas com template
    - as diretivas normalmente são compartilhadas por toda a aplicação
        - pode ser criada dentro da pasta shared ou dentro de uma pasta só para diretivas
    - existem as diretivas estruturais, que são utilizadas para modificar a estrutura do DOM e/ou código HTML
        - ngFor
        - ngIf
            - destrói o elemento com a alteração de true/false, o que significa que isso pode ser custoso para o sistema em termos de performance
                - recomendado para árvores de elementos grandes
                - uma alternativa é trabalhar com a propriedade hidden, fazendo um binding de propriedade, quando a árvore de elementos é pequena ou o custo de criar a árvore de elementos seja grande
            - cria um template por baixo dos panos com um property binding na variável "ngIf"
        - ngSwitch
            - usado com o property binding para ficar escutando o valor da expressão
    - existem as diretivas de atributos, que interagem com o elemento no qual foram aplicadas
        - ng-class
            - utiliza property binding associado a um objeto com todas as classes que se quer aplicar
            - é uma forma mais legível de adicionar diversos class bindings a um elemento
        - ng-style
            - mais um tipo de class binding, com o intuito de aplicar estilos a um elemento html
            - a sintaxe é semelhante à do ng-class
        - ng-content
            - mostra conteúdos passados externamente para o template, no caso conteúdos incluídos dentro da tag de chamada do componente
            - para exibir múltiplos conteúdos, pode-se fazer um select para diferentes seletores
                - caso existam várias divs com o mesmo seletor, o Angular concatena essas divs
    - ao criar uma diretiva de atributos, é preciso importar a classe ElementRef, que é quem pega a referência do elemento html onde a diretiva é chamada, e a classe Renderer, que é a classe que de fato irá modificar o elemento
    - quando se quer ouvir eventos relacionados ao elemento que contém a diretiva, usa-se o metadado HostListener
        - caso seja preciso modificar um atributo em função de um evento (como o mouse estar em cima do elemento) e desfazer a modificação quando o evento for encerrado, o mais elegante é usar o metadado HostBinding, que associa uma propridade a uma variável
    - ao criar uma diretiva estrutural, é preciso importar as classes TemplateRef, que pega a referência da tag onde a diretiva será chamada, e ViewContainerRef, que permite acessar as informações de dentro do elemento, essencialmente as informações com as quais queremos trabalhar

- Os serviços são classes responsáveis por buscar e enviar dados ao servidor
    - evitam repetir código
    - contém a lógica de negócio e classes utilitárias
    - caso um serviço seja adicionado como provider nos submódulos que o utilizam, não é preciso declará-lo como provider no app module, apenas adicionar os submódulos ao imports do app module
    - é possível adicionar o serviço no @Component dos componentes individuais, porém nesse caso será criada uma instância específica apenas para aquele componente


## Ciclo de vida de um componente
- Eventos (hooks)
    - ngOnChanges: antes do ngOnInit e quando o valor property-binding é atualizado
    - ngOnInit: disparado quando o componente é inicializado
    - ngDoCheck: a cada ciclo de verificação de mudanças
    - ngAfterContentInit: depois de inserir conteúdo externo na view
    - ngAfterContentChecked: a cada verificação do conteúdo inserido
    - ngAfterViewChecked: a cada verificação de conteúdo/conteúdo filho
    - ngOnDestroy: antes da diretiva/componente ser destruído

    - é uma boa prática colocar na classe que ela implementa as interfaces dos hooks que estarão sendo escutados
    - se o componente tiver uma propriedade de input, é mais interessante utilizar o ngOnChanges para carregar os valores no lugar do ngOnInit, já que este não é chamado


## Angular CLI
- Funções:
    - cria toda a estrutura do projeto
    - gera página html, arquivos typescript, CSS e de teste unitários iniciais
    - cria o arquivo package.json com todas as dependências do Angular
    - instala todas as dependências do node (npm install)
    - configura o Karma para executar os testes unitários com Jasmine
    - configura o Protractor para executar os testes end-to-end (e2e)
    - inicializa um repositório git no projeto e faz o commit inicial
    - cria todos os arquivos necessários para fazer o build da aplicação para produçãol


## Criação de um projeto
- Requisitos
    - Node.js
    - Angular CLI

- ng new project_name
    - cria uma novo projeto
    - alternativamente, você pode criar a pasta manualmente e então dar um ng init dentro da pasta
- ng g c component_name
    - cria um novo component com os arquivos necessários e atualiza o app.module para que o novo component seja reconhecido
- ng s ou ng serve
    - sobe o servidor do projeto
    - o --open faz com que o navegador seja aberto automaticamente quando o projeto sobe
- ng g m module_name
    - cria um módulo de funcionalidade
- ng g s service_name
    - cria o esqueleto para um serviço
    - pode-se usar <dir>/service_name para criar o serviço dentro de uma pasta específica e melhorar a organização do projeto
- ng build
    - gera a build de desenvolvimento no diretório dist
    - o build de dev não é ofuscado nem minificados
    - alternativas:
        - ng build --target=development --environment=dev
        - ng build --dev --e=dev
        - ng build --dev
- ng build --target=production --environment=prod
    - gera o build de produção
    - ofusca e minifica o código JS da aplicação
    - alternativas:
        - ng build --prod --e=prod
        - ng build --prod

- Diretórios
    - config:  contém configurações para deploy/build e teste
    - dist: onde é gerado o build da aplicação
        - é ignorado pelo git
    - e2e: contém os scripts para testes end-to-end
    - node_modules: contém os pacotes npm da app (package.json)
        - ignorado pelo git
    - public: diretório genérico que contém um arquivo .npmignore
    - src: diretório do código fonte da aplicação
        - contém código typescript/javascript, CSS, imagens e templates HTML


### Fontes
- https://cursos.alura.com.br/course/angular-fundamentos
- https://www.youtube.com/watch?v=tPOMG0D57S0