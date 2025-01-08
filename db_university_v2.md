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
SELECT *
FROM db_university.students
WHERE date_of_birth LIKE "1990-%-%";
```

## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
SELECT *
FROM db_university.students
WHERE date_of_birth LIKE "1990-%-%";
```

## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```sql
SELECT *
FROM db_university.students
WHERE date_of_birth LIKE "1990-%-%";
```

## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
SELECT *
FROM db_university.students
WHERE date_of_birth LIKE "1990-%-%";
```

## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```sql
SELECT *
FROM db_university.students
WHERE date_of_birth LIKE "1990-%-%";
```

## BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.
