### Fundamentos de Angular
- Foca em evergreen browsers, suportando sempre as duas últimas versões vigentes dos navegadores do mercado
    - apenas remove os testes de integração com navegadores não suportados
- Possui 8 blocos principais
    - componentes: basicamente, são a view, encapsulam template, metadata, dado a ser mostrado na tela (data binding) e comportamento da view
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


## Criação de um projeto
- Requisitos
    - Node.js
    - Angular CLI
- ng new project_name
    - cria uma novo projeto
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


### Fontes
- https://cursos.alura.com.br/course/angular-fundamentos
- https://www.youtube.com/watch?v=tPOMG0D57S0