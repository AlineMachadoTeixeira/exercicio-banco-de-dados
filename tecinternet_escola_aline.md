
![](tecinternet_escola_etapa_um.png)

<!--  Crie um banco de dados chamado  -->
```sql
CREATE DATABASE tecinternet_escola_aline CHARACTER SET utf8mb4;
```


<!-- Criar tabela CURSO que fizemos no MySQL Workbench com está na foto -->
```sql
CREATE TABLE cursos(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(30) NOT NULL,
    carga_horaria TINYINT,
    professor_id TINYINT NULL 
); 
```

<!-- Criar tabela PROFESSORES que fizemos no MySQL Workbench com está na foto -->
```sql
CREATE TABLE professores(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    area_de_atuacao ENUM('design', 'desenvolvimento', 'infra')  NOT NULL,   
    curso_id TINYINT NOT NULL  
); 
```

<!-- Criar tabela ALUNOS que fizemos no MySQL Workbench com está na foto -->
```sql
CREATE TABLE alunos(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50),
    data_de_nascimento DATE NOT NULL,
    primeira_nota DECIMAL(4,2) NOT NULL,
    segunda_nota DECIMAL(4,2) NOT NULL,
    curso_id TINYINT NULL
); 
```


<!--  Criando a chave-estrangeira -->
```sql
ALTER TABLE alunos
    
    ADD CONSTRAINT fk_alunos_cursos  
    FOREIGN KEY (curso_id) REFERENCES cursos(id);
```


```sql
ALTER TABLE cursos
    
    ADD CONSTRAINT fk_cursos_professores1 
    FOREIGN KEY (professor_id) REFERENCES professores(id);
```

```sql
ALTER TABLE professores
    
    ADD CONSTRAINT fk_professores_cursos1   
    FOREIGN KEY (curso_id) REFERENCES cursos(id);
```


### Cadastre pelo menos 5 cursos: 

1. Front-End, carga horária 40h
2. Back-End, carga horária 80h
3. UX/UI Design, carga horária 30h
4. Figma, carga horária 10h
5. Redes de Computadores, carga horária 100h


<!-- Incluir No Tabela cursos TITULO e Carga Horaria-->

```sql
INSERT INTO cursos (
         titulo, carga_horaria ) 
    VALUES (
        'Front-End',        
        40
                        
    ), -- linha 1

    (
        'Back-End',        
        80
                        
    ), -- linha 2

    (
        'UX/UI Design',        
        30
                         
    ), -- linha 3

    (
        'Figma',        
        10
                        
    ), -- linha 4

     (
        'Redes de Computadores',        
        100
                       
    ); -- linha 5

```


### Cadastre pelo menos 5 professores: 

1. Jon Oliva, área infra
2. Lemmy Kilmister, área design
3. Neil Peart, área design
4. Ozzy Osbourne, área desenvolvimento
5. David Gilmour, área desenvolvimento

**Atenção:** durante o cadastro dos professores, associe cada professor a um curso na ordem contrária dos registros.


```sql
INSERT INTO professores (
         nome, area_de_atuacao, curso_id) 
    VALUES (
        'Jon Oliva',        
        'infra',
        5                 
    ), -- linha 1

    (
        'Lemmy Kilmister',        
        'design',
        4                  
    ), -- linha 2

    (
        'Neil Peart',        
        'design',
        3                
    ), -- linha 3

    (
        'Ozzy Osbourne',        
        'desenvolvimento',
        2                 
    ), -- linha 4

     (
        'David Gilmour',        
        'desenvolvimento',
        1                
    ); -- linha 5

```









