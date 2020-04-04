### Conceitos básicos
- WCF é baseado no conceito de comunicação baseada em messagens, e tuso que pode ser modelado como mensagem pode ser representado de uma maneira que permita a criação de uma API unificada para diferentes mecanismos de transporte
- As mensagens são trocadas entre endpoints e eles definem quais informações são necessárias para a troca de mensagens
- Um serviço WCF é exposto para o mundo como uma coleção de endpoints
    - um endpoint é um conceito relacionado a troca de mensagens; ele possui uma localização (endereço) que define por onde as mensagens podem ser recebidas/enviadas, uma especificação do mecanismo de comunicação (binding), que descrevecomo as mensagens deveriam ser enviadas, e a definição do set de mensagens que podem ser recebidas/enviadas naquela localização (um contrato de serviço)

### WCF Service Library - resumo
- Cria uma dll que representa o serviço
- Os serviços (interfaces) do WCF devem estar anotados com [ServiceContract]
    - System.ServiceModel
    - estabelece os métodos que o serviço vai disponibilizar
    - é preciso criar uma classe de serviços que implemente a interface
- As operações (métodos) devem ser anotadas com [OperationContract]
- Para que os métodos sejam acessíveis por meio de um navegador, é necessário anotar a classe com [WebInvoke], passando como parâmetros o método http , o formato da resposta (webMessageFormat) e o template da url
    - System.ServiceModel.Web
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
    - é preciso configurar os endpoints para sinalizar q eles são acessíveis por meio de um navegador (em endpoints behavior)
- No visual studio existe um cliente de teste para testar o serviço
- É preciso ter uma outra aplicação que suba a dll
    - ServiceHost numa aplicação console
        - no construtor, ela pede uma referência ao serviço que irá subir
        - adicionar referência ao projeto que contém o serviço
        - adicionar referência ao ServiceModel
        - para se conectar ao serviço é preciso adicionar o seu endpoint ao host, passando o serviço (a interface agora), o binding e a URI
    









###Fontes:
- https://cursos.alura.com.br/course/wcf-framework
- https://docs.microsoft.com/pt-br/dotnet/framework/wcf/fundamental-concepts