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
INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('marcos', '15-01-2003' , 10, 6,);

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2) VALUES('');

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2) VALUES('');

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2) VALUES('');

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2) VALUES('');

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2) VALUES('');

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2) VALUES('');
```

