**SQL**
```
create table t_employee
(
    id  int PRIMARY KEY,
    department_id int NOT NULL,
    name VARCHAR(100) NOT NULL,
    salary int NOT NULL
);

insert into t_employee VALUES
(1, 1, 'Сергей', 190000),
(2, 1, 'Владимир', 160000),
(3, 2, 'Артем', 180000),
(4, 2, 'Павел', 180000),
(5, 2, 'Михаил', 130000);

-- ВАШ ЗАПРОС --
-- Список сотрудников, получающих максимальную заработную плату в своем отделе --
```



**C#**
