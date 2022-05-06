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
ADD CONSTRAINT fk_cursos_professores  FOREIGN KEY (professor_id) REFERENCES professores(id);

```