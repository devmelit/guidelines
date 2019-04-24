## Melit Guidelines

## JIRA:
Recibimos una respuesta de un cliente, comentamos el ticket de esta forma:
EMAIL  CLIENTE: [[ASUNTO EMAIL]]
[[MENSAJE]] 
[[ADJUNTOS]]


Usar opción de “quotes” para diferenciar lo que copiamos del cliente de lo que escribimos nosotros.

Crear ramas con el número de ticket (ver apartado GIT)

Cuando se comenta y se cambia el estado de un ticket, comentar el código #done, #test-env, etc…
Añadir a los commit en la parte de #comment “#code“, para diferenciar un comentario escrito de los comentarios de los commit.

## GIT:
Nombre de las branch:
a)	Ticket JIRA: branch original “/” ticket jira “-“ breve descripción. 
Ej: develop/MESP-15-crear-pdf-oferta

b)	Usaremos un esquema GIT Flow adaptado, es decir, si hay un fallo en la branch master se solucionará en la branch hotfix/MESP-74-fix-null-documentos, al terminar se solicita pull request a master y develop

Usar los Smart commits para realizar acciones en los tickets de JIRA. Info: https://confluence.atlassian.com/fisheye/using-smart-commits-960155400.html
Syntax
<ignored text> ISSUE_KEY <ignored text> #comment <comment_string>
Example
JRA-34 #comment corrected indent issue

Registrar el tiempo en cada commit
Syntax
<ignored text> ISSUE_KEY <ignored text> #time <value>w <value>d <value>h <value>m <comment_string>
Example
JRA-34 #time 1w 2d 4h 30m Total work logged


## CODIGO:

Evitar java.lang.NullPointerException en booleanos.


## BASE DE DATOS:
No se eliminan o renombran columnas o tablas con liquibase.
Evitar incluir el schema en las queries.
Evitar SQL: AFTER `last_modify`
Añadir a los changelog.sql de los proyectos el comentario con la fecha y el ticket. Ej.:
#2019-03-15 MITA-101
ALTER TABLE `mi_tabla` 
ADD COLUMN `mi_column` INT(11) NULL;

Cuando se generan nuevas columnas a tablas que ya contienen datos, siempre intentar crear una query SQL para rellenarla. Excepto si la nueva columna no lo requiere. 
