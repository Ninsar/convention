# Unity C# Convention

## Измениния по сравнению с [С# Convention](../csharp/csharp-convention-ru.md)

### Структура проекта

#### 3. Называйте namespace'ы так, чтобы они соответствовали пространствам имен. Опускайте `Assets` в имени namespace

```csharp
// Расположен in Assets/Items/
namespace Items { }

// Расположен in Assets/Items/Subcomponent/
namespace Items.Subcomponent { }
```
