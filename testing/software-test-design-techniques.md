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
    - pode-se também calcular o núm de casos de teste como o núm de ações a serem executadas + 1
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

## Use Case Testing
- os testes são derivados de casos de uso (descrição da interação entre atores em um sistema)


### White Box Testing
- observa a estrutura interna do sistema
- também chamada de architectured/structured base testing

## Statement coverage
- visa cobrir todas as linhas do código para obter 100% de cobertura
    - cobertura = núm de linhas testadas / núm total de linhas
- não é uma técnica muito eficiente
- o melhor é conseguir a cobertura de 100% com o mínimo de casos de teste possível

## Decision Coverage
- também chamado de branch coverage
- testa todas as saídas de condicionais (decision outcomes) no código
    - cobertura = saídas de condicionais cobertas / núm total de saídas de condicionais
- não é possível atingir 100% de cobertura com menos de 2 casos de teste
- 100% de decision coverage implica em 100% de statement coverage, mas o contrário não é verdade
- desenhar o fluxograma ajuda a visualizar quantos e quais casos de teste devem ser aplicados

## Condition Coverage
- testa cada condição nos casos de true/false presentes no código
    - é mais minucioso do que decision e statement coverage
    - uma decisão pode conter mais de uma condição (concatenadas com or/and)

## Path Coverage
- testa todos os caminhos possíveis no código
    - assim como em decision coverage, desenhar um fluxograma ajuda a entender os diferentes caminhos que devem ser testados e quantos casos de teste devem ser usados
- é mais robusto e mais minucioso, mas às vezes é impraticável de aplicar
    - nos casos mais complexos, o objetivo não é alcançar 100% de cobertura, apenas cobrir alguns dos caminhos possíveis
