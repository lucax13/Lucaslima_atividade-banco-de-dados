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
INSERT INTO curso (titulo, carga_horaria) VALUES('Front-end', 40);

INSERT INTO curso (titulo, carga_horaria) VALUES('Back-end', 80);

INSERT INTO curso (titulo, carga_horaria) VALUES('Desing', 30);

INSERT INTO curso (titulo, carga_horaria) VALUES('Figma', 10);

INSERT INTO curso (titulo, carga_horaria) VALUES('Redes Computadores', 100);
```