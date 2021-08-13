# Unity convention

## Naming

| Object type      | Notation   | Whitespaces | Plural | Part of speech | Abbreviation | Char Mask  |
| :--------------- | :--------- | ----------- | :----- | :------------- | :----------- | :--------- |
| 3D Model         | snake_case | No          | No     | Noun           | No           | [a-z][0-9] |
| Material         | snake_case | No          | No     | Noun           | No           | [a-z][0-9] |
| Shader           | snake_case | No          | No     | Noun           | No           | [a-z][0-9] |
| Texture          | snake_case | No          | No     | Noun           | No           | [a-z][0-9] |
| AnimationСlip    | snake_case | No          | No     | Noun           | No           | [a-z][0-9] |
| AudioClip        | snake_case | No          | No     | Noun           | No           | [a-z][0-9] |
| VideoClip        | snake_case | No          | No     | Noun           | No           | [a-z][0-9] |
| PhysicsMaterial  | snake_case | No          | No     | Noun           | No           | [a-z][0-9] |
| Scene            | snake_case | No          | No     | Noun           | No           | [a-z]      |
| GameObject       | PascalCase | Yes         | No     | Noun           | No           | [A-z][0-9] |
| Prefab           | PascalCase | Yes         | No     | Noun           | No           | [A-z][0-9] |
| ScriptableObject | PascalCase | Yes         | No     | Noun           | No           | [A-z][0-9] |
| Script           | PascalCase | No          | No     | Noun           | No           | [A-z][0-9] |

For examples the following notation will be used:

- `Plain text` – GameObject with name `Plain text`
- `{Script}` – A component attached to the above GameObject
- Hierarcy is displayed with 2-whitespace inddendation
- Comments start with `#`

#### 1. Only English names are allowed

#### 2. Use meaningful names everywhere

#### 3. Do not transliteration. Exception: proper names

#### 4. Do not use caps

#### 5. Avoid using Abbreviations. Exceptions: abbreviations commonly used as names, such as Id, Xml, Ftp, Uri, Ar, Vr etc

#### 6. Any asset name (excluding scripts) may be prefixed with an underscore to enforce desiered sorting order

#### 7. If prefab has a top-level (not only hierarciaclly but logicaly too) component its type name must be the last in prefab's name and separated. Type name may be separated with whitespace. Top-level GameObject name must be the same as prefab's name

```unity-scene-notation
# Correct
# Located in ItemView.prefab
ItemView
{ItemView}
  Name
  {Text}
  Icon
  {Image}

# Located in InventoryItemView.prefab
InventoryItemView
{ItemView}
  Name
  {Text}
  Icon
  {Icon}

# Located in Inventory ItemView.prefab
Inventory ItemView
{ItemView}
  Name
  {Text}
  Icon
  {Image}

# Avoid
# Located in ItemView.prefab
View
{ItemView}
  Name
  {Text}
  Icon
  {Image}

# Located in CardView.prefab
CardView
{ItemView}
  Name
  {Text}
  Icon
  {Image}
```

#### 8. ScriptableObject type must be the last in its name. Type name may be separated with whitespace

```csharp
public SomedData : ScriptableObject {}
```

```unity-scene-notation
# Correct
SomedData.asset
CharacterSomedData.asset
Character SomedData.asset

# Avoid
Some.asset
Character ScriptableObject.assset
```

#### 9. GameObject's name may include an annotation in the following format: `[Annotation] GameObjectName`. Both name and annotation should be in PascalCase and may contain whitespaces

```unity-scene-notation
# Correct
InventoryItem
{Text} ItemTitle
[PopUp] Share

# Avoid
iNvEnToRy___item
{Text} title
```

## Project structure

#### 1. Do use "Component-based" directory structure instead of "AssetType-based" directory structure

#### 2. Scripts should be placed directly in root of respective component directory

```bash
# Correct
Assets/Items/Item.cs
Assets/Items/default_texture.png

# Avoid
Assets/Items/Scripts/Item.cs
Assets/Items/default_texture.png
```

#### 3. If component has prefab from which it can be instantiated it should be placed in root of respective component directory

```bash
# Correct
Assets/Items/Prefabs/Title.prefab
Assets/Items/Item.cs
Assets/Items/Item.prefab

# Avoid
Assets/Items/Prefabs/Title.prefab
Assets/Items/Prefabs/Item.prefab
Assets/Items/Item.cs
```

#### 3. Other assets should be placed in root of respective component directory or futher separated in "AssetType-based" directory structure if there are too many of them

```bash
# Correct
Assets/Items/Models/model_a.fbx
Assets/Items/Models/model_b.fbx
Assets/Items/Models/model_c.fbx
...
Assets/Items/Item.cs

# Avoid
Assets/Items/model_a.fbx
Assets/Items/model_b.fbx
Assets/Items/model_c.fbx
...
Assets/Items/Item.cs
```

#### 4. Try to keep components small (in terms of their responsibilities, size and assets count)

#### 5. General-purpose assets should be placed in "AssetTypee-based" directory structure in project's root or in root directory for all components

```bash
# Correct
Assets/Fonts/
Assets/Items/
Assets/Sprites/icon.png

# Avoid
Assets/Fonts/
Assets/Items/
Assets/icon.png
```

#### 6. Components may have subcomponents

```bash
# Example
Assets/Menus/...
Assets/Menus/MenuItem/...
```

#### 7. Components may be organised in directories based on their purpose

```bash
# Example
Assets/UI/Menus/...
Assets/Mobs/Zombies/...
```

## Scene sctructure

#### 1. Prefer nested scene structure over flat one

```unity-scene-notation
# Correct
UI
  Tutorial
  Menu
  Pause
Game
  Character
  Environment
    Interactable
      ...
    Static
      ...

# Avoid
====UI====
Tutorial
Menu
Pause
===Game===
Caracter
Interactable
  ...
Static
  ...
```