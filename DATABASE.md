##### Instruções acerca do banco de dados



O software UandA, tanto em sua versão desktop quanto web, utiliza uma base de dados em MySQL para adequado funcionamento e integridade. É possível rodar o sistema sem a base de dados, no entanto, a maior parte das funcionalidades não funcionarão. Por isso, caso queira aproveitar da total experiência do software, recomendo que instale o MySQL Server junto ao MySQL Workbench usando o MySQL Installer. Indico que busque por tutoriais ensinando como fazer a instalação em seu computador.



Caso tenha instalado, abra o MySQL Workbench em uma conexão local e execute o seguinte código, que criará a base de dados do software, junto às tabelas e a alguns registros necessários para o seu correto funcionamento (basta copiar, colar e rodar com o ícone de relâmpago na Query):







/\*Criação do banco de dados\*/



CREATE DATABASE uanda;

USE uanda;





/\*Criação das tabelas\*/



CREATE TABLE moderadores (

id INT NOT NULL AUTO\_INCREMENT,

funcao CHAR(1) NOT NULL,

nome VARCHAR(100) NOT NULL,

data\_nascimento DATE NOT NULL,

genero CHAR(1) NOT NULL,

nacionalidade VARCHAR(45) NOT NULL,

cpf VARCHAR(14) NOT NULL,

numero\_cadastro INT NOT NULL,

senha VARBINARY(44) NOT NULL,

PRIMARY KEY (id)

);



CREATE TABLE emails (

id INT NOT NULL AUTO\_INCREMENT,

endereco VARCHAR(100) NOT NULL,

id\_moderador INT NOT NULL,

PRIMARY KEY (id),

FOREIGN KEY (id\_moderador) REFERENCES moderadores(id)

);



CREATE TABLE telefones (

id INT NOT NULL AUTO\_INCREMENT,

numero VARCHAR(45) NOT NULL,

id\_moderador INT NOT NULL,

PRIMARY KEY (id),

FOREIGN KEY (id\_moderador) REFERENCES moderadores(id)

);



CREATE TABLE localidades (

id INT NOT NULL AUTO\_INCREMENT,

rua VARCHAR(100) NOT NULL,

bairro VARCHAR(100) NOT NULL,

cidade VARCHAR(100) NOT NULL,

estado VARCHAR(45) NOT NULL,

id\_moderador INT NULL,

PRIMARY KEY (id),

FOREIGN KEY (id\_moderador) REFERENCES moderadores(id) ON DELETE SET NULL

);



CREATE TABLE modulos (

id INT NOT NULL AUTO\_INCREMENT,

nome\_modulo VARCHAR(45) NOT NULL,

id\_moderador INT NULL,

PRIMARY KEY (id),

FOREIGN KEY (id\_moderador) REFERENCES moderadores(id) ON DELETE SET NULL

);



CREATE TABLE buscas (

id INT NOT NULL AUTO\_INCREMENT,

localidade INT,

modulo INT NOT NULL,

texto VARCHAR(200) NOT NULL,

data\_hora DATETIME NOT NULL,

PRIMARY KEY (id),

FOREIGN KEY (localidade) REFERENCES localidades(id),

FOREIGN KEY (modulo) REFERENCES modulos(id)

);



CREATE TABLE animais (

id INT NOT NULL AUTO\_INCREMENT,

localidade INT NOT NULL,

modulo INT NOT NULL,

foto MEDIUMBLOB NOT NULL,

data\_registro DATETIME NOT NULL,

titulo VARCHAR(45) NOT NULL,

descricao VARCHAR(500) NOT NULL,

preco FLOAT(8,2) UNSIGNED NOT NULL,

idade FLOAT(5,2) UNSIGNED NOT NULL,

id\_moderador INT NULL,

PRIMARY KEY (id),

FOREIGN KEY (id\_moderador) REFERENCES moderadores(id)

);





/\*Inserção de alguns dados nas tabelas\*/



INSERT INTO moderadores VALUES

(1, 'G', 'Gerente 1', '1995-05-31', 'M', 'Brasileiro', '999.999.999-99', 999999, aes\_encrypt('123456', '#@uanda25@#')),

(2, 'F', 'Funcionário 1', '1992-08-14', 'M', 'Brasileiro', '111.111.111-11', 111111, aes\_encrypt('123321', '#@uanda25@#'));



INSERT INTO emails (endereco, id\_moderador) VALUES

('gerente1@gmail.com', 1),

('funcionario1@outlook.com', 2);



INSERT INTO telefones (numero, id\_moderador) VALUES

('71 11111-1111', 1),

('11 99999-9999', 2);



INSERT INTO modulos (nome\_modulo, id\_moderador) VALUES

('Animais de Estimação', 1),

('Animais de Produção', 1);

