# 3D Modelling Convention

## Naming

| Object type      | Notation   | Whitespaces | Plural | Part of speech | Abbreviation | Char Mask  |
| :--------------- | :--------- | ----------- | :----- | :------------- | :----------- | :--------- |
| 3D Model         | PascalCase | No          | No     | Noun           | No           | [A-z][0-9] |
| Material         | snake_case | No          | No     | Noun           | No           | [a-z][0-9] |
| Texture          | snake_case | No          | No     | Noun           | No           | [a-z][0-9] |

#### 1. Only English names are allowed

#### 2. Use meaningful names everywhere

#### 3. Do not transliteration. Exception: proper names

#### 4. Do not use caps

#### 5. Avoid using Abbreviations. Exceptions: abbreviations commonly used as names, such as Id, Xml, Ftp, Uri, Ar, Vr etc

#### 6. Do prefix material names with model name in `camel_case`

#### 7. Do name textures according to this scheme: `"model name"_"additional data"_"texture king"`. `"additional data"` may not be specified. `"model name"` must be in `snake_case`. `"texture kind"` sould have `_map` suffix

```bash
# Example texture naming for model named "Some.fbx":

# for albedo texture (basemap)
some_base_map.png

# for metallic map texture
some_metallic_map.png

# for normal map texture
some_normal_map.png

# for height map texture
some_height_map.png

# for emission map texture
some_emission_map.png

# for occlusion map texture
some_ao_map.png

# for height (deform) map texture
some_height_map.png
```

## General

#### 1. For each material there should be at least basemap texture

#### 2. Use UVs to keep textures as small as possible
