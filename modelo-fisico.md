# etapa 3
```sql
CREATE DATABASE tecinternet_escola_lucaslima
CHARACTER SET utf8mb4;
```
### tabela
```sql
CREATE TABLE curso(id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
titulo VARCHAR(45) NOT NULL
);
```
```sql
INSERT INTO curso (titulo) VALUES('Front-end');
INSERT INTO curso (titulo) VALUES('Back-end');
INSERT INTO curso (titulo) VALUES('UX/UI Desing');
INSERT INTO curso (titulo) VALUES('Figma');
INSERT INTO curso (titulo) VALUES('Redes Computadores');
```