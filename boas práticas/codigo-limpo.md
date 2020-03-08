Anotações sobre o livro Código Limpo - Robert C. Martin

- Cap. 1: Código Limpo
    - De forma geral, um código limpo é um código objetivo, que pode ser lido e interpretado facilmente
    - É menos trabalhoso ter um código limpo se você já começar com essa intenção (obviamente), mas em um código maior é interessante ir alterando pequenas coisas como um nome de uma variável, remover ifs aninhados ou reduzir uma função muito grande
- Cap. 2: Nomes Significativos
    - nomes devem revelar o propósito de uma variável, se o nome da variável precisa de um comentário que o explique, ele não é um bom nome
    - é importante manter a consistência na nomeação de variáveis e funções, mas tomando cuidado com nomes muito longos ou muito parecidos, que acabam dificultando o entendimento e confundindo o leitor
    - é redundante incluir o tipo da variável no nome (como em List lista_variaveis)
    - dê nomes pronunciáveis as variáveis, nada de 'pszqint'
    - dê nomes passíveis de busca, uma variável chamada 'e' seria impossível de buscar
        - o tamanho do nome deve ser proporcional ao escopo; se for uma variável de um for, tudo bem chamar de i
    - classes e objetos devem ter nomes como substantivos
    - nomes de métodos devem conter verbos
    - adicione um contexto às variáveis que juntas consistem numa informação completa mas que separadas podem perder o seu sentido
        - no caso de nome, sobrenome, estado, cep, elas fazem sentido juntas, mas estado aparecendo isolado pode ter um sentido confuso
- Cap. 3: Funções