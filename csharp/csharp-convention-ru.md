# C# Conventions

## Naming

| Идентификатор           | Нотация            | Plural | Часть речи   | Аббреитура | Char Mask  |
| :---------------------- | :----------------- | :----- | :----------- | :--------- | :--------- |
| Namespace name          | PascalCase         | Yes    | N            | No         | [A-z][0-9] |
| Class name              | PascalCase         | No     | N            | No         | [A-z][0-9] |
| Abstract class name     | AbstractPascalCase | No     | N            | No         | [A-z][0-9] |
| Constructor name        | PascalCase         | No     | N            | No         | [A-z][0-9] |
| Interface name          | IPascalCase        | No     | N or Adj     | No         | [A-z][0-9] |
| Method name             | PascalCase         | Yes    | V or V + Any | No         | [A-z][0-9] |
| Method arguments        | camelCase          | Yes    | N            | Yes        | [A-z][0-9] |
| Local variables         | camelCase          | Yes    | N            | Yes        | [A-z][0-9] |
| Constants name          | PascalCase         | No     | N            | No         | [A-z][0-9] |
| Public    field name    | PascalCase         | Yes    | N            | Yes        | [A-z][0-9] |
| Protected field name    | PascalCase         | Yes    | N            | Yes        | [A-z][0-9] |
| Private   field name    | _camelCase         | Yes    | N            | Yes        | [A-z][0-9] |
| Public    property name | PascalCase         | Yes    | N            | Yes        | [A-z][0-9] |
| Protected property name | PascalCase         | Yes    | N            | Yes        | [A-z][0-9] |
| Private   property name | _camelCase         | Yes    | N            | Yes        | [A-z][0-9] |
| Delegate name           | PascalCase         | No     | N            | Yes        | [A-z]      |
| Enum type name          | PascalCase         | Yes    | N            | No         | [A-z]      |

#### 1. Только английские идентификаторы разрешены. Коментарии могут быть написны на любом языке

```csharp
// Correct
public int Counter;

// Avoid
public int Счетчик;
```

#### 2. Используйте осмысленные имена

```csharp
// Correct
public void ClearPage() { }

// Avoid
public void DoThing() { }
```

#### 3. Не используйте транслитерацию. Исключение: имена собственные

```csharp
// Correct
public int ItemCounter;

// Exception
public Onegin Eugeni;

// Avoid
public int ShetchickPredmetov;
```

#### 4. Не пишите капсом

``` csharp
// Correct
public int Count;

// Avoid
public int COUNT;
```

#### 5. Не используйте сокращения. Исключение: общепринятые сокращения, такие как Id, Xml, Ftp, Uri, Ar, Vr и т.д

```csharp
// Correct
UserGroup userGroup;
Assignment employeeAssignment;

// Avoid
UserGroup usrGrp;
Assignment empAssignment;

// Exeptions
public class ArContoller { }
public int UserId;
protected XmlHelper XmlHelper;
```

#### 6. Не используйте подчеркивания в иных случаях, кроме как в качестве префиксов для приватных полей и свойств

```csharp
// Correct
public DateTime ClientAppointment;
protected TimeSpan timeLeft;
private DateTime _registrationDate;

// Avoid
public DateTime client_Appointment;
public TimeSpan time_Left; 
```

#### 7. Добавляйте префикс "Abstract" для абстрактных классов

```csharp
// Correct
public abstract class AbstractShape { }
public abstract class AbstractShapeCollection { }
public abstract class AbstractGroup { }

// Avoid
public abstract class AShape { }
public abstract class ShapeCollection { }
public abstract class Group { }
```

#### 8. К названиям интерфейсов добавляйте префикс "I"

```csharp
// Correct
public interface IShape { }
public interface IShapeCollection { }
public interface IGroupable { }

// Avoid
public interface Shape { }
public interface ShapeCollection { }
public interface Groupable { }
```

#### 9. Используйте суффикс EventArgs при создании новых классов, содержащих информацию о событии

```csharp
// Correct
public class BarcodeReadEventArgs : System.EventArgs { }

// Avoid
public class BarcodeReadArgs : System.EventArgs { }
```

#### 10. Называйте обработчики событий (делегаты, используемые как типы событий) с суффиксом "EventHandler" как показано в примере

```csharp
public delegate void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e);
```

#### 11. Не используйте имена параметров методов (или конструкторов), отличающиеся лишь в регистре

```csharp
// Correct
private void MyFunction(string oneName, string otherName)
{
    //...
}

// Avoid
private void MyFunction(string name, string Name)
{
    //...
}
```

#### 12. Используйте суффикс Exception при создании классов, содержащих информацию об Exeption'ах (Исключениях)

```csharp
// Correct
public class BarcodeReadException : System.Exception { }

// Avoid
public class BarcodeReadError : System.Exception { }
```

#### 13. Используйте префикс Any, Is, Have или схожие по смыслу слова для идентификаторов типа boolean

```csharp
// Correct
public static bool IsNullOrEmpty(string value) => value == null || value.Length == 0;

// Avoid
public static bool NullOrEmpty(string value) => value == null || value.Length == 0;
```

#### 14. Используйте имена в единстенном числе для названия Enum'ов. Искключение: bit field enum'ы

```csharp
// Correct
public enum Color
{
    Red,
    Green,
    Blue,
    Yellow,
    Magenta,
    Cyan
} 

// Exception
[Flags]
public enum Dockings
{
    None = 0,
    Top = 1,
    Right = 2, 
    Bottom = 4,
    Left = 8
}
```

#### 15. Не используйте суффиксы "Flag" или "Flags" в названии Enum'ов

```csharp
// Correct
[Flags]
public enum Dockings
{
    None = 0,
    Top = 1,
    Right = 2, 
    Bottom = 4,
    Left = 8
}

// Avoid
[Flags]
public enum DockingsFlags
{
    None = 0,
    Top = 1,
    Right = 2, 
    Bottom = 4,
    Left = 8
}
```

#### 16. Не используйте суффиксы такие как "Enum" названии Enum'ов

```csharp
// Correct
public enum Coin
{
    Penny,
    Nickel,
    Dime,
    Quarter,
    Dollar
}

// Avoid
public enum CoinEnum
{
    Penny,
    Nickel,
    Dime,
    Quarter,
    Dollar
}
```

## Модификаторы доступа

#### 1.Явно объявляйте модификаторы доступа

```csharp
// Correct
public class Cat
{
    private Color color;
    
    ...

    public void Meow()
    {
        ...
    }
}

// Avoid
class Cat
{
    Color color;
    
    // ...

    public void Meow()
    {
        // ...
    }
}
```

## Type identifier usage

#### 1. Используйте предопределенные название типов (псевдонимы c#) такие  как `int`, `float`, `string` вместо имен из .NET Framework'a такие как `Int32`, `Single`, `String'

```csharp
// Correct
string firstName;
int lastIndex;
bool isSaved;
var commaSeparatedNames = string.Join(", ", names);
var index = int.Parse(input);

// Avoid
String firstName;
Int32 lastIndex;
Boolean isSaved;
string commaSeparatedNames = String.Join(", ", names);
int index = Int32.Parse(input);
```

#### 2. Объявляйте тип локальной переменной неявно (`var`). Исключение: объявляйте тип явно, если в выражении нет идентификатора типа

```csharp
// Correct
var stream = File.Create(path);
var customers = new Dictionary();
string timeSheet;
bool isCompleted;

// Avoid
int index = int.Parse("100");
```

#### 3. Пропускайте Generic (шаблонные) идентификаторы типов там, где это возможно

```csharp
// Correct
List<int>() l;
l.Select(...);

// Avoid
List<int>() l;
l.Select<int>(...);
```

#### 4. Используйте максимально обобщенный тип, если он не противоречит вашей логике

```csharp
// Correct
public class AbstractModel
{
    public abstract void Save()
}

public class UserModel : AbstractModel 
{
    // Model implementation
}

public class ModelWrapper
{
    private AbstractModel _wrappedModel;

    public ModelWrapper(AbstractModel modelToWrap)
    {
        _wrappedModel = modelToWrap
    }

    // ...
}

public class OnlyUserModelWrapper
{
    private UserModel _wrappedModel;

    public OnlyUserModelWrapper(UserModel modelToWrap)
    {
        _wrappedModel = modelToWrap
    }

    // ...
}

// Avoid
public class AbstractModel
{
    public abstract void Save()
}

public class UserModel : AbstractModel 
{
    // Model implementation
}

public class ModelWrapper
{
    private UserModel _wrappedModel;

    public ModelWrapper(UserModel modelToWrap)
    {
        _wrappedModel = modelToWrap
    }

    // ...
}

public class OnlyUserModelWrapper
{
    private AbstractModel _wrappedModel;

    public OnlyUserModelWrapper(AbstractModel modelToWrap)
    {
        _wrappedModel = modelToWrap
    }

    // ...
}

```

## Структура проекта

#### 1. Называйте исходные файлы также как и их главные классы. Исключение: имена файлов, содержащих partial-классы, которые отражают их суть или происхождение. Например disgner, generated и т. д

```csharp
// Находится в Task.cs
public partial class Task { }
// Находится в Task.generated.cs
public partial class Task { }
```

#### 2. Помещайте классы(или enum'ы, структуры или интерфейсы) в отдельные файлы, если они относятся не только к основному классу(или enum'у, стурктуре или интефейсу) файла или имеют длину более 5-10 строк

#### 3. Организуйте структуру проекта так, чтобы она соответствовала именам и структуре namespace'ов (пространств имен)

```csharp
//Находится в Company/Technology/Feature/Subnamespace/
namespace Company.Technology.Feature.Subnamespace{ }

// Находится в Company/Product/Module/SubModule/
namespace Company.Product.Module.SubModule { }

// Находится в Product/Module/Component/
namespace Product.Module.Component { }

// Находится в Product/Layer/Module/Group/
namespace Product.Layer.Module.Group { }
```

## Форматирование

### Новые строки

#### 1. Помещайте новую строку чтобы разделить код по смыслу в разделы длиной в 2-4 строки

#### 2. Оставляйте одну строку между классами, пространствами имен, интефейсами или описанием методов

```csharp
// Correct
namespace Product
{
    public abstract class AbstractFeature { }

    public class Feature : AbstractFeature
    {
        public Settings Settings;

        public int CalculateSomething()
        {
            // ...
        }

        public bool IsAvailable()
        {
            // ...
        }
    }
}

public class Programm
{
    public static void Main(string[] args)
    {
        // ...
    }
}

// Avoid
namespace Product
{
    public abstract class AbstractFeature { }
    public class Feature : AbstractFeature
    {
        public Settings Settings;
        public int CalculateSomething()
        {
            // ...
        }
        public bool IsAvailable()
        {
            // ...
        }
    }
}
public class Programm
{
    public static void Main(string[] args)
    {
        // ...
    }
}
```

### Отступы

#### 1. Используйте отступы для каждого блока

#### 2. Используйте пробелы вместо табуляции

#### 3. Используйте одинаковое количество пробелов на каждый уровень вложенности (обычно 4 пробела)

### Фигурные скобки

#### 1. Выравнивайте фигурные скобки по вертикали

```csharp
// Верно
public class Program
{
    public static void Main(string[] args)
    {
        //...
    }
}

// Avoid
public class Program {
    public static void Main(string[] args) {
        //...
    }
}
```

#### 2. Помещайте пустой блок фигурных скобок на той же линии и оставляйте пробел до скобок и внутри них

```csharp
// Correct
public void AddUser() { }

// Avoid
public void AddUser() {}

public void AddUser(){ }

public void AddUser(){}

public void AddUser() 
{

}
```

### Комментарии

#### 1. Оставляйте комментарии перед той строкой, к которой адресован комментарий. Оставляйте пустюу строку между комментарием и предыдщим выражением

```csharp
// Correct:
public int Zero = 0;

// One equals 0 + 1
public int One = Zero + 1;

// Avoid:
public int Zero = 0;
// One equals 0 + 1
public int One = Zero + 1;

public int Zero = 0;
public int One = Zero + 1; // One equals 0 + 1
```

#### 2. Начинайте новый комментарий с пробела

```csharp
// Correct:
// Example of correct comment

// Avoid:
//Example of incorrect comment
```

### Аттрибуты

#### 1. Размещайте каждый аттрибут на новой строке перед идентификатором

```csharp
// Correct
[AttributeA]
[AttributeB]
public int Value;

// Avoid
[AttributeA] [AttributeB]
public int Value;

[AttributeA] [AttributeB] public int Value;
```

#### 2. Оставляйте пустую линию между предыдущим выражением и аттрибутом

```csharp
// Correct
public string Name;

[AttributeA]
[AttributeB]
public int Value;

// Avoid
public string Name;
[AttributeA]
[AttributeB]
public int Value;
```

## Главное

#### 1. Не указыайте явный тип enum'ов или значений enum'ов (кроме bit fields enum'ов)

```csharp
// Correct
public enum Direction
{
    North,
    East,
    South,
    West
}

// Avoid
public enum Direction : long
{
    North = 1,
    East = 2,
    South = 3,
    West = 4
}
```

### Код должен быть максимально коротким и декларативным

#### 1. Используйте expression body (тело-выражение), если блок содержит однострочное выржение

```csharp
// Correct
public float ToKelvin(float celsius) => celsius - 273; 

// Avoid
public float ToKelvin(float celsius)
{
    return elsius - 273; 
}
```

#### 2. Предпочитайте `foreach` вместо `for`

#### 3. Предпочитайте `LINQ` вместо `foreach`

#### 4. Используйте только синтаксис методов `LINQ`

### Воспользуйтесь преимуществами особенностей `C#` и сделайте свой код понятным

#### 1. Предпочитайте не использовать приватные свойства

#### 2. Предпочитайте использовать свойства, а не методы `Set` и `Get`

#### 3. Не используйте тернарный оператор более одного раза в выражении

<!-- ## Example

```csharp
namespace Animals
{
    public interface IMakingSounds
    {
        public void MakeSound();
    }

    public interface IMovementCapable
    {
        public void MoveTo(float x, float y);
    }
}

namespace Animals.Dogs
{
    public abstract class AbstractDog : IMakingSounds, IMovementCapable
    {
        public float TailLength 
        {
            get { return _tailLength; }
            set 
            {
                _tailLength = value;
                ChangeTailLength(_tailLength);
            }
        }

        private float _tailLength;

        // barks
        public abstract void MakeSound();

        // goes to point
        public abstract void MoveTo(float x, float y);

        // tail length-changing method
        protected abstract void ChangeTailLength(float tailLength);
    }

    // AbstractDog implementation
    public Dog : AbstractDog { }
}
``` -->

## Сокращение частей речи

| Аббреввиатура | Часть речи                                                  |
| :------------ | :---------------------------------------------------------- |
| N             | Существительное                                             |
| V             | Глагол                                                      |
| Adj           | Прилоагательное                                             |
| Adv           | Наречие                                                     |
| Any           | Существительное или Глагол, или Прилагательное, или Наречие |

Этот документ основан на [другом соглашении об именовании](https://github.com/ktaranov/naming-convention/blob/master/C%23%20Coding%20Standards%20and%20Naming%20Conventions.md).
