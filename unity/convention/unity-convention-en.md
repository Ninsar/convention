# Unity Convention

## Naming

| Object type      | Notation   | Whitespaces | Plural | Part of speech | Abbreviation | Char Mask  |
| :--------------- | :--------- | ----------- | :----- | :------------- | :----------- | :--------- |
| 3D Model         | PascalCase | No          | No     | Noun           | No           | [A-z][0-9] |
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
- Hierarcy is displayed with 2-whitespace intendation
- Comments start with `#`

#### 1. Only English names are allowed

#### 2. Use meaningful names everywhere

#### 3. Do not transliteration. Exception: proper names

#### 4. Do not use caps

#### 5. Avoid using Abbreviations. Exceptions: abbreviations commonly used as names, such as Id, Xml, Ftp, Uri, Ar, Vr etc

#### 6. If material belongs to model (is not a general-purpose) do prefix material names with model name in `camel_case`

#### 7. Do name textures according to this scheme: `"model name"_"additional data"_"texture king"`. `"additional data"` may not be specified. `"model name"` must be in `snake_case`

```bash
# Example texture naming for model named "Some.fbx":

# for albedo texture
some_albedo.png

# for metallic map texture
some_metallic.png

# for normal map texture
some_normal.png

# for height map texture
some_height.png

# for emission map texture
some_emission.png

# for occlusion map texture
some_ao.png

# for height (deform) map texture
some_height.png
```

#### 8. Any asset name (excluding scripts) may be prefixed with an underscore to enforce desiered sorting order

#### 9. If prefab has a top-level (not only hierarciaclly but logicaly too) component its type name must be the last in prefab's name and separated. Type name may be separated with whitespace. Top-level GameObject name must be the same as prefab's name

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

#### 10. ScriptableObject type must be the last in its name. Type name may be separated with whitespace

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

#### 11. GameObject's name may include an annotation in the following format: `[Annotation] GameObjectName`. Both name and annotation should be in PascalCase and may contain whitespaces

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

Unity proposes AssetType-based project structure:

```bash
Assets/Textures/grass.png
Assets/Textures/dirt.png
Assets/Scenes/main.unity
Assets/Meshes/model.fbx
Assets/Materials/MaterialB.mat
Assets/Materials/MaterialA.mat
```

However, larger the project becomes more unwieldy AssetType-based structure gets.

Instead, organise assets by components (component being a self-contained part of something). Every asset of a component must be stored in one directory.

E. g. shooter game project structure:

```bash
Assets/Player/Player.prefab
Assets/Player/FirstPersonController.cs
Assets/Weapons/Weapon.cs
Assets/Weapons/Ar15/Ar15.cs
Assets/Weapons/Ar15/ar15.fbx
Assets/Weapons/Ar15/ar15.png
Assets/Weapons/Ar15/223_rem.fbx
Assets/Weapons/Ar15/223_rem.png
...
Assets/Maps/
...
```

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
Assets/Menu/...
Assets/Menu/MenuItem/...
```

#### 7. Components may be organised in directories based on their purpose

```bash
# Example
Assets/UI/Menu/...
Assets/Mobs/Zombies/...
```

## Allowed assets file formats

#### 1. Only assets in common exchange formats are allowed

Reason: Some formats are not designed for purpose of exchanging and may require plugins (which as well may be buggy) and/or third party software (which may be heavy or unsupported across multiple platforms).

#### 2. Prefer open source formats if possible

#### 3. List of allowed formats (from most recommended to least in each category)

| Category  | Format | Notes                                  |
| --------- | ------ | -------------------------------------- |
| 3D Models | fbx    | Closed-source, but is widely used      |
| 3D Models | obj    | Open-source                            |
| Images    | png    |                                        |
| Images    | jpg    |                                        |
| Images    | tif    |                                        |
| Images    | exr    | HDR raster format                      |
| Audio     | wav    |                                        |
| Audio     | ogg    |                                        |
| Audio     | mp3    |                                        |
| Video     | mp4    |                                        |
| Video     | webm   | Use vp8 webm if transparency is needed |

## Scene structure

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
Character
Interactable
  ...
Static
  ...
```

## Prefabs

#### 1. Prefer nested prefab structure over flat one

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
Character
Interactable
  ...
Static
  ...
```

#### 2. Do not unpack prefabs unless it is necessary

## Builds

#### 1. Builds should be stored in `Builds/"Platform"/` where `"Platform"` is platforrm for which build is done

NB: Correct spelling is: `iOS`, `macOS`, `Android`, `Windows`, `Linux`, `WebGL`

#### 2. Releases should be stored in `Builds/"Platform"/Release` (exept iOS releases bcs they are built via xcode)

#### 3. For any post-build actions use Build PostProcessing (useful to do builds in CI)

## Git

#### 1. Use `git lfs` for each binary file

Exaple of `.gitattributes`:

```bash
# Image formats:
*.tga filter=lfs diff=lfs merge=lfs
*.png filter=lfs diff=lfs merge=lfs
*.tif filter=lfs diff=lfs merge=lfs
*.jpg filter=lfs diff=lfs merge=lfs
*.gif filter=lfs diff=lfs merge=lfs
*.psd filter=lfs diff=lfs merge=lfs
*.exr filter=lfs diff=lfs merge=lfs

# Audio formats:
*.ogg filter=lfs diff=lfs merge=lfs
*.mp3 filter=lfs diff=lfs merge=lfs
*.wav filter=lfs diff=lfs merge=lfs
*.aiff filter=lfs diff=lfs merge=lfs

# 3D model formats:
*.fbx filter=lfs diff=lfs merge=lfs
*.obj filter=lfs diff=lfs merge=lfs

# Dynamic libraries formats:
*.dll filter=lfs diff=lfs merge=lfs
*.so filter=lfs diff=lfs merge=lfs
*.dylib filter=lfs diff=lfs merge=lfs

# Video formats:
*.webm filter=lfs diff=lfs merge=lfs
*.mp4 filter=lfs diff=lfs merge=lfs
*.mov filter=lfs diff=lfs merge=lfs
```

#### 2. Repository name must be equal to `ProductName` in Player settings
