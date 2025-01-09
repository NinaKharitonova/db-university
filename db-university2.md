1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT
	`students`.`id`,
    `students`.`degree_id`,
    `students`.`name`  AS `student_name`,
    `students`.`registration_number`,
    `degrees`.`name` AS `degrees_name`
FROM `students`
JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia'
;
```

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
   Neuroscienze

```sql
 SELECT
`departments`.`name` AS `departments_name`,
 `degrees`. `name` AS `degrees_name`,
  `degrees`. `level`
FROM `departments`
INNER JOIN `degrees`
ON `departments`.`id` = `degrees`.`department_id`
WHERE `departments`.`name` = 'Neuroscienze'
AND `degrees`.`level` = 'magistrale';
```

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
SELECT
    `courses`.`name` AS `course_name`
FROM `courses`
JOIN `course_teacher`
    ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers`
    ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `teachers`.`id` = 44;
```

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
   sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
   nome

```sql
SELECT
    `students`.`name` AS `student_name`,
    `students`.`surname` AS `student_surname`,
    `degrees`.`name` AS `degree_name`,
    `departments`.`name` AS `department_name`
FROM `students`
JOIN `degrees`
    ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments`
    ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname`, `students`.`name`;
```

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
SELECT
    `departments`.`name` AS `department_name`,
    `degrees`.`name` AS `degree_name`,
    `courses`.`name` AS `course_name`,
    `teachers`.`name` AS `teacher_name`,
    `teachers`.`surname` AS `teacher_surname`
FROM `departments`
JOIN `degrees`
    ON `departments`.`id` = `degrees`.`department_id`
JOIN `courses`
    ON `degrees`.`id` = `courses`.`degree_id`
JOIN `course_teacher`
    ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers`
    ON `course_teacher`.`teacher_id` = `teachers`.`id`
ORDER BY `departments`.`name`, `degrees`.`name`, `courses`.`name`;
```

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
   Matematica (54)

```sql
SELECT
    `teachers`.`name` AS `teachers_name`,
    `teachers`.`surname` AS `teachers_surname`
FROM `teachers`
JOIN `courses`
    ON `teachers`.`id` = `courses`.`id`
JOIN `degrees`
    ON `courses`.`degree_id` = `degrees`.`id`
JOIN `departments`
    ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Matematica';
```

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
   per ogni esame, stampando anche il voto massimo. Successivamente,
   filtrare i tentativi con voto minimo 18

```sql

```
