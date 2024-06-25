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

```
create table Employee
(
ID int PRIMARY KEY,
DEPARTMENT_ID int NOT NULL,
CHIEF_ID int REFERENCES Employee(ID), 
NAME VARCHAR(100) NOT NULL,
SALARY int NOT NULL
)


--department "A"
insert into Employee values (1, 1, 1, '[A] Boss', 1000); 
insert into Employee values (2, 1, 1, '[A] Ivan', 500); --department "B"
insert into Employee values (3, 2, 3, '[B] Boss', 600);
insert into Employee values (4, 2, 3, '[B] Andrey', 700);

with cte as
(
select max(salary) as salary, department_id as department_id
from employee
group by department_id
)

select e.name from employee e
join cte c on e.salary = c.salary and e.department_id = c.department_id
```

**C#**
```
class Program
{
    private static string message;

    static void Main()
    {
        SaySomething();
        Console.WriteLine(message); // будет выводиться или null или Hello world! , так как SaySomething будет выполняться в другом потоке и Console.WriteLine не будет ждать окончания вычисления. Если использовать var message = SaySomething(); - то будет аналогичная ситуация
    }

    static async Task<string> SaySomething()
    {
        await Task.Delay(5);
        message = "Hello world!";
        return "Something";
    }
}
```

```
class Program
{
    static void Main()
    {
        var list = new List<int>();
         
        var i = 10;
          
        var query = list.Where(x => x == i).Where(x => x < 20);
 
        list.Add(10);
        list.Add(15);
        list.Add(20);

        i = 15;
  
        var result=query.ToList();

        list.Clear();

        Console.WriteLine(result.Count); // 1
        Console.WriteLine(result.FirstOrDefault()); // 15. Причина: при i=15 изменится Query и изменения применятся при материализации
    }
}
```

```
private readonly int _intLockObj = 1; 
private readonly string _strLockObj = "1";
private readonly object _objLockObj = new object();

//какую из вышеперечисленных переменных можно использовать в конструкции lock//
lock(...)
{
	//нельзя использовать не ссылочные типы в lock, int - нельзя, string, object - можно
}
```

```
class Person
{
    public int Age;
}

var persons = Enumerable.Range(0, 3).Select(itr=> new Person{Age = itr});

foreach(var itr in persons)
{
	itr.Age++;
}


foreach(var itr in persons)
{
	Console.WriteLine(itr.Age); //будет 0 1 2. Причина: внутри первого foreach каждый элемент материализуется, значение меняется, но вне первого foreach изменения не сохранятся
}
```

```
public class MyClass
{
    public int Num { get; set; }
}
public struct MyStruct
{
    public int Num { get; set; }
}
public class Program
{
    static void Main()
    {
        var myClassObj = new MyClass(); 
        var myStructObj = new MyStruct();

        Console.WriteLine(myClassObj.Num);
        Console.WriteLine(myStructObj.Num);

        MethodA(myClassObj.Num);
        MethodB(myStructObj);

        Console.WriteLine(myClassObj.Num);
        Console.WriteLine(myStructObj.Num);

        MethodC(myClassObj);

        Console.WriteLine(myClassObj.Num);
        Console.WriteLine(myStructObj.Num);

        MethodD(myClassObj);

        Console.WriteLine(myClassObj.Num);
        Console.WriteLine(myStructObj.Num);
    }
    private static void MethodA(int num)
    {
        num = num + 1;
    }
    private static void MethodB(MyStruct myStruct)
    {
        myStruct.Num += 1;
    }
    private static void MethodC(MyClass myClass)
    {
        myClass.Num += 1;
    }

    private static void MethodD(MyClass myClass)
    {
        myClass = new MyClass
        {
            Num = myClass.Num * 2,
        };
    }
}
```

```
public class Program
{
    static void Main()
    {
        var s1 = "Text";
        var s2 = s1;
        var s3 = "Text";
        Console.WriteLine(s1 == s3);
        s2 += " Changed";
        ChangeString(s1);
        Console.WriteLine(s1 == s2);
    }
    static void ChangeString(string str)
    {
        str += " Changed";
    }
}
```
