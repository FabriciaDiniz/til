1. Checar se tanto o Python quanto o Django estão instalados
    - $ python --version (ou py --version)
    - $ python -m django --version
    - caso o python não esteja instalado, baixar do site oficial; caso o django não esteja instalado, instalar com $ pip install django
    - opcionalmente, instalar o virtualenv wrapper para criar um ambiente dedicado para cada projeto Django
        - $ pip install virtualenvwrapper-win
        - $ mkvirtualenv myproject (cria o ambiente virutal)
        - $ workon myproject (ativa o ambiente virtual)

2. Criar um projeto
    - $ django-admin startproject mysite
        - atenção para não nomear o projeto com coisas como django ou test pq aí dá erro na hora de rodar os comandos
        - esse comando cria os seguintes arquivos:
            - diretório mysite/ que é só um container para o projeto
            - manage.py 
            - diretório interno mysite/ que é o pacote python do projeto
            - mysite
    - com o projeto criado dessa forma, já dá para subir o servidor e ver se está tudo funcionando corretamente
        - $ python manage.py runserver
        - o servidor usado por baixo dos panos é o Django development server, que não precisa vc configurar muita coisa mas que não deve ser utilizado em produção
        - o servidor pode ficar rodando em um terminal e em outro você pode ficar fazendo as alterações no projeto
        
3. Criar um app
    - um app é como se fosse um módulo, a existência de diversos módulos divide as responsabilidades dentro do projeto
    - $ python manage.py startapp nome_do_app
    - para que o django associe esse app ao seu projeto, é preciso registrar o app no arquivo settings.py do projeto, em INSTALLED_APPS
    - criar então a primeira view do projeto
        - o jeito rudimentar e mais simples possível: importar HttpResponse do django.http em views.py, criar a função index que recebe um request como parâmetro e retorna uma HttpResponse(‘texto’)
        - uma das formas de retornar alguma coisa para o usuário é através do render, q recebe primeiro o request e dps o nome do arquivo html que deve ser exibido
            - só é possível acessar com o render arquivos que estejam dentro de uma pasta chamada templates
    - no urls.py do app, adicionar o path para a view criada
        - a sintaxe pode ser path(‘’, views.index, name=’index’) ou url(r'^$', index, name='index') (pode ser necessário importar path ou url para que o mapeamento funcione)
            - a segunda forma requer um pouco de conhecimento em expressões regulares quando as views começarem a ficar mais complexas
        - pode-se dar um import nas views do projet com 'from .views import *' e então registrar o path apenas como path(‘’, index, name=’index’)
    - no urls.py do projeto, adicionar o path para as urls do app
        - a sintaxe pode ser path(‘mysite/polls/’, include(‘polls.urls’)) ou url(r'^', include('polls.urls'))