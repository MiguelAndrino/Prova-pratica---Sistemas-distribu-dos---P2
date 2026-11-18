# Prova-pratica---Sistemas-distribuídos---P2

Foi nos dado uma situação onde uma equipe de Ti identificou 3 erros no funcionamento do sistema, nossa tarefa é executar o codigo e verificar quais são os pontos de falha e corrigilos.

A primeira etapa foi criar o arquivo a qual iriamos conseguir utilizar o codigo, para isso criamos a pasta **simulado_distribuidos**.

E em seguida criamos o arquivo **central_pedidos.py**

-------------------------------------------------------------------------------------------------------------------------------------------------------

No Problema A, a empresa havia estabelecido que apenas dois processos podia estar sendo processados simultaneamente, no entanto o programa estava permitindo três.

Para resolver isto, basta que na variável **MAXIMO_SIMULTANEO** alteremos o valor de 3 para 2 e em seguida retiremos o numero '103' do bloco a seguir:
trabalhadores = [
    threading.Thread(
        target=processar_pedido,
        args=(numero,)
    )
    for numero in [101, 102, 103]
]

-------------------------------------------------------------------------------------------------------------------------------------------------------

O Problema B, dizia que ao realizar a sincronização do estoque o principal realizava a sincronização correta, porém a replica continuava a mostrar o valor anterior.

Foi identificado que na função sincronizar havia duas variaveis nomeadas 'replicas', ou seja uma recebia o valor da outra e no final ambas apresentavam o mesmo valor.

Para resolver isso foi necessario alterar uma delas para 'principal' assim resolvendo o problema. Segue o bloco alterado:

ANTES
def sincronizar():
    replica["estoque"]= replica["estoque"]
    
DEPOIS:
def sincronizar():
    replica["estoque"]= principal["estoque"]


---------------------------------------------------------------------------------------------------------------------------------------------------

Problema C





