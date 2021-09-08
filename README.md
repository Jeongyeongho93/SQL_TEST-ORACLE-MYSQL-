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


























