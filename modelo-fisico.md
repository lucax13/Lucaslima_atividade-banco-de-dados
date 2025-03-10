# etapa 3
```sql
CREATE DATABASE tecinternet_escola_lucaslima
CHARACTER SET utf8mb4;
```
### tabela
```sql
CREATE TABLE curso(id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
titulo VARCHAR(45) NOT NULL,
carga_horaria VARCHAR(45) NOT NULL,
curso_id INT
);

CREATE TABLE aluno(id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
nome VARCHAR(45) NOT NULL,
data_nascimento DATE,
nota_1 DECIMAL(10),
nota_2 DECIMAL(10),
curso_id INT
);

CREATE TABLE professor(id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
nome VARCHAR(45) NOT NULL,
area_atuacao ENUM('desing', 'desenvolvimento', 'infra')
);
```
```sql
INSERT INTO curso (titulo) VALUES('Front-end');
INSERT INTO curso (titulo) VALUES('Back-end');
INSERT INTO curso (titulo) VALUES('Desing');
INSERT INTO curso (titulo) VALUES('Figma');
INSERT INTO curso (titulo) VALUES('Redes Computadores');
```