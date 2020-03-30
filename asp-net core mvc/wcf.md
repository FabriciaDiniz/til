###WCF Service Library - resumo
- Cria uma dll que representa o serviço
- Os serviços (interfaces) do WCF devem estar anotados com [ServiceContract]
    - System.ServiceModel
    - estabelece os métodos que o serviço vai disponibilizar
    - é preciso criar uma classe de serviços que implemente a interface
- As operações (métodos) devem ser anotadas com [OperationContract]
- Classes de model devem ser anotadas com [DataContract]
    - System.Runtime.Serialization
- Os atributos das classes que serão trafegadas devem ser anotados com [DataMember]
    - indica quais atributos devem trafegar pelo serviço
- Configurações necessárias em appconfig (dá pra usar uma interface gráfica para isso)
    - definir o nome do serviço, selecionando na interface a dll do serviço
        - bin > Debug > seu_app.dll > seu_app_service
    - definir os endpoints para o serviço
        - endereço, protocolo (binding), contrato (o serviço em si)
    - alterar o endereço base (host)
- No visual studio existe um cliente de teste para testar o serviço
- É preciso ter uma outra aplicação que suba a dll
    - ServiceHost numa aplicação console
        - no construtor, ela pede uma referência ao serviço que irá subir
        - adicionar referência ao projeto que contém o serviço
        - adicionar referência ao ServiceModel
        - para se conectar ao serviço é preciso adicionar o seu endpoint ao host, passando o serviço (a interface agora), o binding e a URI
    









###Fontes:
- https://cursos.alura.com.br/course/wcf-framework