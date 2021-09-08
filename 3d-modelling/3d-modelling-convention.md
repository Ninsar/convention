# 3D Modelling Convention

## Naming

| Object type      | Notation   | Whitespaces | Plural | Part of speech | Abbreviation | Char Mask  |
| :--------------- | :--------- | ----------- | :----- | :------------- | :----------- | :--------- |
| 3D Model         | PascalCase | No          | No     | Noun           | No           | [a-z][0-9] |
| Material         | snake_case | No          | No     | Noun           | No           | [a-z][0-9] |
| Texture          | snake_case | No          | No     | Noun           | No           | [a-z][0-9] |

#### 1. Only English names are allowed

#### 2. Use meaningful names everywhere

#### 3. Do not transliteration. Exception: proper names

#### 4. Do not use caps

#### 5. Avoid using Abbreviations. Exceptions: abbreviations commonly used as names, such as Id, Xml, Ftp, Uri, Ar, Vr etc

#### 6. Do prefix material names with model name in `camel_case`

#### 7. Do name textures according to this scheme: `"model name"_"additional data"_"texture king"`. `"additional data"` may not be specified. `"model name"` must be in `camel_case`

```bash
# Example texture naming for model named "Some.fbx":

# for albedo texture
some_albedo.png

# for metallic map texture
some_metallic.png

# for normal map texture
some_normal.png

# for occlusion map texture
some_ao.png

# for height (deform) map texture
some_height.png
```
