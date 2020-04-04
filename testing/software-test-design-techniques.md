Notas para curso de testes da Udemy, disponível em:  https://www.udemy.com/course/test-techniques/learn/lecture/15921080?start=0#overview

### Black Box Testing
- testam o sistema sem nenhum conhecimento sobre suas estruturas internas

## Equivalence Partitioning (EP)
- divide o sistema em diversas partições baseado em algum critério, de forma que as partições sejam equivalentes entre si
- você deve ter um test case para cada partícula
- cada valor pertence apenas a uma partícula
- as partículas podem ser de 2 tipos: válidas ou inválidas
- deve ser usada em sistemas que tenham algum range
- é importante testar valores que estejam fora do range das partículas (invalid partitions)
- cobertura = número total de partículas cobertas pelos casos de teste / número total de partículas
    - testar 2 valores de uma partícula não aumenta a cobertura
- pode ser aplicada para valores de input ou output

## Boundary Value Analysis (BVA)
- analisa o sistema utilizando boundary values, pontos nos quais os programadores costumam cometer erros
- considerada uma extensão do equivalence partitioning
- pode usar 2 ou 3 valores para testar os limites
    - testa o valor limite e o valor imediatamente anterior(fim da partição anterior) ou o valor limite, o valor imediatamente anterior e o imediatamente posterior
- é importante testar os valores limite inválidos, aqueles que estão nas extremidades do seu range mas não são valores válidos

## Decision Table Testing 
- utilizada quando diferentes combinações de condições levam a resultados diferentes
- o número de casos de testes (table rules) vai ser 2^n
    - 2 representa perguntas de sim/não (2 reusltados possíveis)
    - n representa o número de perguntas que necessitam ser respondidas para gerar o resultado
    - esse número pode ser reduzido com base no número de casos de testes e das condições que precisam ser testadas
- é representada pela tabela de regras, com as condições e as "ações" (resultados) como coluna principal e as diferentes combinações de resultados (true ou false para cada pergunta) nas demais colunas

## State Transition Testing
- utilizado para sistemas que consistem em estados e transições
- desenhar o diagrama de estados ajuda a visualizar quais devems ser os casos de teste
- testar as transições resulta em uma cobertura maior do que testar os estados
    - cada transição independente (que não pode ser testada em conjunto com alguma das outras) requer um caso de teste único
    - o núm de casos de teste será igual ao núm de transições independentes
- normalmente o número de casos de teste pode ser inferido calculando o número de estados finais (dead states) do sistema, estados que não levam a outros
    - o núm de casos de teste será igual ao núm de estados finais
    - os casos de teste consistiriam em sair do estado inicial e chegar nos estados finais por caminhos distintos
