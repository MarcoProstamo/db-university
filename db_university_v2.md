## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT students.*, degrees.name degree_name
FROM students
INNER JOIN degrees
ON students.degree_id = degrees.id
WHERE degrees.name = "Corso di Laurea in Economia";
```

## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```sql
SELECT  dp.id dp_id, dp.name dp_name , dg.id dg_id, dg.name dg_name
FROM departments dp
INNER JOIN degrees dg
ON dp.id = dg.department_id
WHERE dg.level = "Magistrale" AND dp.name = "Dipartimento di Neuroscienze";
```

## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
SELECT c.id c_id, c.name c_name, c.description c_description, c.period c_period, c.year c_year, c.cfu c_cfu, c.website c_website, t.id t_id, t.name t_name, t.surname t_surname
FROM courses c
INNER JOIN teachers t
ON c.id = t.id
where t.id = "44";
```

## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```sql
SELECT s.id s_id, s.name s_name, s.surname s_surname, s.registration_number s_registration_number, dg.id dg_id, dg.department_id dg_department_id, dg.name dg_name, dg.level dg_level, dg.address dg_address, dg.email dg_email, dg.website dg_website, dp.id dp_id, dp.name dp_name, dp.address dp_address, dp.phone dp_phone, dp.email dp_email, dp.website dp_website, dp.head_of_department dp_head_of_department
FROM students s
INNER JOIN degrees dg
ON s.degree_id = dg.id
INNER JOIN departments dp
ON dg.department_id = dp.id
ORDER BY s.surname, s.name
```

## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
SELECT d.id d_id, d.name d_name, c.id c_id, c.name c_name, t.id t_id, t.name t_name, t.surname t_surname
FROM degrees d
INNER JOIN courses c
ON d.id = c.degree_id
INNER JOIN teachers t
ON c.id = t.id;
```

## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```sql
SELECT DISTINCT t.*
FROM departments dp
INNER JOIN degrees dg
ON dp.id = dg.department_id
INNER JOIN courses c
ON dg.id = c.degree_id
INNER JOIN course_teacher ct
ON c.id = ct.course_id
INNER JOIN teachers t
ON ct.teacher_id = t.id
WHERE dp.id = "5"
```

## BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

```sql
SELECT
    s.id as s_id,
    s.name as s_name,
    s.surname as s_surname,
    e.course_id c_id,
    COUNT(es.exam_id) as attempts,
    MAX(es.vote) as max_vote
FROM
    students s
INNER JOIN
    exam_student es ON s.id = es.student_id
INNER JOIN
    exams e ON es.exam_id = e.id
WHERE
    es.vote >= 18
GROUP BY
    s.id, s.name, s.surname, e.course_id
ORDER BY
    s.id, e.course_id;

```
