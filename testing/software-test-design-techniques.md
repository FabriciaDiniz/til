Notas para curso de testes da Udemy, disponível em:  https://www.udemy.com/course/test-techniques/learn/lecture/15921080?start=0#overview

### Black box techniques
    - testa o sistema sem nenhum conhecimento sobre suas estruturas internas
    - técnicas
        - equivalence partitioning (EP): divide o sistema em diversas partições baseado em algum critério, de forma que as partições sejam equivalentes entre si
            - você deve ter um test case para cada partícula
            - cada valor pertence apenas a uma partícula
            - as partículas podem ser de 2 tipos: válidas ou inválidas
            - deve ser usada em sistemas que tenham algum range
            - é importante testar valores que estejam fora do range das partículas (invalid partitions)
            - cobertura = número total de partículas cobertas pelos casos de teste / número total de partículas
                - testar 2 valores de uma partícula não aumenta a cobertura
            - pode ser aplicada para valores de input ou output
        - boundary value analysis (BVA): analisa o sistema utilizando boundary values, pontos nos quais os programadores costumam cometer erros
            - considerada uma extensão do equivalence partitioning
            - pode usar 2 ou 3 valores para testar os limites
                - testa o valor limite e o valor imediatamente anterior(fim da partição anterior) ou o valor limite, o valor imediatamente anterior e o imediatamente posterior
            - é importante testar os valores limite inválidos, aqueles que estão nas extremidades do seu range mas não são valores válidos
        - decision table testing: 
        - state transition testing: 