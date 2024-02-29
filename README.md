# Curso de SQLServer
SELECT:
-------------------------------------------------------------------------
    
    -SELECT *DISTINCT* coluna1                                             -> retorna dados únicos e não duplicados 
     FROM tabela
    
    
    -SELECT *                                                              -> extrai alguns dados específicos da 
    -FROM tabela                                                           coluna dependendo da condição proposta.
     *WHERE* coluna = ''


    -SELECT *COUNT*(coluna)                                                -> retorna o n° de linhas da coluna selecionada 
     FROM tabela                                                           de acordo com a condição


    -SELECT *TOP 10* coluna                                                -> seleciona os top 10 ou a quantidade que quiser
     FROM tabela                                                           da coluna selecionada


    -SELECT coluna                                                         -> ordena a coluna selecionada na condição do
    -FROM tabela                                                           WHERE em ordem crescente ou decrescente 
     WHERE coluna = ''
     *ORDER BY* coluna *ASC/DESC*


    -SELECT *                                                              -> encontra o valor entre o mínimo e o máximo
    -FROM tabela                                                           da coluna da tabela selecionada
     WHERE coluna *between* MIN and MAX


    -SELECT *                                                             -> verifica se tem os valores selecionados dentro do ()  
    -FROM                                                                 se existem dentro da coluna desejada    
     WHERE coluna IN (2,3,4)

-------------------------------------------------------------------------

    -TIPOS DE DADOS
        1.Boleanos | 2.Caractere | 3.Números | 4.Temporais

            # 1.BOLEANOS #
            -> Por padrão ele é iniciacializado como nulo, e pode receber tanto 1 ou 0
            para representar usa o tipo BIT
        
            # 2.CARACTERES #
            -> Tamanho fixo CHAR = Permite inserir até uma quantidade fixa de caracteres e sempre ocupa todo o espaço reservado 
            -> Tamanho variável VARCHAR / NVARCHAR = Permite inserir até uma quantidade que for definida, porém só usa o espaço que for preenchido

            # 3.NUMEROS #
            -> TINYINT = Não tem parte com valores fracionados (ex 1.23, 3.45), somente inteiros (1, 2234654, 465)
            -> SMALLINT, INT, BIGINT = Mesma coisa porém com limite maior na sequência colocada
            -> NUMERIC ou DECIMAL = Valores exatos, porém permite ter parte fracionada ou seja, os valores depois da vírgula
            que também pode ser especificado a precisão ex: NUMERIC(5,2) 452,32 | 5 é a quantidade total de números e 2 a quantidade após a vírgula
            -> REAL = Tem precisão aproximada de até 15 dígitos após a vírgula
            -> FLOAT = Mesmo conceito do real

            # 4.Temporais #
            -> DATE = armazena a data no formato ano/mes/dia
            -> DATETIME = armazena a data e horas no formato ano/mes/dia:hr:min:seg
            -> DATETIME2 = armazena a data e horas no formato ano/mes/dia:hr:min:seg:miliseg
            -> TIME = horas, minutos, segundos e milisegundos

-------------------------------------------------------------------------

# CHAVE PRIMÁRIA E ESTRANGEIRA

    -CHAVE PRIMÁRIA
        -> é basicamente uma coluna ou grupo de colunas, usada para identificar unicamente uma linha em uma tabela
            CREATE TABLE Nome_Tabela (
                nomeColuna TipodeDados PRIMARY KEY
                nomeColuna TipodeDados .....

    -CHAVE ESTRANGEIRA
        -> é simplesmente uma coluna ou grupo de colunas que é uma chave primária em outra tabela, é chamada de tabbela pai
            
