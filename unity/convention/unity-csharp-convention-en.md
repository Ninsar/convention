# Unity C# Convention

## Changes from [С# Convention](../csharp/csharp-convention.md)

### Projet Structure

#### 3. Do name namespaces to correspond to components sctructure. Omit `Assets` in namespace name

```csharp
// Located in Assets/Items/
namespace Items { }

// Located in Assets/Items/Subcomponent/
namespace Items.Subcomponent { }
```
