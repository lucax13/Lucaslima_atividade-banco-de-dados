# etapa 3
```sql
CREATE DATABASE tecinternet_escola_lucaslima
CHARACTER SET utf8mb4;
```
### tabela
```sql
CREATE TABLE cursos(id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
titulo VARCHAR(45) NOT NULL,
carga_horaria VARCHAR(45) NOT NULL,
professor_id INT NOT NULL
);

CREATE TABLE alunos(id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
nome VARCHAR(45) NOT NULL,
data_nascimento DATE,
nota_1 DECIMAL(10),
nota_2 DECIMAL(10),
curso_id INT NOT NULL 
);

CREATE TABLE professores(id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
nome VARCHAR(45) NOT NULL,
area_atuacao ENUM('desing', 'desenvolvimento', 'infra'),
professor_id INT NOT NULL
);
```

### chave estrangeira
```sql
ALTER TABLE cursos
ADD CONSTRAINT fk_cursos_professores FOREIGN KEY (professor_id) REFERENCES professores(id);

ALTER TABLE professores
ADD CONSTRAINT fk_professores_cursos FOREIGN KEY (curso_id) REFERENCES cursos(id);

ALTER TABLE alunos
ADD CONSTRAINT fk_alunos_cursos FOREIGN KEY (curso_id) REFERENCES alunos(id);

```

### curso e carga horaria
```sql
INSERT INTO cursos (titulo, carga_horaria) VALUES('Front-end', 40);

INSERT INTO cursos (titulo, carga_horaria) VALUES('Back-end', 80);

INSERT INTO cursos (titulo, carga_horaria) VALUES('Desing', 30);

INSERT INTO cursos (titulo, carga_horaria) VALUES('Figma', 10);

INSERT INTO cursos (titulo, carga_horaria) VALUES('Redes Computadores', 100);
```

### professores
```sql
INSERT INTO professores(nome, area_atuacao curso_id) VALUES('lemmy kilmister', 'desing', 16);

INSERT INTO professores(nome, area_atuacao curso_id) VALUES('jon oliva', 'infra', 17);

INSERT INTO professores(nome, area_atuacao curso_id) VALUES('neil peart', 'desing', 16);

INSERT INTO professores(nome, area_atuacao curso_id) VALUES('ozzy osbourne', 'desenvolvimento', 14);

INSERT INTO professores(nome, area_atuacao curso_id ) VALUES('david gilmour', 'desenvolvimento', 14);
```

### alunos
```sql
INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('marcos', '2000-03-07' , 10, 6, 17);

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('luan', '2006-09-08', 6, 9, 16);

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('pietra', '2009-08-07', 4, 5, 17);

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('lima','1990-01-03', 10, 2, 13 );

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('lua', '2009-01-12', 10, 2, 14);

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('amora', '2010-02-11', 10, 2, 16);





```

