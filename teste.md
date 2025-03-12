
```sql
CREATE TABLE cursos(
  id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
  titulo VARCHAR(45) NOT NULL,
  carga_horaria VARCHAR(45) NOT NULL,
  professor_id INT NOT NULL,
  FOREIGN KEY (professor_id) REFERENCES professores(id)
);

CREATE TABLE alunos(
  id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
  nome VARCHAR(45) NOT NULL,
  data_nascimento DATE,
  nota_1 DECIMAL(4,2),
  nota_2 DECIMAL(4,2),
  curso_id INT NOT NULL,
  FOREIGN KEY (curso_id) REFERENCES cursos(id)
);

CREATE TABLE professores(
  id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
  nome VARCHAR(45) NOT NULL,
  area_atuacao ENUM('desing', 'desenvolvimento', 'infra') NOT NULL
);
 ```

 ```sql
 INSERT INTO cursos (titulo, carga_horaria) 
VALUES 
('Front-end', 40),
('Back-end', 80),
('Desing', 30),
('Figma', 10),
('Redes Computadores', 100);

INSERT INTO professores(nome, area_atuacao) 
VALUES 
('Lemmy Kilmister', 'desing'),
('Jon Oliva', 'infra'),
('Neil Peart', 'desing'),
('Ozzy Osbourne', 'desenvolvimento'),
('David Gilmour', 'desenvolvimento');

INSERT INTO alunos(nome, data_nascimento, nota_1, nota_2, curso_id) 
VALUES 
('Marcos', '2000-03-07', 10, 6, 17),
('Luan', '2006-09-08', 6, 9, 16),
('Pietra', '2009-08-07', 4, 5, 17),
('Lima', '1990-01-03', 10, 2, 13),
('Lua', '2009-01-12', 10, 2, 14),
('Amora', '2010-02-11', 10, 2, 16),
('Kelly', '1997-01-01', 10, 2, 16),
('Elly', '1997-01-01', 10, 2, 16),
('Ly', '1997-01-01', 10, 2, 16),
('Elly', '1997-01-01', 10, 2, 16),
('Ly', '1997-01-01', 10, 2, 16);

 ```

 ```sql
SELECT nome, data_nascimento 
FROM alunos
WHERE data_nascimento < '2009-01-01';

SELECT nome, id, ROUND((AVG(nota_1) + AVG(nota_2)) / 2, 2) AS "media dos alunos"
FROM alunos
GROUP BY nome, id;

SELECT titulo, id, carga_horaria, ROUND(carga_horaria * 0.25, 2) AS 'limite de faltas' 
FROM cursos
ORDER BY titulo;

SELECT nome, area_atuacao 
FROM professores
WHERE area_atuacao = 'desenvolvimento';

SELECT area_atuacao, COUNT(area_atuacao) AS "quantidade de professores"  
FROM professores
GROUP BY area_atuacao;

SELECT alunos.nome, cursos.titulo, cursos.carga_horaria
FROM alunos
JOIN cursos ON alunos.curso_id = cursos.id;

SELECT professores.nome, cursos.titulo 
FROM professores
JOIN cursos ON professores.id = cursos.professor_id
ORDER BY professores.nome;

SELECT alunos.nome, cursos.titulo, professores.nome
FROM alunos
JOIN cursos ON alunos.curso_id = cursos.id
JOIN professores ON cursos.professor_id = professores.id;

 ```