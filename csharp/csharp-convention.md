# C# Convention

## Naming

| Object Name             | Notation           | Plural | Part of speech | Abbreviation | Char Mask  |
| :---------------------- | :----------------- | :----- | :------------- | :----------- | :--------- |
| Namespace name          | PascalCase         | Yes    | N              | No           | [A-z][0-9] |
| Class name              | PascalCase         | No     | N              | No           | [A-z][0-9] |
| Abstract class name     | AbstractPascalCase | No     | N              | No           | [A-z][0-9] |
| Constructor name        | PascalCase         | No     | N              | No           | [A-z][0-9] |
| Interface name          | IPascalCase        | No     | N or Adj       | No           | [A-z][0-9] |
| Method name             | PascalCase         | Yes    | V or V + Any   | No           | [A-z][0-9] |
| Method arguments        | camelCase          | Yes    | N              | Yes          | [A-z][0-9] |
| Local variables         | camelCase          | Yes    | N              | Yes          | [A-z][0-9] |
| Constants name          | PascalCase         | No     | N              | No           | [A-z][0-9] |
| Public    field name    | PascalCase         | Yes    | N              | Yes          | [A-z][0-9] |
| Protected field name    | PascalCase         | Yes    | N              | Yes          | [A-z][0-9] |
| Private   field name    | _camelCase         | Yes    | N              | Yes          | [A-z][0-9] |
| Public    property name | PascalCase         | Yes    | N              | Yes          | [A-z][0-9] |
| Protected property name | PascalCase         | Yes    | N              | Yes          | [A-z][0-9] |
| Private   property name | _camelCase         | Yes    | N              | Yes          | [A-z][0-9] |
| Delegate name           | PascalCase         | No     | N              | Yes          | [A-z]      |
| Enum type name          | PascalCase         | Yes    | N              | No           | [A-z]      |

#### 1. Only English identifiers are allowed. Comments may be written in language of choice

```csharp
// Correct
public int Counter;

// Avoid
public int Счетчик;
```

#### 2. Use meaningful names everywhere

```csharp
// Correct
public void ClearPage() { }

// Avoid
public void DoThing() { }
```

#### 3. Do not transliteration. Exception: proper names

```csharp
// Correct
public int ItemCounter;

// Exception
public Onegin Eugeni;

// Avoid
public int ShetchickPredmetov;
```

#### 4. Do not use caps

```csharp
// Correct
public int Count;

// Avoid
public int COUNT;
```

#### 5. Avoid using Abbreviations. Exceptions: abbreviations commonly used as names, such as Id, Xml, Ftp, Uri, Ar, Vr etc

```csharp
// Correct
public UserGroup UserGroup;
public Assignment EmployeeAssignment;

// Avoid
public UserGroup UsrGrp;
public Assignment EmpAssignment;

// Exeptions
public class ArContoller { }
public int UserId;
protected XmlHelper XmlHelper;
```

#### 6. Do not use Underscores in identifiers other than prefixes of private fields and properties

```csharp
// Correct
public DateTime ClientAppointment;
protected TimeSpan TimeLeft;
private DateTime _registrationDate;

// Avoid
public DateTime client_Appointment;
public TimeSpan time_Left; 
```

#### 7. Do prefix abstract classes nams with `Abstract`

```csharp
public abstract class AbstractShape { }
public abstract class AbstractShapeCollection { }
public abstract class AbstractGroup { }
```

#### 8. Do prefix interfaces names with the letter `I`

```csharp
public interface IShape { }
public interface IShapeCollection { }
public interface IGroupable { }
```

#### 9. Do use suffix EventArgs at creation of the new classes comprising the information on event

```csharp
// Correct
public class BarcodeReadEventArgs : System.EventArgs { }

// Avoid
public class BarcodeReadArgs : System.EventArgs { }
```

#### 10. Do name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example

```csharp
public delegate void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e);
```

#### 11. Do not create names of parameters in methods (or constructors) which differ only by the register

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

#### 12. Do use suffix Exception at creation of the new classes comprising the information on exception

```csharp
// Correct
public class BarcodeReadException : System.Exception { }

// Avoid
public class BarcodeReadError : System.Exception { }
```

#### 13. Do use prefix Any, Is, Have or similar keywords for boolean identifier

```csharp
// Correct
public static bool IsNullOrEmpty(string value) => value == null || value.Length == 0;

// Avoid
public static bool NullOrEmpty(string value) => value == null || value.Length == 0;
```

#### 14. Do use singular names for enums. Exception: bit field enums

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

#### 15. Do not use "Flag" or "Flags" suffixes in enum type names

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

#### 16. Do not use an "Enum" suffix in enum type names

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

## Access modifiers

#### 1. Prefer explicit access modifier declaration

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

#### 1. Do use predefined type names (C# aliases) like `int`, `float`, `string` instead of .NET Framework names like `Int32`, `Single`, `String`

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

#### 2. Do use implicit type var for local variable declarations. Exception: use explicit type declaration if no type identifier is present in current statement

```csharp
// Correct
var stream = File.Create(path);
var customers = new Dictionary();
string timeSheet;
bool isCompleted;

// Avoid
int index = int.Parse("100");
```

#### 3. Do omit Generic type identifiers whenever possible

```csharp
// Correct
List<int>() l;
l.Select(...);

// Avoid
List<int>() l;
l.Select<int>(...);
```

#### 4. Do use maximally generalized type if it does not conradict your logic

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

## Project structure

#### 1. Do name source files according to their main classes. Exception: file names with partial classes reflect their source or purpose, e.g. designer, generated, etc

```csharp
// Located in Task.cs
public partial class Task { }
// Located in Task.generated.cs
public partial class Task { }
```

#### 2. Do put classes (or enums, structures or interfaces) in separate files if they related not only to main class (or enum, structure or interface) of the file or are longer than 5-10 lines

#### 3. Do organize project folder structure to correspond to name and organisation of namespaces

```csharp
// Located in Company/Technology/Feature/Subnamespace/
namespace Company.Technology.Feature.Subnamespace { }

// Located in Company/Product/Module/SubModule/
namespace Company.Product.Module.SubModule { }

// Located in Product/Module/Component/
namespace Product.Module.Component { }

// Located in Product/Layer/Module/Group/
namespace Product.Layer.Module.Group { }
```

## Formatting

### New lines

#### 1. Place a new line to separate code by sense in 2-4 lines long sections

#### 2. Do leave a new line between class, namespace, interface or method declarations

```csharp
// Сorrect
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

### Intendation

#### 1. Do use intendation for each block

#### 2. Use whitespaces instead of tabs

#### 3. Use consistent space count (usually 4 spaces)

### Curly Brackets

#### 1. Do vertically align curly brackets

```csharp
// Correct
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

#### 2. Do place empty curly brackets block on same line and leave whitespace before brackets and in between

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

### Comments

#### 1. Do place comments on a line before the line to which comment is addressed. Leave new line between comment and previous statement

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

#### 2. Start comment with whitespace

```csharp
// Correct:
// Example of correct comment

// Avoid:
//Example of incorrect comment
```

### Attributes

#### 1. Do place attributes each on a new line before the identifier

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

#### 2. Do leave a new line between previous statement and attribute

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

## General

#### 1. Do not explicitly specify a type of an enum or values of enums (except bit fields)

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

### Keep your code as short and declarative as possible

#### 1. Do use expression body if block contains one-line statement

```csharp
// Correct
public float ToKelvin(float celsius) => celsius - 273; 

// Avoid
public float ToKelvin(float celsius)
{
    return elsius - 273; 
}
```

#### 2. Favor `foreach` over `for`

#### 3. Favor `LINQ` over `foreach`

#### 4. Do use only Method syntax of `LINQ`

### Take advantage of `C#` features and make your code clear to understand

#### 1. Prefer not to use private properties

#### 2. Prefer to use properties rather then `Set` and `Get` methods

#### 3. Do not use ternary operator more than once in the expression

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

## Parts of speech abbreviation reminder

| Abbreviation | Part of speech                       |
| :----------- | :----------------------------------- |
| N            | Noun                                 |
| V            | Verb                                 |
| Adj          | Adjective                            |
| Adv          | Adverb                               |
| Aby          | Noun or Verb or Adjective or Addverb |

The document is based on [another naming convention](https://github.com/ktaranov/naming-convention/blob/master/C%23%20Coding%20Standards%20and%20Naming%20Conventions.md).
