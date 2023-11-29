# Locadora de Carros
## Projeto Banco de Dados Locadora de Carros
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
# Descrição Modelo Lógico
---

```
Produto(ID_Prod, Nome, Descrição, Preco_Venda, Quant_Estoque)
Funcionários(ID_Func, Nome, Salário, Cargo, Data_Contratação)
Pedido(ID_Ped, ID_Cli, ID_Prod, Data_Compra, Total_Compra)
Clientes(ID_Cli, Nome, Telefone, Email, Cidade, Estado, Rua)
Email(ID_Email,ID_cli,Email)
Telefone(ID_telefone,ID_cli,Telefone)
Produto_Pedido(ID_Pro_Ped,ID_Cli,ID_Prod)

```

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

---
CRUD
---
## Dados
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
# inserção Email

```
insert into Email values(null,'dom_quixote@gmail.com');
insert into Email values(null,'Marco_Nanini@hotmail.com');
insert into Email values(null,'Marco_Bonni@uol.com.br');
insert into Email values(null,'Marilia_Banana@uol.com.br');
insert into Email values(null,'Maria_maçã@terra.com.br');
insert into Email  values(null,'Maria_pera@gmail.com');
insert into Email values(null,'Maria_Helena@outlook.com');
insert into Email values(null,'Maria@outlook.com');
insert into Email values(null,'Lucilia@outlook.com');
insert into Email values(null,'Lucia@outlook.com');
insert into Email values(null,'Leandro@outlook.com');
insert into Email values(null,'Luciano@outlook.com');
insert into Email values(null,'Bruno@outlook.com');
insert into Email values(null,'Arthur@outlook.com');
insert into Email values(null,'Artur@outlook.com');
insert into Email values(null,'Alvim@outlook.com');
insert into Email values(null,'Aline@outlook.com');
insert into Email values(null,'Alice@outlook.com');
insert into Email values(null,'Alice_Maria@outlook.com');

```

# Inserção Telefone

```
insert into Telefone values (null,1698875-4689);
insert into Telefone values (null,1698875-4688);
insert into Telefone values (null,1698875-4687);
insert into Telefone values (null,1698875-4686);
insert into Telefone values (null,1698875-4685);
insert into Telefone values (null,1698875-4684);
insert into Telefone values (null,1698875-4683);
insert into Telefone values (null,1698875-4682);
insert into Telefone values (null,1698875-4681);
insert into Telefone values (null,1698875-4680);
insert into Telefone values (null,1698875-4690);
insert into Telefone values (null,1698875-4691);
insert into Telefone values (null,1698875-4692);
insert into Telefone values (null,1698875-4693);
insert into Telefone values (null,1698875-4620);
insert into Telefone values (null,1698875-4630);
insert into Telefone values (null,1698875-4640);
insert into Telefone values (null,1698875-4650);
insert into Telefone values (null,1698875-4655);
insert into Telefone values (null,1698875-4666);
insert into Telefone values (null,1698875-4677);



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
# Update 
```
update Pedidos set Total_compra=30000 ,ID_cli = 1,Data_Compra = '2019-12-02'  where ID_ped = 4;
update Pedidos set Total_compra=20000 ,ID_cli = 2,Data_Compra = '2014-11-02'  where ID_ped = 8;
update Pedidos set Total_compra=25000 ,ID_cli = 3,Data_Compra = '2013-02-02'  where ID_ped = 9;
update Pedidos set Total_compra=15000 ,ID_cli = 4,Data_Compra = '2011-01-02'  where ID_ped = 10;
update Pedidos set Total_compra=20000 ,ID_cli = 5,Data_Compra = '2009-09-02'  where ID_ped = 11;
update Pedidos set Total_compra=17000 ,ID_cli = 6,Data_Compra = '2012-08-02'  where ID_ped = 12;
update Pedidos set Total_compra=15000 ,ID_cli = 7,Data_Compra = '2011-07-02'  where ID_ped = 13;
update Pedidos set Total_compra=16600 ,ID_cli = 8,Data_Compra = '2010-10-02'  where ID_ped = 14;
update Pedidos set Total_compra=18000 ,ID_cli = 9,Data_Compra = '2023-10-02'  where ID_ped = 15;
update Pedidos set Total_compra=35000 ,ID_cli = 10,Data_Compra = '2022-10-02'  where ID_ped = 16;
update Pedidos set Total_compra=40000 ,ID_cli = 11,Data_Compra = '2021-10-02'  where ID_ped = 17;
update Pedidos set Total_compra=70000 ,ID_cli = 12,Data_Compra = '2019-10-20'  where ID_ped = 18;
update Pedidos set Total_compra=60000 ,ID_cli = 13,Data_Compra = '2019-10-15'  where ID_ped = 19;
update Pedidos set Total_compra=20000 ,ID_cli = 14,Data_Compra = '2019-08-02'  where ID_ped = 20;
update Pedidos set Total_compra=10000 ,ID_cli = 15,Data_Compra = '2015-09-02'  where ID_ped = 21;
update Pedidos set Total_compra=12000 ,ID_cli = 16,Data_Compra = '2017-10-02'  where ID_ped = 22;
update Pedidos set Total_compra=15000 ,ID_cli = 17,Data_Compra = '2019-12-02'  where ID_ped = 23;
update Pedidos set Total_compra=16000 ,ID_cli = 18,Data_Compra = '2019-11-02'  where ID_ped = 24;
update Pedidos set Total_compra=40000 ,ID_cli = 19,Data_Compra = '2017-10-02'  where ID_ped = 25;

```
# Select tabela Funcionarios

```
mysql> select * from Funcionarios;
+---------+------------+------------+------------------+---------+
| ID_Func | Nome       | Cargo      | data_contratacao | salario |
+---------+------------+------------+------------------+---------+
|       1 | Clarice    | Atendente  | 2020-12-12       | 2000.00 |
|       2 | Clark      | Manobrista | 2020-12-12       | 2500.00 |
|       3 | Adalberto  | Manobrista | 2010-10-12       | 2100.00 |
|       4 | Jeremias   | gerente    | 2006-05-12       | 5500.70 |
|       5 | Clark Kent | Ajudante   | 2020-11-15       | 1500.30 |
|       6 | Silene     | Atendente  | 2010-01-12       | 1800.00 |
|       7 | Gabriel    | Vendedor   | 2010-12-12       | 2600.00 |
|       8 | Silas      | Manobrista | 2020-12-12       | 2500.00 |
|       9 | Silvia     | Manobrista | 2020-12-12       | 2500.00 |
|      10 | Silvana    | Manobrista | 2020-12-12       | 2500.00 |
|      11 | Silvio     | Manobrista | 2020-12-12       | 2500.00 |
|      12 | Selena     | Manobrista | 2020-12-12       | 2500.00 |
|      13 | Danilo     | Manobrista | 2020-12-12       | 2500.00 |
|      14 | Tamires    | Manobrista | 2020-12-12       | 2500.00 |
|      15 | Cintia     | Manobrista | 2020-12-12       | 2500.00 |
|      16 | Carina     | Manobrista | 2020-12-12       | 2500.00 |
|      17 | karina     | Manobrista | 2020-12-12       | 2500.00 |
|      18 | koema      | Manobrista | 2020-12-12       | 2500.00 |
|      19 | Hector     | Manobrista | 2020-12-12       | 2500.00 |
|      20 | Ludovico   | Manobrista | 2020-12-12       | 1600.00 |
+---------+------------+------------+------------------+---------+
20 rows in set (0,00 sec)


```
---
# Select Email

```
mysql> select * from Email;
+----------+---------------------------+
| ID_Email | Email                     |
+----------+---------------------------+
|        1 | daniel@uol.com            |
|        2 | dom_quixote@gmail.com     |
|        3 | Marco_Nanini@hotmail.com  |
|        4 | Marco_Bonni@uol.com.br    |
|        5 | Marilia_Banana@uol.com.br |
|        6 | Maria_maçã@terra.com.br   |
|        7 | Maria_pera@gmail.com      |
|        8 | Maria_Helena@outlook.com  |
|        9 | Maria@outlook.com         |
|       10 | Lucilia@outlook.com       |
|       11 | Lucia@outlook.com         |
|       12 | Leandro@outlook.com       |
|       13 | Luciano@outlook.com       |
|       14 | Bruno@outlook.com         |
|       15 | Arthur@outlook.com        |
|       16 | Artur@outlook.com         |
|       17 | Alvim@outlook.com         |
|       18 | Aline@outlook.com         |
|       19 | Alice@outlook.com         |
|       20 | Alice_Maria@outlook.com   |
|       21 | Maria_dulce@outlook.com   |
+----------+---------------------------+
21 rows in set (0,00 sec)



```
---

# Select tabela Telefone

```
mysql> select *  from Telefone;
+--------+---------------+
| ID_cli | Telefone      |
+--------+---------------+
|      1 | 11 98144-3787 |
|      2 | 1694186       |
|      3 | 1694187       |
|      4 | 1694188       |
|      5 | 1694189       |
|      6 | 1694190       |
|      7 | 1694191       |
|      8 | 1694192       |
|      9 | 1694193       |
|     10 | 1694194       |
|     11 | 1694195       |
|     12 | 1694185       |
|     13 | 1694184       |
|     14 | 1694183       |
|     15 | 1694182       |
|     16 | 1694255       |
|     17 | 1694245       |
|     18 | 1694235       |
|     19 | 1694225       |
|     20 | 1694220       |
|     21 | 1694209       |
|     22 | 1694198       |
+--------+---------------+
22 rows in set (0,00 sec)

```
---

# Select tabela Produto_Pedido

```
mysql> select * from Produto_Pedido;
+------------+---------+
| ID_Pro_Ped | ID_Prod |
+------------+---------+
|          1 |       1 |
|          2 |      10 |
|          3 |      10 |
|          4 |      10 |
|          5 |      10 |
|          6 |      10 |
|          7 |      10 |
|          8 |      10 |
|          9 |      10 |
|         10 |      10 |
|         11 |      10 |
|         12 |      11 |
|         13 |      11 |
|         14 |      11 |
|         15 |       1 |
|         16 |       2 |
|         17 |       3 |
|         18 |       4 |
|         19 |       5 |
|         20 |       6 |
|         21 |       7 |
|         22 |       8 |
+------------+---------+
22 rows in set (0,00 sec)

```

# Relatórios

---
## Nome dos clientes começando pela letra A

```
mysql> select * from Clientes where Nome like 'A%';
+------------+-----------+-------------+--------+--------+---------------------------------+
| ID_Cliente | ID_Pedido | Nome        | Cidade | Estado | Rua                             |
+------------+-----------+-------------+--------+--------+---------------------------------+
|         20 |         3 | Arthur      | Franca | SP     | Rua das Carambolas azedas, 100a |
|         21 |         3 | Artur       | Franca | SP     | Rua do Jambolão, 100a fundos    |
|         22 |         3 | Alvim       | Franca | SP     | Rua do Jambolão, 300            |
|         23 |         3 | Aline       | Franca | SP     | Rua do Jambolão, 400            |
|         24 |         3 | Alice       | Franca | SP     | Rua do Jambolão, 500            |
|         25 |         3 | Alice Maria | Franca | SP     | Rua do Jambolão, 5000           |
+------------+-----------+-------------+--------+--------+---------------------------------+
6 rows in set (0,00 sec)


```

## Funcionários que tem salário inferior a 1800 ou igual
```
mysql> select * from Funcionarios where salario <= 1800;
+---------+------------+------------+------------------+---------+
| ID_Func | Nome       | Cargo      | data_contratacao | salario |
+---------+------------+------------+------------------+---------+
|       5 | Clark Kent | Ajudante   | 2020-11-15       | 1500.30 |
|       6 | Silene     | Atendente  | 2010-01-12       | 1800.00 |
|      20 | Ludovico   | Manobrista | 2020-12-12       | 1600.00 |
+---------+------------+------------+------------------+---------+
3 rows in set (0,00 sec)

```
## quantos funcionários são do cargo manobrista
```
mysql> select Nome from  Funcionarios where Cargo='Manobrista';
+-----------+
| Nome      |
+-----------+
| Clark     |
| Adalberto |
| Silas     |
| Silvia    |
| Silvana   |
| Silvio    |
| Selena    |
| Danilo    |
| Tamires   |
| Cintia    |
| Carina    |
| karina    |
| koema     |
| Hector    |
| Ludovico  |
+-----------+
15 rows in set (0,01 sec)
```
## Quantos manobristas tem o salário maior que 1800,00
```
mysql> select Nome,salario from  Funcionarios where Cargo='Manobrista' and salario > 1600 ;
+-----------+---------+
| Nome      | salario |
+-----------+---------+
| Clark     | 2500.00 |
| Adalberto | 2100.00 |
| Silas     | 2500.00 |
| Silvia    | 2500.00 |
| Silvana   | 2500.00 |
| Silvio    | 2500.00 |
| Selena    | 2500.00 |
| Danilo    | 2500.00 |
| Tamires   | 2500.00 |
| Cintia    | 2500.00 |
| Carina    | 2500.00 |
| karina    | 2500.00 |
| koema     | 2500.00 |
| Hector    | 2500.00 |
+-----------+---------+
14 rows in set (0,00 sec)

```
## Nome e endereço de clientes que residem na cidade de São Paulo
```
mysql> select nome,rua,Estado from Clientes where Cidade = 'São Paulo';
+-------------+--------------+--------+
| nome        | rua          | Estado |
+-------------+--------------+--------+
| Dom Quixote | Rua do Jambo | sp     |
+-------------+--------------+--------+
1 row in set (0,01 sec)
```
## Pedidos feitos antes do ano de 2022

```
mysql> select ID_Cli,Data_Compra,Total_compra from Pedidos where Data_compra < '2022';
+--------+-------------+--------------+
| ID_Cli | Data_Compra | Total_compra |
+--------+-------------+--------------+
|      1 | 2019-12-02  |     30000.00 |
|      2 | 2014-11-02  |     20000.00 |
|      3 | 2013-02-02  |     25000.00 |
|      4 | 2011-01-02  |     15000.00 |
|      5 | 2009-09-02  |     20000.00 |
|      6 | 2012-08-02  |     17000.00 |
|      7 | 2011-07-02  |     15000.00 |
|      8 | 2010-10-02  |     16600.00 |
|     11 | 2021-10-02  |     40000.00 |
|     12 | 2019-10-20  |     70000.00 |
|     13 | 2019-10-15  |     60000.00 |
|     14 | 2019-08-02  |     20000.00 |
|     15 | 2015-09-02  |     10000.00 |
|     16 | 2017-10-02  |     12000.00 |
|     17 | 2019-12-02  |     15000.00 |
|     18 | 2019-11-02  |     16000.00 |
|     19 | 2017-10-02  |     40000.00 |
+--------+-------------+--------------+
17 rows in set, 1 warning (0,00 sec)
```
## Selecionando os clientes para visualizar seus pedidos

```
mysql> select * from Clientes inner join Pedidos on Clientes.ID_Pedido = Pedidos.ID_Cli;
+------------+-----------+----------------+------------+--------+---------------------------------+--------+--------+-------------+--------------+
| ID_Cliente | ID_Pedido | Nome           | Cidade     | Estado | Rua                             | ID_Ped | ID_Cli | Data_compra | Total_compra |
+------------+-----------+----------------+------------+--------+---------------------------------+--------+--------+-------------+--------------+
|          7 |         1 | Dom Quixote    | São Paulo  | sp     | Rua do Jambo                    |      4 |      1 | 2019-12-02  |     30000.00 |
|          8 |         3 | Marco Nanini   | Franca     | SP     | rua do sabão                    |      9 |      3 | 2013-02-02  |     25000.00 |
|          9 |         3 | Marco Bonni    | Franca     | SP     | Avenida João Dias               |      9 |      3 | 2013-02-02  |     25000.00 |
|         10 |         3 | Marilia Banana | Franca     | SP     | Avenida Torquato Caleiros       |      9 |      3 | 2013-02-02  |     25000.00 |
|         11 |         3 | Maria maçã     | Franca     | SP     | Avenida Torquato Caleiros II    |      9 |      3 | 2013-02-02  |     25000.00 |
|         12 |         3 | Maria pera     | Franca     | SP     | Avenida Torquato Caleiros III   |      9 |      3 | 2013-02-02  |     25000.00 |
|         13 |         3 | Maria Helena   | Franca     | SP     | Avenida dos Bandeirantes        |      9 |      3 | 2013-02-02  |     25000.00 |
|         14 |         3 | Maria          | Franca     | SP     | Rua das Bananas, 10             |      9 |      3 | 2013-02-02  |     25000.00 |
|         15 |         3 | Lucilia        | Franca     | SP     | Rua das Bananas verdes, 10      |      9 |      3 | 2013-02-02  |     25000.00 |
|         16 |         3 | Lucia          | Franca     | SP     | Rua das Ameixas verdes, 10      |      9 |      3 | 2013-02-02  |     25000.00 |
|         17 |         3 | Leandro        | Franca     | SP     | Rua das Ameixas Pretas, 10      |      9 |      3 | 2013-02-02  |     25000.00 |
|         18 |         3 | Luciano        | Franca     | SP     | Rua das Carambolas, 10a         |      9 |      3 | 2013-02-02  |     25000.00 |
|         19 |         3 | Bruno          | Franca     | SP     | Rua das Carambolas, 100a        |      9 |      3 | 2013-02-02  |     25000.00 |
|         20 |         3 | Arthur         | Franca     | SP     | Rua das Carambolas azedas, 100a |      9 |      3 | 2013-02-02  |     25000.00 |
|         21 |         3 | Artur          | Franca     | SP     | Rua do Jambolão, 100a fundos    |      9 |      3 | 2013-02-02  |     25000.00 |
|         22 |         3 | Alvim          | Franca     | SP     | Rua do Jambolão, 300            |      9 |      3 | 2013-02-02  |     25000.00 |
|         23 |         3 | Aline          | Franca     | SP     | Rua do Jambolão, 400            |      9 |      3 | 2013-02-02  |     25000.00 |
|         24 |         3 | Alice          | Franca     | SP     | Rua do Jambolão, 500            |      9 |      3 | 2013-02-02  |     25000.00 |
|         25 |         3 | Alice Maria    | Franca     | SP     | Rua do Jambolão, 5000           |      9 |      3 | 2013-02-02  |     25000.00 |
+------------+-----------+----------------+------------+--------+---------------------------------+--------+--------+-------------+--------------+
19 rows in set (0,00 sec)
```

## selecionando os nomes com a compra a partir do ano de 2012

```
mysql> select Nome,Data_Compra from Clientes inner join Pedidos on Clientes.ID_Pedido = Pedidos.ID_Cli where Data_compra > '2012';
+----------------+-------------+
| Nome           | Data_Compra |
+----------------+-------------+
| Dom Quixote    | 2019-12-02  |
| Marco Nanini   | 2013-02-02  |
| Marco Bonni    | 2013-02-02  |
| Marilia Banana | 2013-02-02  |
| Maria maçã     | 2013-02-02  |
| Maria pera     | 2013-02-02  |
| Maria Helena   | 2013-02-02  |
| Maria          | 2013-02-02  |
| Lucilia        | 2013-02-02  |
| Lucia          | 2013-02-02  |
| Leandro        | 2013-02-02  |
| Luciano        | 2013-02-02  |
| Bruno          | 2013-02-02  |
| Arthur         | 2013-02-02  |
| Artur          | 2013-02-02  |
| Alvim          | 2013-02-02  |
| Aline          | 2013-02-02  |
| Alice          | 2013-02-02  |
| Alice Maria    | 2013-02-02  |
+----------------+-------------+
19 rows in set, 1 warning (0,00 sec)



```

## Filtrando nomes começados com A que compraramno ano de 2013

```
mysql> select Nome,Data_Compra from Clientes inner join Pedidos on Clientes.ID_Pedido = Pedidos.ID_Cli where Data_compra < '2013' or  Nome like 'A%';
+-------------+-------------+
| Nome        | Data_Compra |
+-------------+-------------+
| Arthur      | 2013-02-02  |
| Artur       | 2013-02-02  |
| Alvim       | 2013-02-02  |
| Aline       | 2013-02-02  |
| Alice       | 2013-02-02  |
| Alice Maria | 2013-02-02  |
+-------------+-------------+
6 rows in set, 1 warning (0,00 sec)


```
## Somando todos os pedidos
```
mysql> select sum(Total_compra) as total_Geral from Pedidos;
+-------------+
| total_Geral |
+-------------+
|   494600.00 |
+-------------+
1 row in set (0,01 sec)
```

