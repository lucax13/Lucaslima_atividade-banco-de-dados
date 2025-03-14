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
nota_1 DECIMAL(4,2),
nota_2 DECIMAL(4,2),
curso_id INT NOT NULL 
);

CREATE TABLE professores(id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
nome VARCHAR(45) NOT NULL,
area_atuacao ENUM('desing', 'desenvolvimento', 'infra'),
curso_id INT NOT NULL
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
INSERT INTO professores(nome, area_atuacao, curso_id) VALUES('lemmy kilmister', 'desing', 3);

INSERT INTO professores(nome, area_atuacao, curso_id) VALUES('jon oliva', 'infra', 5);

INSERT INTO professores(nome, area_atuacao, curso_id) VALUES('neil peart', 'desing', 4);

INSERT INTO professores(nome, area_atuacao, curso_id) VALUES('ozzy osbourne', 'desenvolvimento', 1);

INSERT INTO professores(nome, area_atuacao ,curso_id ) VALUES('david gilmour', 'desenvolvimento', 2);
```

### alunos
```sql
INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('marcos', '2000-03-07' , 10, 6, 1);

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('luan', '2006-09-08', 6, 9, 4);

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('pietra', '2009-08-07', 4, 5, 3);

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('lima','1990-01-03', 10, 2, 2 );

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('lua', '2009-01-12', 10, 2, 5);

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('amora', '2010-02-11', 10, 2, 5);

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('kelly', '1997-01-01', 10, 2, 2);

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('elly', '1997-01-01', 10, 2, 1);


INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('ly', '1997-01-01', 10, 2, 3);


INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('elly', '1997-01-01', 10, 2, 4);


INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) VALUES('ly', '1997-01-01', 10, 2, 5);
```
### crud consultas


1) Faça uma consulta que mostre os alunos que nasceram antes do ano 2009 
```sql
SELECT nome, data_nascimento FROM alunos
WHERE data_nascimento < '2009-01-01';
```

2) Faça uma consulta que calcule a média das notas de cada aluno e as mostre com duas casas decimais.
```sql
SELECT nome, id, ROUND((AVG(nota_1) + AVG(nota_2)) / 2, 2) AS "media dos alunos"
FROM alunos
GROUP BY nome, id;
```

3) Faça uma consulta que calcule o limite de faltas de cada curso de acordo com a carga horária. Considere o limite como 25% da carga horária. Classifique em ordem crescente pelo título do curso.
```sql
SELECT titulo, id, carga_horaria, ROUND(carga_horaria * 0.25, 2) AS 'limite de faltas' 
FROM cursos
WHERE id = 15; 
```

4) Faça uma consulta que mostre os nomes dos professores que são somente da área "desenvolvimento".
```sql
SELECT nome, area_atuacao FROM professores
WHERE area_atuacao = 'desenvolvimento';
```

5) Faça uma consulta que mostre a quantidade de professores que cada área ("design", "infra", "desenvolvimento") possui.
```sql
SELECT area_atuacao,
 COUNT(area_atuacao) AS "quantidade de professores"  
 FROM professores WHERE  
 area_atuacao = 'desenvolvimento';
 
SELECT area_atuacao,
 COUNT(area_atuacao) AS "quantidade de professores"  
 FROM professores WHERE  
 area_atuacao = 'design';  
 
 SELECT area_atuacao,
 COUNT(area_atuacao) AS "quantidade de professores"  
 FROM professores WHERE  
 area_atuacao = 'infra';  
```

6) Faça uma consulta que mostre o nome dos alunos, o título e a carga horária dos cursos que fazem.
```sql
SELECT alunos.nome, cursos.titulo, cursos.carga_horaria
FROM alunos
JOIN cursos ON alunos.curso_id = cursos.id;
```

7) Faça uma consulta que mostre o nome dos professores e o título do curso que lecionam. Classifique pelo nome do professor.
```sql
SELECT professores.nome, area_atuacao FROM professores
```
8) Faça uma consulta que mostre o nome dos alunos, o título dos cursos que fazem, e o professor de cada curso.
```sql
SELECT alunos.nome, cursos.titulo, professores.nome
FROM alunos
JOIN cursos ON alunos.curso_id = cursos.id
JOIN professores ON cursos.id = professores.curso_id;
```
9) Faça uma consulta que mostre a quantidade de alunos que cada curso possui. Classifique os resultados em ordem descrecente de acordo com a quantidade de alunos.
```sql
SELECT
  cursos.titulo AS Curso,
  COUNT(alunos.nome) AS Quantidade
FROM alunos
  JOIN cursos
  ON alunos.curso_id = cursos.id
GROUP BY cursos.titulo
ORDER BY Quantidade;
```

10) Faça uma consulta que mostre o nome dos alunos, suas notas, médias, e o título dos cursos que fazem. Devem ser considerados somente os alunos de Front-End e Back-End. Mostre os resultados classificados pelo nome do aluno.
```sql
SELECT
  alunos.nome AS Aluno,
  alunos.nota_1 AS Nota_1,
  alunos.nota_2 AS Nota_2,
  (alunos.nota_1 + alunos.nota_2) / 2 AS Media,
  cursos.titulo AS Curso
FROM alunos
JOIN cursos ON alunos.curso_id = cursos.id
WHERE cursos.titulo IN ('Front-End', 'Back-End')
ORDER BY alunos.nome;
```

11) Faça uma consulta que altere o nome do curso de Figma para Adobe XD e sua carga horária de 10 para 15.
```sql
UPDATE cursos SET titulo = 'Adobe XD' 
WHERE id = 4;

UPDATE cursos SET carga_horaria = 15 
WHERE id = 4;
```

12) Faça uma consulta que exclua um aluno do curso de Redes de Computadores e um aluno do curso de UX/UI.

```sql
DELETE FROM alunos WHERE id = 7;

DELETE FROM alunos WHERE id = 4;
```

13) Faça uma consulta que mostre a lista de alunos atualizada e o título dos cursos que fazem, classificados pelo nome do aluno.
```sql
SELECT
  alunos.nome AS Aluno,
  cursos.titulo AS Curso
FROM alunos
JOIN cursos ON alunos.curso_id = cursos.id
ORDER BY alunos.nome;

```


