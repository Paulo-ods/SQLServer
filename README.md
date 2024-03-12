# Curso de SQLServer
SELECT:
-------------------------------------------------------------------------
    
    -SELECT *DISTINCT* coluna1                                             -> retorna dados únicos e não duplicados 
     FROM tabela
    
    
    -SELECT *                                                              -> extrai alguns dados específicos da 
     FROM tabela                                                           coluna dependendo da condição proposta.
     *WHERE* coluna = ''


    -SELECT *COUNT*(coluna)                                                -> retorna o n° de linhas da coluna selecionada 
     FROM tabela                                                           de acordo com a condição


    -SELECT *TOP 10* coluna                                                -> seleciona os top 10 ou a quantidade que quiser
     FROM tabela                                                           da coluna selecionada


    -SELECT coluna                                                         -> ordena a coluna selecionada na condição do
     FROM tabela                                                           WHERE em ordem crescente ou decrescente 
     WHERE coluna = ''
     *ORDER BY* coluna *ASC/DESC*


    -SELECT *                                                              -> encontra o valor entre o mínimo e o máximo
     FROM tabela                                                           da coluna da tabela selecionada
     WHERE coluna *BETWEEN* MIN and MAX


    -SELECT *                                                             -> verifica se tem os valores selecionados dentro do ()  
     FROM                                                                 se existem dentro da coluna desejada    
     WHERE coluna *IN* (2,3,4)


    -SELECT *								  -> quando sao o começo de algum dado e não lembra o 
     FROM tabela							  resto ou o começo ou o fim
     WHERE coluna *LIKE* 'san%'					 	  -> tanto para filtrar os dados que tem 'san' no começo da palavra,
     WHERE coluna *LIKE* '%to%'					  	  ou filtrar essa sílaba que existam no meio de algum dado


    -SELECT TOP 10 *SUM*(coluna) AS 'Soma'				 -> quando quer somar todos os valores de uma coluna *SUM*
     FROM tabela							 -> quando quer fazer a média total dos valores de uma coluna *AVG*
     SELECT *AVG*(coluna) AS 'Media'					 -> quando quer selecionar o *MIN* da coluna
     FROM tabela							 -> quando quer selecionar o *MAX* da coluna


    -SELECT coluna1, SUM(coluna2) AS 'nome'				 -> serve para agrupar resultados
     FROM tabela							 -> nesse caso agrupou a soma da coluna 2 em uma nova coluna
     GROUP BY coluna1							 com o nome que você colocar entre as aspas


    -SELECT coluna1, SUM(coluna2) AS 'nome'				 -> é usado para filtrar resultados de um agrupamento
     FROM tabela							 -> filtra dados já agrupados dependendo da condição 
     GROUP BY coluna 1							 que você impor no HAVING	
     *HAVING* COUNT(coluna1) > 10


    -SELECT P.Coluna1, P.Coluna2, PE.Coluna3, PE.Coluna4		 -> junta as colunas de uma tabela para outra
     FROM tabela AS P							 -> tem que colocar apelido 'AS PE' para identificar as colunas
     *INNER JOIN* tabela2 AS PE ON ColunaChave1 = ColunaChave2		 -> quando n especifíca as colunas junta todas colunas das 2 tabelas
     *FULL OUTER JOIN*							 -> retorna todos os registros correspondentes das 2 tabelas selecionadas
     									 quando são iguais, e quando não são retorna valor NULL
     *LEFT OUTER JOIN*		  					 -> retorna todos os registros da tabela A correspondente disoníveis, se não retorna NULL
     									 -> são todos os valores da segunda tabela + os valores comuns entre a primeira e a segunda através e primary key e foreign key


    -SELECT coluna1, coluna2						 -> seelciona a mesma quantidade de coluna do mesmo tipo:string, int
     FROM tabela1							 -> remove os dados duplicados
     *UNION*
     SELECT coluna1, coluna2
     FROM tabela2
-------------------------------------------------------------------------

# TIPOS DE DADOS
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

# CHAVE PRIMÁRIA E ESTRANGEIRA; CRIAÇÃO DE TABELAS

    -CHAVE PRIMÁRIA
        -> é basicamente uma coluna ou grupo de colunas, usada para identificar unicamente uma linha em uma tabela
            CREATE TABLE Nome_Tabela (
                nomeColuna TipodeDados PRIMARY KEY
                nomeColuna TipodeDados .....

    -CHAVE ESTRANGEIRA
        -> é simplesmente uma coluna ou grupo de colunas que é uma chave primária em outra tabela, é chamada de tabbela pai

    -CRIAR TABELA                                                                PRINCIPAIS TIPOS DE RESTRIÇÕES
        ->CREATE TABLE Nome_Tabela (                                             -NOT NULL= não permite nulos   
                nomeColuna TipodeDados Restrição da Coluna,                      -UNIQUE= força q todos os valores em uma coluna tem que ser diferentes  
                nomeColuna2 TipodeDados, .....                                   -PRIMARY KEY= uma junção de NOT NULL e UNIQUE 
                nomeColuna3 TipodeDados, .....                                   -FOREIGN KEY= identifica únicamente uma linha em outra tabela
                nomeColuna4 TipodeDados, PRIMARY KEY                             -CHECK= só quero valores acima de tantos seja inseridos em uma coluna, aplica restrições específicas
                ....                                                             -DEFAULT= força um valor padrão quando nenhum valor é passado   
            

-------------------------------------------------------------------------

# | INSERT INTO | UPDATE | DELETE | ALTER TABLE | DROP TABLE | #
    
     - # INSERT INTO tabela(coluna1, coluna2) #                            
     VALUES (valor1, valor2)

            -> os valosres entre parenteses vão preencher os dados da primeira linha da coluna selecionada
            -> é usado quando você ja tem uma tabela e quer inserir dados nela

    - # SELECT INTO tabelaNova FROM tabelaOriginal #

            -> serve para criar uma tabela rapidamente com os mesmos dados da original
            mesma estrutura e os mesmos dados das linhas 

    - # UPDATE nomeTabela
        SET coluna1 = valor1
          coluna2 = valor2
        WHERE id = 2 #
      
            -> serve para atualizar linhas de dados aonde você ja inseriu dados mas quer atualizar
            -> para não alterar a coluna inteira temos que colocar uma condição para pegar somente a linha desejada

    - # DELETE FROM nomeTabela
        WHERE 
        
            -> serve para apagar linhas do banco de dados
            -> sempre colocar WHERE para que não apague a tabela inteira

    - # 1.1 ALTER TABLE nomeTabela
            ADD colunaNova INT
                -> para adicionar nova coluna em uma tabela
            
        1.2 EXEC sp_RENAME 'tabela.ColunaAtual', 'ColunaNova', 'COLUMN'
                -> Altera o nome da coluna selecionada, primeiro o nome da tabela. coluna que quer alterar 
                o nome, coloca o novo nome e por fim o tipo que é a coluna

        1.3 EXEC sp_RENAME 'nomeTabelaAtual' 'nomeTabelaNova'
                -> Altera o nome da tabela ao invés de ser da coluna
                só colocar o nome atual e depois o novo nome

        1.4 ALTER TABLE tabela
            ALTER COLUMN coluna TipoDeDados
                -> Altera alguma categoria de Tipod de dados, como ex antes varchar(200) e executa o comando pra varchar(300)
                
    - # DROP TABLE nomeTabela #
    
        -> é usado para excluir uma tabela do banco de dados
        -> só consguimos dropar quando a tabela não é referencida por outra 

    - # TRUNCATE TABLE nomeTabela #
        -> serve para apagar tudo que esta dentro da tabela 
        -> vai apagar todos os dados de todas as linhas mas deixando as colunas da tabela

    - # CREATE TABLE CarteiraMotorista (                                -> serve para criar restrições de valores
	ID			INT				NOT NULL,                               que vão ser inseridos numa tabela no tipo 
	Nome		VARCHAR(250)	NOT NULL,                               de dados quando você esta criando uma.
	Idade		INT CHECK	(Idade >= 18))


    - # CREATE VIEW nomeTabelaNova AS                                    -> serve para criar uma nova tabela tipo relatório,
        SELECT Coluna1, Coluna2, Coluna3                                 que pega algumas colunas de acordo com a condição proposta   
        FROM ColunaOriginal                                              -> onde coluna cidade for = fco beltrao pega os dados da   
        WHERE coluna = ''#                                               coluna1, coluna2, coluna 3 e cria uma nova tabela 



    - # PROCEDURES # 							 -> conjunto de comandos que podem ser executados de uma só vez
    									 -> se tem uma rotina pra verificar tal coisa fazer tal coisa e depois excluir tal coisa 
									 podemos juntar todas essas ações em uma procedure só, sempre vai ser só um chamado
 

-------------------------------------------------------------------------

# | ISNULL | VIEW | HTTP |#

    - # SELECT ISNULL(nome, 'Nome não especificado') AS Nome		 -> se o valor da coluna nome for nulo, a função ISNULL irá retornar 'Nome n especificado',
	FROM Tabela #				 			 caso contrario ira retornar o valor da coluna 'nome' 
 

    - # SELECT coluna1, coluna2						 -> a consulta pode ler os dados da tabela, mesmo que eles estejam sendo modificados por 
	FROM tabela WITH(NOLOCK)					 outras transações no momento da execução da consulta
	WHERE condição; #


    - # VIEW #
    	-> é uma possibilidade de armazenar resultado de uma query dentro de uma tabela virtual
	-> não é possível adiocionar, excluir ou atualizar dados pois é somente uma vizualização
 	-> ganho de tempo, ao invés de criar sempre um select pra tal coisa, criamos uma view


    - # HTTP - Hyper Text Transfer Protocol #
    	-> GET: quando solicta informações para serem retornadas para você, tanto busca no sistema, retornar dados de um usuário e etc
     	-> POST: quando você quer salvar alguma informação no servidor, com esse metodo eu digo que quero grvar as info mandados no formulário
      	-> PUT: serve para alterar algum dado, adicionar, remover ou alterar
       	-> DELET: serve para remover informações

-------------------------------------------------------------------------

curso
		CREATE TABLE Alunos (
	ID_aluno						INT						PRIMARY KEY,
	nome							VARCHAR(200)			NOT NULL,
	data_nascimento					date					NOT NULL,
	sexo							VARCHAR(1)				NOT NULL,
	data_cadastro					DATETIME				NOT NULL,
	login_cadastro					VARCHAR(15)				NOT NULL
)	

CREATE TABLE situacao (
	ID_situacao						INT						PRIMARY KEY,
	situacao						VARCHAR(25)				NOT NULL,
	data_cadastro					DATETIME				NOT NULL, 
	login_cadastro					VARCHAR(15)				NOT NULL,
)

CREATE TABLE Cursos (
	ID_curso						INT						PRIMARY KEY,
	nome_curso						VARCHAR(200)			NOT NULL,
	data_cadastro					DATETIME				NOT NULL,
	login_cadastro					VARCHAR(15)				NOT NULL,
	data_alteracao					DATETIME				NULL,
	login_alteracao					VARCHAR(15)				NULL
)

CREATE TABLE Turmas (
	ID_turma						INT						PRIMARY KEY,
	ID_aluno						INT						NOT NULL,
	ID_curso						INT						NOT NULL,
	valor_turma						NUMERIC(15,2)			NOT NULL,
	desconto						NUMERIC(3,2)			NOT NULL,
	data_inicio						DATE					NOT NULL,
	data_termino					DATE					NULL,
	data_cadastro					DATE					NOT NULL,
	login_cadastro					VARCHAR(15)				
)	

CREATE TABLE Registro_Presenca		(
	ID_turma						INT						NOT NULL,
	ID_aluno						INT						NOT NULL,
	ID_siutacao						INT						NOT NULL,
	data_presenca					DATE					NOT NULL,
	data_cadastro					DATE					NOT NULL,
	login_cadastro					VARCHAR(15)				NOT NULL
)

--Turmas X Alunos
ALTER TABLE Turmas
	ADD CONSTRAINT fk_turmaAlunos FOREIGN KEY (ID_aluno) REFERENCES Alunos (ID_aluno);

--Turmas X Cursos
ALTER TABLE Turmas
	ADD CONSTRAINT fk_turmaCursos FOREIGN KEY (ID_curso) REFERENCES	Cursos (ID_curso);

--Reg. Pres. X Turmas
ALTER TABLE Registro_Presenca
	ADD CONSTRAINT fk_RPTurmas FOREIGN KEY (ID_turma) REFERENCES Turmas (ID_turma);

--Reg. Pres. X Alunos
ALTER TABLE Registro_Presenca
	ADD CONSTRAINT fk_RPAlunos FOREIGN KEY (ID_aluno) REFERENCES Turmas (ID_aluno);

	CREATE TABLE Alunos (
	ID_aluno						INT						PRIMARY KEY,
	nome							VARCHAR(200)			NOT NULL,
	data_nascimento					date					NOT NULL,
	sexo							VARCHAR(1)				NOT NULL,
	data_cadastro					DATETIME				NOT NULL,
	login_cadastro					VARCHAR(15)				NOT NULL
)	

CREATE TABLE situacao (
	ID_situacao						INT						PRIMARY KEY,
	situacao						VARCHAR(25)				NOT NULL,
	data_cadastro					DATETIME				NOT NULL, 
	login_cadastro					VARCHAR(15)				NOT NULL,
)

CREATE TABLE Cursos (
	ID_curso						INT						PRIMARY KEY,
	nome_curso						VARCHAR(200)			NOT NULL,
	data_cadastro					DATETIME				NOT NULL,
	login_cadastro					VARCHAR(15)				NOT NULL,
	data_alteracao					DATETIME				NULL,
	login_alteracao					VARCHAR(15)				NULL
)

CREATE TABLE Turmas (
	ID_turma						INT						PRIMARY KEY,
	ID_aluno						INT						NOT NULL,
	ID_curso						INT						NOT NULL,
	valor_turma						NUMERIC(15,2)			NOT NULL,
	desconto						NUMERIC(3,2)			NOT NULL,
	data_inicio						DATE					NOT NULL,
	data_termino					DATE					NULL,
	data_cadastro					DATE					NOT NULL,
	login_cadastro					VARCHAR(15)				
)	

CREATE TABLE Registro_Presenca		(
	ID_turma						INT						NOT NULL,
	ID_aluno						INT						NOT NULL,
	ID_siutacao						INT						NOT NULL,
	data_presenca					DATE					NOT NULL,
	data_cadastro					DATE					NOT NULL,
	login_cadastro					VARCHAR(15)				NOT NULL
)

--Turmas X Alunos
ALTER TABLE Turmas
	ADD CONSTRAINT fk_turmaAlunos FOREIGN KEY (ID_aluno) REFERENCES Alunos (ID_aluno);

--Turmas X Cursos
ALTER TABLE Turmas
	ADD CONSTRAINT fk_turmaCursos FOREIGN KEY (ID_curso) REFERENCES	Cursos (ID_curso);

--Reg. Pres. X Turmas
ALTER TABLE Registro_Presenca
	ADD CONSTRAINT fk_RPTurmas FOREIGN KEY (ID_turma) REFERENCES Turmas (ID_turma);

--Reg. Pres. X Alunos
ALTER TABLE Registro_Presenca
	ADD CONSTRAINT fk_RPAlunos FOREIGN KEY (ID_aluno) REFERENCES Turmas (ID_aluno);

	
