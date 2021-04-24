# sql-query-practice


### Round 1

Connect to the LikeyPix database in Beekeeper, and answer the following questions:

1. Write a query that returns all Users

```
Paste your query below:
SELECT * 
FROM users;

```

2. Write a query that returns all Posts

```
Paste your query below:
SELECT *
FROM posts;


```

3. Write a query that returns the count of all Posts

```
Paste your query below:
SELECT COUNT(*) FROM posts;

```

4. Which Post had the most Comments?

Answer: post 1

5. Write a query that returns the Post which had the least Comments

```
Paste your query below:
SELECT count(*) as coms, post_id FROM comments
	GROUP BY post_id
    ORDER BY coms ASC
    LIMIT 1;
	

```

6. Which User has the most Comments?

Answer: Alice

7. Write a single query to get all of the Posts and their Comments (You'll see the same Post repeated in the results)

```
Paste your query below:
Select * from posts
	join comments
    on posts.id = comments.post_id
ORDER BY posts.id;

```

### Round 2

- Disconnect from the `likeypix` database connection
- Connect to the `classroom` database connection

1. Write a query to get the first name, last name, and github URL for every Student in the `students` table

```
Paste your query below:
SELECT first_name, last_name, github_url
FROM students;


```

2. Write a query to get a list of Students who do not have a LinkedIn URL

```
Paste your query below:
SELECT first_name, last_name, linkedin_url
FROM students
WHERE linkedin_url = '';

```

3. Write a query to get a list of Teachers with the "Teaching Assistant" Role

```
Paste your query below:
SELECT teachers.first_name, teachers.last_name FROM teachers
	JOIN teacher_roles
    ON teachers.teacher_role_id = teacher_roles.id
WHERE teacher_roles.slug = 'teaching-assistant';

```

4. Write a query to get a list of Students, and their Class' `slug`

```
Paste your query below:
select students.id, students.first_name, students.last_name, classes.slug
from students
join classes
	on classes.id = students.class_id;

```

5. Write a query to get the length of every students First Name

```
Paste your query below:
select first_name, last_name, LENGTH(first_name) from students;
```

6. What is the ID of the Student with the longest Last Name?

Answer: 8

7. Write a query to get a list of Students in reverse alphabetical order of First Name

```
Paste your query below:
select first_name, last_name, id  from students
order by first_name desc;

```

### Round 3

- Disconnect from the `classroom` database connection
- Connect to the `food` database connection

This Round is going to require you to get curious about your surroundings. At some point in your path as a developer, you will work on a project that already has an existing database. That database may be quite old, or have been built on a different set of standards.

These questions will be focused on exploring an unknown database that does not follow the standards we have established in class. See if you can work out answers to the following questions:


1. What table contains information about individual food items? 

Answer: food_des

2. Using the table from the previous answer as your starting point - what table do you think contains Food Group information about individual foods?

Answer: fd_group

3. Write a query to get the name of a food, and its corresponding food group name 

```
Paste your query below:
select food_des.comname, food_des.long_desc, fd_group.fddrp_desc  from food_des
	join fd_group
    on food_des.fdgrp_cd = fd_group.fdgrp_cd;


```

4. Identify the table that has information about data sources

Answer: data_src

5. Using the table from your previous answer, write a query that will get the oldest data source

```
Paste your query below:
select * from data_src
order by year
limit 1;

```

6. How many foods contain "Egg" in their description?

Answer: 54

select count(*) from food_des
where long_desc like '%Egg%';

7. Write a query that will return a count of foods in each food group

```
Paste your query below:
select fd_group.fddrp_desc, count(fd_group.fddrp_desc) num from food_des
	join fd_group
    on food_des.fdgrp_cd = fd_group.fdgrp_cd
    group by fd_group.fddrp_desc;

```
