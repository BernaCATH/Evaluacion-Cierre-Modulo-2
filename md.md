---
title: ""
tags: ""
---

## PRUEBA FINAL SQL

### DLL

```sql
CREATE TABLE alternativa (
    idalternativa       INTEGER NOT NULL,
    descripcion          VARCHAR2(200 CHAR),
    valorlogico          CHAR(1 CHAR),
    valorporcentual      INTEGER,
    idpregunta           INTEGER,
    idtest               INTEGER,
    pregunta_idpregunta  INTEGER NOT NULL,
    pregunta_idtest1     INTEGER NOT NULL
);

ALTER TABLE alternativa ADD CONSTRAINT alternativa_pk PRIMARY KEY ( idalternativa );

CREATE TABLE curso (
    idcurso  INTEGER NOT NULL,
    nombre   VARCHAR2(100)
);

ALTER TABLE curso ADD CONSTRAINT curso_pk PRIMARY KEY ( idcurso );

CREATE TABLE estudiante (
    idestudiante  INTEGER NOT NULL,
    nombre        VARCHAR2(30 CHAR),
    apellido      VARCHAR2(30 CHAR),
    idcurso       INTEGER
);

ALTER TABLE estudiante ADD CONSTRAINT estudiante_pk PRIMARY KEY ( idestudiante );

CREATE TABLE evaluacion (
    idevaluacion             INTEGER NOT NULL,
    puntaje                  NUMBER,
    nota                     NUMBER,
    idtest                   INTEGER,
    idestudiante             INTEGER,
    idcurso                  INTEGER,
    estudiante_idestudiante  INTEGER NOT NULL,
    test_idtest              INTEGER NOT NULL,
    curso_idcurso            INTEGER NOT NULL
);

ALTER TABLE evaluacion ADD CONSTRAINT evaluacion_pk PRIMARY KEY ( idevaluacion,
                                                                  curso_idcurso );

CREATE TABLE pregunta (
    idpregunta   INTEGER NOT NULL,
    enunciado    VARCHAR2(200 CHAR) NOT NULL,
    idtest       INTEGER,
    test_idtest  INTEGER NOT NULL
);

ALTER TABLE pregunta ADD CONSTRAINT pregunta_pk PRIMARY KEY ( idpregunta,
                                                              test_idtest );

CREATE TABLE test (
    idtest         INTEGER NOT NULL,
    nombretest     VARCHAR2(100),
    descripcion    VARCHAR2(200 CHAR),
    programa       VARCHAR2(100 CHAR),
    unidad         VARCHAR2(50 CHAR) NOT NULL,
    autor          VARCHAR2(40 CHAR),
    fechacreacion  DATE,
    idcurso        INTEGER,
    curso_idcurso  INTEGER NOT NULL
);

ALTER TABLE test ADD CONSTRAINT test_pk PRIMARY KEY ( idtest );

ALTER TABLE alternativa
    ADD CONSTRAINT alternativa_pregunta_fk FOREIGN KEY ( pregunta_idpregunta,
                                                         pregunta_idtest1 )
        REFERENCES pregunta ( idpregunta,
                              test_idtest );

ALTER TABLE evaluacion
    ADD CONSTRAINT evaluacion_curso_fk FOREIGN KEY ( curso_idcurso )
        REFERENCES curso ( idcurso );

ALTER TABLE evaluacion
    ADD CONSTRAINT evaluacion_estudiante_fk FOREIGN KEY ( estudiante_idestudiante )
        REFERENCES estudiante ( idestudiante );

ALTER TABLE evaluacion
    ADD CONSTRAINT evaluacion_test_fk FOREIGN KEY ( test_idtest )
        REFERENCES test ( idtest );

ALTER TABLE pregunta
    ADD CONSTRAINT pregunta_test_fk FOREIGN KEY ( test_idtest )
        REFERENCES test ( idtest );

ALTER TABLE test
    ADD CONSTRAINT test_curso_fk FOREIGN KEY ( curso_idcurso )
        REFERENCES curso ( idcurso );
```

### INGRESO DE DATOS

#### Tabla Estudiante

```sql
SELECT * FROM dual;

INSERT ALL
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (1,'Francisco','Jacobsen',1)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (2,'Javiera','Soto',1)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (3,'Diego','Menendez',1)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (4,'Marcela','Loyola',1)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (5,'Francisco','Prado',1)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (6,'Javiera','Castro',1)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (7,'Marcela','Perez',1)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (8,'Francisco','Jacobsen',1)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (9,'Javiera','Menendez',1)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (10,'Diego','Ortiz',1)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (11,'Adriana','Loyola',2)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (12,'Carolina','Castro',2)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (13,'Alejandro','Galleguillos',2)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (14,'Esteban','Perez',2)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (15,'Javier','Cortes',2)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (16,'Francisca','Salinas',2)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (17,'Karen','Garcia',2)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (18,'Carmen','Reyes',2)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (19,'David','Pinto',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (20,'Oscar','Castro',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (21,'Aurora','Riquelme',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (22,'Felipe','Andrade',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (23,'Daniela','Pizarro',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (24,'Manuel','Castillo',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (25,'Pablo','Salgado',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (26,'Teresa','Alarcon',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (27,'Patricia','Manriquez',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (28,'Marcelo','Mora',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (29,'Felipe','Abarca',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (30,'Pablo','Carrillo',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (31,'Omar','Arteaga',3)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (32,'Jorge','Castro',4)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (33,'Antonieta','Jara',4)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (34,'Pedro','Astorga',4)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (35,'Cecilia','Carmona',4)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (36,'Elias','Rifo',4)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (37,'Sandra','Ortega',4)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (38,'Lucia','Martinez',4)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (39,'Catalina','Garcia',4)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (40,'Andres','Vera',4)
INTO estudiante (idestudiante,nombre,apellido,idcurso) VALUES (41,'Julio','Donoso',4)
```

#### Tabla Evaluación

```sql
SELECT * FROM dual;

INSERT ALL
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (1,90,6.7,1,1,1)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (2,50,3.5,2,1,1)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (3,45,2.4,1,2,4)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (4,90,6.7,3,1,1)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (5,100,7.0,4,1,1)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (6,50,3.5,2,2,4)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (7,100,7.0,5,1,1)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (8,60,4.2,3,2,4)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (9,100,7.0,4,2,4)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (10,90,6.7,6,1,1)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (11,50,3.5,5,2,4)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (12,45,2.4,6,2,4)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (13,45,2.4,7,1,1)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (14,90,6.7,7,2,4)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (15,100,7.0,8,1,1)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (16,50,3.5,9,1,1)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (17,100,7.0,10,1,1)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (18,60,4.2,8,2,4)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (19,100,7.0,9,2,4)
INTO evaluacion (idevaluacion,puntaje,nota,estudiante_idestudiante,test_idtest,curso_idcurso) VALUES (20,100,7.0,10,2,4)
```

#### Tabla Curso

```sql
INSERT ALL
    INTO curso (idcurso,nombre) VALUES (1,'sala 039')
    INTO curso (idcurso,nombre) VALUES (2,'sala 022')
    INTO curso (idcurso,nombre) VALUES (3,'sala 057')
    INTO curso (idcurso,nombre) VALUES (4,'sala 025')
    INTO curso (idcurso,nombre) VALUES (5,'sala 028')
```

#### Tabla Test

```sql
SELECT * FROM dual;

INSERT ALL
    INTO test (idtest,nombretest,descripcion,programa,unidad,autor,fechacreacion,curso_idcurso) VALUES (1,'Proyecto Modulo 1','Programación orientada a objetos','Desarrollo de Aplicaciones Móviles Android Trainee','Unidad 1','Jimmy Muñoz',TO_DATE('06-05-2020', 'DD-MM-YYYY'),1)
    INTO test (idtest,nombretest,descripcion,programa,unidad,autor,fechacreacion,curso_idcurso) VALUES (2,'Operaciones Algoritmicas','Prueba Full Stack JAVA','Programación orientada a objetos','Desarrollo de Aplicaciones Full Stack Java Trainee','Unidad 2','Jacob Vega',TO_DATE('10-03-2020', 'DD-MM-YYYY'),4)
    INTO test (idtest,nombretest,descripcion,programa,unidad,autor,fechacreacion,curso_idcurso) VALUES (3,'Introducción al Human-Computer','User Experience','Diseñador UX/UI','Unidad 1','Manuel Soto',TO_DATE('06-06-2020', 'DD-MM-YYYY'),3)
```

#### Tabla Preguntas

```sql
SELECT * FROM dual
Agregamos preguntas de selección multiple

INSERT ALL
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (1,'Qué es herencia',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (2,'Qué es la Encapsulación',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (3,'Los niveles de acceso para el encapsulamiento son:',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (4,'Qué son las interfases',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (5,'Pueden las clases de Java heredar más de una clase',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (6,'Qué es Polimorfismo',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (7,'Qué es sobrecarga',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (8,'Diferencia entre Interfase y Clase',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (9,'Qué tipo de excepciones conoces',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (10,'Qué hace la palabra Static',1)
 
```
