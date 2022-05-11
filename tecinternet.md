```sql
CREATE DATABASE tecinternet_escola_guilherme CHARACTER SET utf8mb4;

CREATE TABLE cursos(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(30) NOT NULL,
    carga_horaria TINYINT NOT NULL,
    professor_id SMALLINT NOT NULL
);

CREATE TABLE professores(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    area_de_atuacao ENUM('design','desenvolvimento','infra') NOT NULL,
    curso_id TINYINT NOT NULL
);

CREATE TABLE alunos(
    id SMALLINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    data_nascimento DATE NOT NULL,
    primeira_nota DECIMAL(4.2) NOT NULL,
    segunda_nota DECIMAL(4.2) NOT NULL,
    curso_id TINYINT NOT NULL
);

ALTER TABLE cursos 
ADD CONSTRAINT fk_curso_professor  FOREIGN KEY (professor_id) 
REFERENCES professores(id);

ALTER TABLE `cursos` 
ADD CONSTRAINT `fk_curso_professor` 
FOREIGN KEY (`professor_id`) REFERENCES `professores`(`id`)

INSERT INTO cursos(titulo, carga_horaria) VALUES(
    'Front-End',
    40
);
INSERT INTO cursos(titulo, carga_horaria) VALUES (
    'Back-End',
    80
),
(
    'UX/UI Design',
    30
),
(
    'Figma',
    10
),
(
    'Redes de Computadores',
    100
);
INSERT INTO professores(nome, area_de_atuacao, curso_id) VALUES 
(
    'Jon Oliva',
    'área infra',
    5
),
(
    'Lemmy Kilmister',
    'área design',
    4
),
(
    'Neil Peart',
    'área design',
    3
),
(
    'Ozzy Osbourne',
    'área desenvolvimento',
    2
),
(
    'David Gilmour',
    'área desenvolvimento',
    1
);



INSERT INTO alunos (nome, data_nascimento, primeira_nota, segunda_nota, curso_id) VALUES (
    'Guilherme',
    '1998-10-31',
    7.5,
    8
);
INSERT INTO alunos (nome, data_nascimento, primeira_nota, segunda_nota, curso_id) VALUES (
    'Felipe',
    '1995-01-02',
    8,
    7,
    2
),
(
    'João',
    '2000-04-13',
    6.5,
    8,
    4
),
(
    'Carol',
    '2001-05-10',
    7.3,
    9,
    3
),
(
    'Rayssa',
    '2008-10-04',
    8,
    7,
    4
);

INSERT INTO alunos (nome, data_nascimento, primeira_nota, segunda_nota, curso_id) VALUES (
    'Joel',
    '1993-02-12',
    3,
    5,
    5
),
(
    'Lara',
    '1973-07-27',
    6,
    5,
    5
),
(
    'Juliana',
    '1969-08-10',
    2,
    9,
    1
),
(
    'Rivaldo',
    '1983-02-25',
    1,
    7,
    2
),
(
    'Mauro',
    '1998-07-14',
    3,
    9,
    1

);

INSERT INTO alunos (nome, data_nascimento, primeira_nota, segunda_nota, curso_id) VALUES (
    'Eneias',
    '1972-02-12',
    3.6,
    5.9,
    5
);

-- ETAPA 3
--01
SELECT nome, data_nascimento FROM alunos WHERE data_nascimento < 20091231;   
--02
SELECT nome ,primeira_nota,segunda_nota, ROUND(AVG((primeira_nota + segunda_nota)/2),2) AS 'Média' 
FROM alunos GROUP BY nome; 
--03
SELECT titulo, ROUND((carga_horaria * 0.25),1) AS "Limite de faltas" FROM cursos GROUP BY id;
--04
SELECT nome, area_de_atuacao FROM professores WHERE area_de_atuacao LIKE '%desenvolvimento%';
--05
SELECT  area_de_atuacao, COUNT(DISTINCT id) AS 'Quantidade de professores' 
FROM professores GROUP BY area_de_atuacao; 
--06
SELECT alunos.nome, cursos.titulo, cursos.carga_horaria 
FROM alunos INNER JOIN cursos ON alunos.curso_id = cursos.id ;
--07
SELECT professores.nome, cursos.titulo
FROM professores INNER JOIN cursos ON professores.curso_id = cursos.id  ORDER BY professores;
--08
SELECT alunos.nome AS Alunos, cursos.titulo AS Curso, professores.nome AS Professores
FROM alunos INNER JOIN cursos ON alunos.curso_id = cursos.id INNER JOIN professores ON cursos_id = cursos.id;
--09
SELECT cursos.titulo AS Curso, COUNT(alunos.curso_id) AS "Quantidade" 
FROM cursos INNER JOIN  alunos ON alunos.curso_id = cursos.id GROUP BY cursos.titulo 
ORDER BY quantidade DESC;    
--10
SELECT nome ,primeira_nota,segunda_nota, ROUND(AVG((primeira_nota + segunda_nota)/2),2) AS 'Média',
cursos.titulo AS curso FROM alunos INNER JOIN cursos ON alunos.curso_id = cursos.id  
WHERE curso_id IN(1,2) GROUP BY nome ORDER BY titulo ASC; 
--11
UPDATE cursos SET titulo = 'Adobe XD' , carga_horaria = 15 WHERE id = 4;
--12

```

