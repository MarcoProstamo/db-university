## Selezionare tutti gli studenti nati nel 1990 (160)

```sql
SELECT *
FROM db_university.students
WHERE date_of_birth LIKE "1990-%-%";
```

## Selezionare tutti i corsi che valgono più di 10 crediti (479)

```sql
SELECT *
FROM db_university.courses
WHERE cfu > 10;
```

## Selezionare tutti gli studenti che hanno più di 30 anni

```sql
SELECT *
FROM db_university.students
WHERE YEAR(CURDATE()) - YEAR(date_of_birth) > 30;
```

## Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

```sql
SELECT *
FROM db_university.courses
WHERE period = "I semestre" AND year = "1";
```

## Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

```sql
SELECT *
FROM db_university.exams
WHERE date = "2020-06-20" AND hour > "13:59:59";
```

## Selezionare tutti i corsi di laurea magistrale (38)

```sql
SELECT *
FROM db_university.degrees
WHERE level = "magistrale";
```

## Da quanti dipartimenti è composta l'università? (12)

```sql
SELECT COUNT(*)
FROM db_university.departments;
```

## Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

```sql
SELECT COUNT(*)
FROM db_university.teachers
WHERE phone IS NULL;
```

## Inserire nella tabella degli studenti un nuovo record con i propri dati (per il campo degree_id, inserire un valore casuale)

```sql
INSERT INTO `db_university`.`students` (`degree_id`, `name`, `surname`, `date_of_birth`, `fiscal_code`, `enrolment_date`, `registration_number`, `email`) VALUES ('68', 'Marco', 'Prostamo', '1010-12-12', '12312QWQWE2334', '2022-22-22', '696969', 'clo23wn@gmail.com');

```

## Cambiare il numero dell’ufficio del professor Pietro Rizzo in 126

```sql
UPDATE db_university.teachers
SET office_number = "126"
WHERE id = "58";
```

## Eliminare dalla tabella studenti il record creato precedentemente al punto 9

```sql
DELETE FROM `db_university`.`students`
WHERE (`id` = '1001');
```

## Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT COUNT(id), YEAR(enrolment_date) AS enrolment_year
FROM db_university.students
GROUP BY YEAR(enrolment_date);
```

## Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT COUNT(id), office_address
FROM db_university.teachers
GROUP BY office_address;
```

## Calcolare la media dei voti di ogni appello d'esame

```sql
SELECT exam_id, AVG(vote) AS average_vote
FROM db_university.exam_student
GROUP BY exam_id;
```

## Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql
DELETE FROM `db_university`.`students`
WHERE (`id` = '1001');
```
