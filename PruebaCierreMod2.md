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
    INTO test (idtest,nombretest,descripcion,programa,unidad,autor,fechacreacion,curso_idcurso) VALUES (2,'Operaciones Algoritmicas','Prueba Full Stack JAVA','Desarrollo de Aplicaciones Full Stack Java Trainee','Unidad 2','Jacob Vega',TO_DATE('10-03-2020', 'DD-MM-YYYY'),4)
    INTO test (idtest,nombretest,descripcion,programa,unidad,autor,fechacreacion,curso_idcurso) VALUES (3,'Introducción al Human-Computer','User Experience','Diseñador UX/UI','Unidad 1','Manuel Soto',TO_DATE('06-06-2020', 'DD-MM-YYYY'),3)
```

#### Tabla Pregunta

```sql
SELECT * FROM dual

INSERT ALL
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (1,'Qué es herencia',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (2,'Qué es la Encapsulación',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (3,'Los niveles de acceso para el encapsulamiento son:',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (4,'Al hablar de interfases podemos decir que:',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (5,'Pueden las clases de Java heredar más de una clase',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (6,'Qué es Polimorfismo',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (7,'Qué significa Paso por valor',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (8,'Con respecto a una Clase podemos afirmar que:',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (9,'Qué tipo de excepciones conoces',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (10,'Qué hace la palabra Static',1)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (11,'Las principales estructuras algorítmicas son:',2)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (12,'Un algoritmo debe cumplir con las siguientes características:',2)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (13,'Las instrucciones de un programa Java pueden ser:',2)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (14,'Las dos herramientas más utilizadas comúnmente para describir algoritmos son:',2)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (15,'Qué es Pseint',2)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (16,'En Pseint las instrucción de ciclo son:',2)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (17,'Las dimensiones pueden ser:',2)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (18,'Respecto a los subprocesos en Pseint podemos afirmar que:',2)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (19,'Qué son los operadores lógicos',2)
    INTO pregunta (idpregunta,enunciado,test_idtest) VALUES (20,'Cuando hablamos de operadores racionales nos referimos a:',2)
```

#### Tabla Alternativa

```sql
SELECT * FROM dual;
Agregamos alternativas para respuestas

INSERT ALL
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (1,'Es la base de la reutilización del código','V',50,1,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (2,'Mediante la herencia se pueden crear relaciones entre objetos que extienden a objetos madres','F',0,1,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (3,'Mediante la herencia se pueden crear relaciones entre objetos que extienden a objetos padres','V',50,1,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (4,'Es la facultad que tienen los objetos de heredad estructuras externas','F',0,1,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (5,'Es la forma de proteger u ocultar las propiedades de un objeto','V',50,2,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (6,'Se proteje un objeto estableciendo permisos y niveles de visibilidad','V',50,2,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (7,'Es la protección de un objeto por medio de 2 niveles de acceso o encapsulamiento','F',50,2,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (8,'Es una forma de ocultar del código fuente','F',0,2,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (9,'tres','V',50,3,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (10,'dos','F',0,3,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (11,'Publico(Public) - Protegido(Protected) y Privado(Private)','V',50,3,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (12,'Protegido(Protected) y Privado(Private)','F',0,3,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (13,'Las interfaces definen lo que una clase que la implemente debe hacer pero no la forma como lo hará','V',50,4,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (14,'Las interfaces son completamente abstractas y que todos sus métodos lo son y no poseen implementación','V',50,4,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (15,'Las interfaces definen lo que una clase debe hacer y la forma en como lo hará','F',0,4,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (16,'Las interfaces son completamente abstractas pero sus métodos no lo son','F',0,4,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (17,'No permite la herencia múltiple','V',50,5,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (18,'Solo permite la construcción de interfaz para acceder a una forma de simulación o implementación limitada de la herencia múltiple','V',50,5,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (19,'Si permite la herencia múltiple','F',0,5,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (20,'Sólo puede heredar a dos clases','F',0,5,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (21,'La capacidad que tienen los objetos de comportarse de múltiples formas recurriendo a la herencia','V',50,6,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (22,'Consiste en hacer referencia a objetos de una clase que puede tomar comportamientos de objetos que son descendientes de esta','V',50,6,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (23,'Se refiere a la propiedad por la que es posible enviar mensajes sintácticamente distintos a objetos de tipos iguales','F',0,6,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (24,'Es la capacidad que tienen los objetos de una clase de responder a distintos mensajes','F',0,6,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (25,'Que cualquier modificacion que realicemos solo afectara a una copia de la variable que pasemos','V',50,7,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (26,'Nos indica que nuestro metodo recibirá una copia de la variable que pasemos','V',50,7,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (27,'Que además de pasar el valor a la función, se pasa la referencia a la variable original','F',0,7,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (28,'Si hacemos algun cambio en el parametro de nuestro metodo, esto equivaldria a estar actuando directamente sobre la variable original','F',0,7,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (29,'Una clase se extiende','V',50,8,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (30,'Una clases contiene comportamiento establecido','V',50,8,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (31,'Una clase se implementa','F',0,8,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (32,'Una clase no tiene ningún comportamiento en su interior solo descripción','F',0,8,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (33,'Error: Indican problemas muy graves que suelen ser no recuperables','V',50,9,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (34,'Exception: no definitivas pero se detectan fuera del tiempo de ejecucion','V',50,9,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (35,'RutineError: son errores que se dan durante la ejecucion del programa','F',0,9,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (36,'Todas las anteriores','F',0,9,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (37,'Poder acceder o invocar a un método sin la necesidad de tener que instanciar un objeto de la clase','V',50,10,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (38,'Poder acceder o invocar a bloque de código sin la necesidad de tener que instanciar un objeto de la clase','V',50,10,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (39,'Acceder o invocar a una variable creando un objeto','F',0,10,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (40,'Ninguna de las anteriores','F',0,10,1)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (41,'Composición secuencial','V',50,11,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (42,'Estructura recursiva','V',50,11,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (43,'Composición incondicional','F',0,11,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (44,'Ninguna de las anteriores','F',0,11,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (45,'Bien definido','V',50,12,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (46,'Entrada','V',50,12,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (47,'Infinito','F',0,12,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (48,'Todas las anteriores','F',0,12,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (49,'Simples','V',50,13,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (50,'Compuestas','V',50,13,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (51,'Flexibles','F',0,13,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (52,'Complejas','F',0,13,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (53,'Diagrama de Flujo','V',50,14,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (54,'Seudocódigo','V',50,14,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (55,'Diagrama de Venn','F',0,14,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (56,'Todas las anteriores','F',0,14,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (57,'Es una herramienta de desarrollo de pseudocódigo','V',50,15,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (58,'Es una herramienta para asistir a estudiantes en sus primeros pasos en programación','V',50,15,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (59,'Es un repositorio de código fuente','F',0,15,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (60,'Es una interfaz de Java','F',0,15,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (61,'Mientras','V',50,16,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (62,'Repetir','V',50,16,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (63,'Si','F',0,16,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (64,'Sino','F',0,16,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (65,'Unidimensionales: tiene una solo dimensión una fila y una columna ','V',50,17,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (66,'Bidimensionales: tablas o matrices','V',50,17,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (67,'Heterogeneas: permiten almacenar distintos datos','F',0,17,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (68,'Ninguna de las anteriores','F',0,17,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (69,'Los subprocesos pueden o no tener retorno','V',50,18,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (70,'Siempre que usemos parámetros estos deben de ser del mismo tipo datos','V',50,18,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (71,'Los subprocesos siempre deben tener retorno','F',0,18,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (72,'Siempre que usemos parámetros estos deben de ser de distinto tipo datos','F',0,18,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (73,'Respecto a los subprocesos podemos afirmar que:','V',50,19,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (74,'Nos proporcionan un resultado a partir de que se cumpla o no una cierta condición','V',50,19,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (74,'Producen un resultado booleano','F',0,19,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (76,'Nos proporcionan un resultado númerico único','F',0,19,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (77,'Mayor que','V',50,20,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (78,'Distinto que','V',50,20,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (79,'Potenciación','F',0,20,2)
INTO alternativa (idalternativa,descripcion,valorlogico,valorporcentual,pregunta_idpregunta,pregunta_idtest) VALUES (80,'Módulo','F',0,20,2)
```
