Notas para curso de testes da Udemy, disponível em:  https://www.udemy.com/course/test-techniques/learn/lecture/15921080?start=0#overview

- Black box techniques
    - testa o sistema sem nenhum conhecimento sobre suas estruturas internas
    - técnicas
        - equivalence partitioning: divide o sistema em diversas partições baseado em algum critério, de forma que as partições sejam equivalentes entre si
            - você deve ter um test case para cada partícula
            - deve ser usada em sistemas que tenham algum range
            - é importante testar valores que estejam fora do range das partículas i(invalid partitions)
        - boundary value analysis: analisa o sistema utilizando boundary values, pontos nos quais os programadores costumam cometer erros
            - considerada uma extensão do equivalence partitioning
            - pode usar 2 ou 3 valores para testar os limites
                - testa o valor limite e o valoor imediatamente anterior(fim da partição anterior) ou o valor limite, o valor imediatamente anterior e o imediatamente posterior
        - decision table testing: 
        - state transition testing: 