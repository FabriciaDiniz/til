## Comandos básicos
Anotações que eu acho importantes sobre os comandos básicos, incluindo apenas aqueles que eu não conhecia

- **>**: indica que algo deve ser inserido em um arquivo
    - ex: $ echo "Tenha um ótimo dia" > bom-dia.txt
    - sobrescreve o que existia no arquivo anteriormente

- **>>**: indica que algo deve ser _adicionado_ a um arquivo
    - ex: $ echo "E uma ótima semana" >> bom-dia.txt
    - adiciona ao final do que já existia no arquivo

- **cd**: o comando cd sem nenhum argumento volta para o diretório base

- **rm**: deleta o arquivo passado como argumento
    - a flag -r apaga recursivamente, permitindo usar o rm para apagar diretórios inteiros com múltiplos arquivos dentro
    - ex: $ rm -r workspace/

- **rmdir**: deleta o repositório passado como argumento
    - só apaga repositórios vazios

- **cat**: lê o arquivo passado como argumento
    - é possível ler vários arquivos ao mesmo tempo de se eles tiverem nomes similares, por exemplo: arquivo1.txt e arquivo2.txt poderiam ser lidos ao mesmo tempo passando os argumentos arquivo?.txt ou arquivo*.txt
    - para ler todos os arquivos que possuem uma mesma extensão, o argumento deve ser *.txt
    - ex: $ cat *.txt

- **mv**: quando os argumentos são dois arquivos, essencialmente muda o nome do arquivo, movendo o conteúdo do arquivo original para outro
    - quando um argumento é um arquivo e o outro é um diretório, move o arquivo para dentro do diretório passado

- **ls**: pode receber argumentos, como parte do nome dos arquivos que se quer listar ou um diretório diferente do que estamos
    - ex: $ ls bom-dia*
    - ex: $ ls diretorio-superespecifico/

- **zip**: compacta um arquivo ou diretório
    - deve-se estar fora do diretório para poder compactá-lo
    - aceita a falg -r para zipar recursivamente uma pasta e todo o seu conteúdo
    - ex: $ zip -r work.zip workspace/

- **unzip**: descompacta um arquivo .zip
    - pode ser usado com a flag -l, dessa forma apenas lista o que tem dentro do arquivo
    - ex: $ unzip -l work.zip  -> apenas exibe o que está compactado, sem descompactar

- **tar**: forma de compactar arquivos mais famosa no mundo Linux
    - é recursivo por padrão
    - apenas empacota vários arquivos em um único arquivo, sem realizar compactação
    - normalmente são utilizadas as flags -c (create) e -z (zip)
    - ex: $ tar -cz workspace > work.tar.gz || $ tar -czf work.tar.gz workspace/
    - para descompactar: $ tar -x < work.tar.gz || $ tar -xf work.tar.gz
        - o x vem de _extract_ e o < representa "leia desse arquivo"
    - outro formato de compactação que pode ser utilizado com o tar (invés do zip) é o bzip2, que é mais eficiente na compactação, porém leva mais tempo para criar o arquivo
        - o arquivo compactado possui a extensão .bz2
        - ex: $ tar -cjf work.tar.bz2 workspace/

- **head**: recebe o nome de um arquivo e traz as 10 primeiras linhas 
    - é útil quando se está lidando com arquivos grandes que seriam trabalhosos de examinar com o cat
    - aceita a flag -n para especificar um número de linhas diferente
    - ex: $ head -n 5 arquivo-grandao.txt

- **tail**: similar ao head, porém mostra as linhas finais de um arquivo
    - ex: $ tail -n 3 arquivo-grandao.txt

## Fontes
- [Linux I](https://cursos.alura.com.br/course/linux-ubuntu/) (Alura)