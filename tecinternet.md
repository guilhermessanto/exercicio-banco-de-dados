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
    '1996',
    3,
    9,
    1

);

```

