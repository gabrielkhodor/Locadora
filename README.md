# Locadora
## Projeto Banco de Dados Locadora
---
# Cenário

```
Cenário
Uma locadora de automóveis, necessita de um sistema no qual permita controlar com 
eficiência a disponibilidade dos veículos, as transações de aluguel, o histórico de 
cliente e funcionários, além de informações sobre os tipos de veículos oferecidos. 
Sendo preciso no sistema ter o cadastro de clientes, possuindo informações como 
nome, CPF, endereço e telefone. O cadastro dos veículos contendo modelo, placa, ano 
de fabricação, cor e status. O registro do funcionário que deve possuir nome, 
matrícula/id, e os dados de contratação para o cargo. O cadastro do aluguel do 
automóvel possuindo data da retirada e da devolução, o valor do aluguel desse 
período, tendo a quilometragem inicial e no fim do período a quilometragem rodada. E 
por fim o sistema deve ter o registro do tipo de veículo, contendo a categoria do 
automóvel, tarifa diária, a capacidade de passageiros e a capacidade do porta-malas.


```

# Modelo Entidade Relacionamento


![MER](https://github.com/gabrielkhodor/Locadora/assets/44448751/5b2116da-f7f7-41bd-8698-d30256cfc7e5)




# Modelo Lógico


![image](https://github.com/gabrielkhodor/Locadora/assets/44448751/f7307af4-ce91-4e57-a163-2c0e30e9d0c1)

---

# Modelagem Física

```
O modelagem física do banco de dados escolhido foi o Mysql da plataforma LINUX UBUNTU 18.04 LTS X86/64 

```
# Tabelas

```
drop database if exists Locadora;
create database Locadora;
use Locadora;


drop table if EXISTS Funcionarios ;
drop table if EXISTS Produtos;
drop table if EXISTS Clientes;
drop table if EXISTS Pedido;
drop table if EXISTS Email;
drop table if EXISTS Telefone;
drop table if EXISTS Produto_Pedido;

Create Table Funcionarios(
	ID_Func 		int  PRIMARY KEY auto_increment,
	Nome 			varchar (60)  		  not null,
	Cargo 			varchar (60)              not null,
	data_contratacao 	date 	                  not null,
	salario			decimal (10,2)             not null
);

CREATE TABLE Produtos(
	ID_Prod				int PRIMARY KEY auto_increment,
	ID_fun				int                       not null,
	Nome			 	varchar(60)               not null,
	Descricao		 	varchar(60)               not null,
	Preco_Venda		 	decimal                        not null,
	Quant_Estoque		 	int                       not null,
	FOREIGN KEY (ID_fun) REFERENCES Funcionarios(ID_func) 
);

CREATE TABLE Clientes(
	ID_Cliente              int PRIMARY KEY     auto_increment,
	ID_Pedido                  int                        not null,
	Nome                    varchar (60)               not null,
	Cidade                  varchar (60)               not null,
	Estado                  char (2)                   not null,
	Rua	                varchar (60)               not null
	
);

create table Pedidos(
	ID_Ped                  int PRIMARY KEY auto_increment,
	ID_Cli                  int                        not null, 
	Data_compra             date 			   not null,
	Total_compra            decimal (6,2)              not null
	

);


create table Email(
	ID_Email                int PRIMARY KEY auto_increment     not null,
	Email                   varchar (60) 			   not null
);


create table Telefone(
	ID_cli                  integer PRIMARY KEY auto_increment,
	Telefone                 integer                   not null

);



create table Produto_Pedido(
	ID_Pro_Ped              integer PRIMARY KEY auto_increment,
	ID_Prod                 integer                   not null

);




```
---

# Dados
## Tabela Funcionários
```
inserção tabela Funcionarios

insert into Funcionarios values(null, 'Clark', 'Manobrista','2020-12-12',2500.00);
insert into Funcionarios values(null, 'Adalberto', 'Manobrista','2010-10-12',2100.00);
insert into Funcionarios values(null, 'Jeremias', 'gerente','2006-05-12',5500.70);
insert into Funcionarios values(null, 'Clark Kent', 'Ajudante','2020-11-15',1500.30);
insert into Funcionarios values(null, 'Silene', 'Atendente','2010-01-12',18000.50);
insert into Funcionarios values(null, 'Gabriel', 'Vendedor','2010-12-12',2600.00);
insert into Funcionarios values(null, 'Clak', 'Manobrista','2020-12-12',1500.00);
insert into Funcionarios values(null, 'Clak', 'Manobrista','2020-12-12',1500.00);
insert into Funcionarios values(null, 'Clak', 'Manobrista','2020-12-12',1500.00);
insert into Funcionarios values(null, 'Clak', 'Manobrista','2020-12-12',1500.00);
insert into Funcionarios values(null, 'Clak', 'Manobrista','2020-12-12',1500.00);
insert into Funcionarios values(null, 'Clak', 'Manobrista','2020-12-12',1500.00);
insert into Funcionarios values(null, 'Clak', 'Manobrista','2020-12-12',1500.00);
insert into Funcionarios values(null, 'Lucas Calango', 'Vendedor','2020-10-12',2500.00);
insert into Funcionarios values(null, 'Cleiton', 'Vendedor','2020-10-12',2500.00);
insert into Funcionarios values(null, 'Carlos', 'Vendedor','2020-10-12',2500.00);
insert into Funcionarios values(null, 'Cintia', 'Vendedora','2020-10-12',2500.00);
insert into Funcionarios values(null, 'Camila', 'Vendedora','2020-10-12',2500.00);

```
---

## Tabela Produtos
```
insert into Produtos values(null,1,'celta','cor vermelho',18000,1);
insert into Produtos values(null,2,'gol ','cor verde',20000,1);
insert into Produtos values(null,3,'corsa','cor azul',18500,2);
insert into Produtos values(null,4,'parati','cor vermelho',22000,1);
insert into Produtos values(null,5,'celta','cor preto',15000,1);
insert into Produtos values(null,6,'celta','cor branco',10000,1);
insert into Produtos values(null,7,'corola','cor vermelho',60000,1);
insert into Produtos values(null,8,'corsa','cor verde',17000,1);
insert into Produtos values(null,9,'meriva','cor vermelho',30000,1);
insert into Produtos values(null,10,'titã','moto varias cores 0 km',16000,10);
insert into Produtos values(null,11,'fan','cores variasdas semi nova',15000,5);
insert into Produtos values(null,12,'honda civic','cor branca',58000,1);
insert into Produtos values(null,13,'hilux',' o km',180000,2);
insert into Produtos values(null,14,'nissan ','preta',180000,1);
insert into Produtos values(null,15,'golf 2.0','cor vermelho',25000,1);
insert into Produtos values(null,16,'vectra','cor vermelho semi novo',28000,1);
insert into Produtos values(null,17,'novo uno','verde',15000,1);
insert into Produtos values(null,18,'novo uno ','azul',16000,1);
insert into Produtos values(null,19,'novo uno','preto',13000,1);
insert into Produtos values(null,20,'uno r3','cor amarelo semi nivo',55000,1);


```
## Tabela Clientes

```

insert into Clientes values(null,'Dom Quixote','Birigui','sp','Rua das Nações');            
insert into Clientes values(null,'Marco Nanini','Franca','SP','Avenida José Lourenço');
insert into Clientes values(null,'Marco Bonni','Franca','SP','Av Lizete coelho Lourenço');   
insert into Clientes values(null,'Marilia Banana'  ,'Franca'  ,'SP','Rua das Laranjeiras');       
insert into Clientes values(null,'Maria maçã','Franca','SP','Rua das Amoreiras');         
insert into Clientes values(null,'Maria pera','Franca','SP','Rua das Mexericas');         
insert into Clientes values(null,'Maria Helena','Franca','SP','Rua das Melismas');          
insert into Clientes values(null,'Maria','Franca','SP','Rua das Amoxas');            
insert into Clientes values(null,'Lucilia','Franca','SP','Rua dos Limões');            
insert into Clientes values(null,'Lucia','Franca','SP','Rua das Lixias');            
insert into Clientes values(null,'Leandro','Franca', 'SP','Rua dos Abacaxis');          
insert into Clientes values(null,'Luciano','Franca', 'SP','avenida do Melão');          
insert into Clientes values(null,'Bruno','Franca','SP','Av Getúlio Vargas');         
insert into Clientes values(null,'Arthur','Franca'  ,'SP','Rua Gal. Carneiro');         
insert into Clientes values(null,'Artur','Franca','SP'      ,'Rua Gal. Osório');           
insert into Clientes values(null,'Alvim','Franca','SP','Rua Tiradentes');            
insert into Clientes values(null,'Aline','Franca','SP','Rua Caramuru');              
insert into Clientes values(null,'Alice','Franca'  ,'SP','Avenida Brasil');             
insert into Clientes values(null,'Alice Maria','Franca','SP','Avenida Brasil');           

```


## select na tabela Clientes
```
mysql> select * from Clientes;
+------------+-----------+----------------+--------+--------+---------------------------+
| ID_Cliente | ID_Pedido | Nome           | Cidade | Estado | Rua                       |
+------------+-----------+----------------+--------+--------+---------------------------+
|          7 |         1 | Dom Quixote    | Birigui| sp     | Rua das Nações            |
|          8 |         2 | Marco Nanini   | Franca | SP     | Avenida José Lourenço     |
|          9 |         3 | Marco Bonni    | Franca | SP     | Av Lizete coelho Lourenço |   
|         10 |         4 | Marilia Banana | Franca | SP     | Rua das Laranjeiras       |
|         11 |         5 | Maria maçã     | Franca | SP     | Rua das Amoreiras         |
|         12 |         6 | Maria pera     | Franca | SP     | Rua das Mexericas         |
|         13 |         7 | Maria Helena   | Franca | SP     | Rua das Melismas          |
|         14 |         8 | Maria          | Franca | SP     | Rua das Amoxas            |
|         15 |         9 | Lucilia        | Franca | SP     | Rua dos Limões            |
|         16 |         10| Lucia          | Franca | SP     | Rua das Lixias            |
|         17 |         11| Leandro        | Franca | SP     | Rua dos Abacaxis          |
|         18 |         12| Luciano        | Franca | SP     | avenida do Melão          |
|         19 |         13| Bruno          | Franca | SP     | Av Getúlio Vargas         |
|         20 |         14| Arthur         | Franca | SP     | Rua Gal. Carneiro         | 
|         21 |         15| Artur          | Franca | SP     | Rua Gal. Osório           |
|         22 |         16| Alvim          | Franca | SP     | Rua Tiradentes            |
|         23 |         17| Aline          | Franca | SP     | Rua Caramuru              |
|         24 |         18| Alice          | Franca | SP     | Avenida Brasil            | 
|         25 |         19| Alice Maria    | Franca | SP     | Avenida Brasil            |
+------------+-----------+----------------+--------+--------+---------------------------+

```

# Select tabela Pedidos

```
mysql> select * from Pedidos;
+--------+--------+-------------+--------------+
| ID_Ped | ID_Cli | Data_compra | Total_compra |
+--------+--------+-------------+--------------+
|      4 |      1 | 2019-12-02  |     30000.00 |
|      8 |      2 | 2014-11-02  |     20000.00 |
|      9 |      3 | 2013-02-02  |     25000.00 |
|     10 |      4 | 2011-01-02  |     15000.00 |
|     11 |      5 | 2009-09-02  |     20000.00 |
|     12 |      6 | 2012-08-02  |     17000.00 |
|     13 |      7 | 2011-07-02  |     15000.00 |
|     14 |      8 | 2010-10-02  |     16600.00 |
|     15 |      9 | 2023-10-02  |     18000.00 |
|     16 |     10 | 2022-10-02  |     35000.00 |
|     17 |     11 | 2021-10-02  |     40000.00 |
|     18 |     12 | 2019-10-20  |     70000.00 |
|     19 |     13 | 2019-10-15  |     60000.00 |
|     20 |     14 | 2019-08-02  |     20000.00 |
|     21 |     15 | 2015-09-02  |     10000.00 |
|     22 |     16 | 2017-10-02  |     12000.00 |
|     23 |     17 | 2019-12-02  |     15000.00 |
|     24 |     18 | 2019-11-02  |     16000.00 |
|     25 |     19 | 2017-10-02  |     40000.00 |
+--------+--------+-------------+--------------+
19 rows in set (0,01 sec)

```





