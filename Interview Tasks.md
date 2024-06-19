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
```
class Program
{
    private static string message;

    static void Main()
    {
        SaySomething();
        Console.WriteLine(message); // будет выводиться или null или Hello world! так как SaySomething будет выполняться в другом потоке и Console.WriteLine не будет ждать окончания вычисления
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
....
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
