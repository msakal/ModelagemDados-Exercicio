# Criando Tabelas


## Criando DataBase
```sql
CREATE DATABASE tecinternet_escola_marcellosa CHARACTER SET utf8mb4;
USE DATABASE tecinternet_escola_marcellosa;
```

### Criar Tabelas
```sql
CREATE TABLE cursos(
    id SMALLINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(30) NOT NULL,
    carga_horaria SMALLINT NOT NULL,
    professor_id SMALLINT NULL
);

CREATE TABLE professores(
    id SMALLINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    area_de_atuacao ENUM('design', 'desenvolvimento', 'infra') NOT NULL,
    curso_id SMALLINT NOT NULL
);

CREATE TABLE alunos(
    id SMALLINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    data_nascimento DATE NOT NULL,
    primeira_nota DECIMAL(4, 2) NOT NULL,
    segunda_nota DECIMAL(4, 2) NOT NULL,
    curso_id SMALLINT NOT NULL
);
```

### Criação da Chave Estrangeira (FK - relacionamento entre as tabelas)
```sql
ALTER TABLE cursos
    ADD CONSTRAINT fk_cursos_professores
    FOREIGN KEY(professor_id) REFERENCES professores(id);

ALTER TABLE professores
    ADD CONSTRAINT fk_professores_cursos
    FOREIGN KEY(curso_id) REFERENCES cursos(id);

ALTER TABLE alunos
    ADD CONSTRAINT fk_alunos_cursos
    FOREIGN KEY(curso_id) REFERENCES cursos(id);
```
