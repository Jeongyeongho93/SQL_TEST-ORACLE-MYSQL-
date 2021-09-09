# SQL_TEST-ORACLE-MYSQL-

Requirement explanation
Find that these Neutered animals are given after comes in the center earlier.

<SELECT animal_outs.animal_id, animal_outs.animal_type, animal_outs.name
FROM animal_outs left join animal_ins
ON animal_outs.animal_id = animal_ins.animal_id
WHERE animal_outs.sex_upon_outcome IN ('Spayed Female', 'Neutered Male')
AND animal_outs.datetime < animal_ins.datetime
ORDER BY animal_outs.animal_id ASC>





Requirement explanation
Find that these Neutered animals are given after comes in the center.

-Oracle
SELECT animal_outs.animal_id, animal_outs.animal_type, animal_outs.name
FROM animal_outs left join animal_ins
ON animal_outs.animal_id = animal_ins.animal_id
WHERE (animal_ins.sex_upon_intake = 'Intact Male' AND animal_outs.sex_upon_outcome = 'Neutered Male')
OR (animal_ins.sex_upon_intake = 'Intact Female' AND animal_outs.sex_upon_outcome = 'Spayed Female')
ORDER BY animal_outs.animal_id

-MySQL
SELECT animal_id, animal_type, name
FROM animal_outs
WHERE animal_id IN 
(SELECT animal_id FROM animal_ins 
 WHERE sex_upon_intake 
 IN ('Intact Female', 'Intact Male'))
AND sex_upon_outcome IN ('Spayed Female', 'Neutered Male')





Requirement explanation
Find that these Neutered Female animals are given after comes in the center.

-Oracle
SELECT animal_id, name, sex_upon_intake
FROM animal_ins
WHERE sex_upon_intake IN ('Spayed Female')
AND name IN ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty')
ORDER BY animal_id ASC

-MySQL
SELECT animal_id, name, sex_upon_intake
FROM animal_ins
WHERE sex_upon_intake IN ('Spayed Female')
AND name IN ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty')
ORDER BY animal_id ASC




Requirement explanation
Find the dog name that has contain a character with 'el'

-Oracle
SELECT animal_id, name
FROM animal_ins
WHERE REGEXP_LIKE(name,'el|eL|El|EL') 
AND animal_type='Dog'
ORDER BY name

-MySQL
SELECT animal_id, name
FROM animal_ins
WHERE REGEXP_LIKE(name,'el|eL|El|EL') 
AND animal_type='Dog'
ORDER BY name




Requirement explanation
Whether these are taken neutered action or not given by

-Oracle
SELECT animal_id, name, CASE WHEN REGEXP_LIKE(sex_upon_intake, 'Neutered|Spayed')
THEN 'O' 
ELSE 'X' 
END AS 중성화 
FROM animal_ins 
ORDER BY animal_id

-MySQL
SELECT animal_id, name, 
IF(INSTR(SEX_UPON_INTAKE, 'Intact') > 0 , 'X', 'O') AS 중성화
FROM animal_ins
ORDER BY animal_id










