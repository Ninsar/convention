# 3D Modelling Convention

## Naming

| Тип объекта             | Нотация    | Пробелы | Множественное число | Часть речи | Аббревиатура | Char Mask  |
| :---------------------- | :--------- | ------- | :------------------ | :--------- | :----------- | :--------- |
| 3D модель               | PascalCase | No      | No                  | Noun       | No           | [A-z][0-9] |
| Объект внутри 3D модели | PascalCase | No      | No                  | Noun       | No           | [A-z][0-9] |
| Материал                | snake_case | No      | No                  | Noun       | No           | [a-z][0-9] |
| Текстура                | snake_case | No      | No                  | Noun       | No           | [a-z][0-9] |

#### 1. Разрешены только английские имена

#### 2. Используйте осмысленные имена

#### 3. Не используйте транслитерацию. Исключение: имена собственные

#### 4. Не пишите капсом

#### 5. Не используйте сокращения. Исключение: общепринятые сокращения, такие как Id, Xml, Ftp, Uri, Ar, Vr и т.д

#### 6. Называйте объекты

Не разрешается оставлять названия примитивов или прочие названия по умолчанию, такие как:

- Cube
- Box
- Cylinder
- Cone
- Sphere
- и т. п.

Исключение: название объекта действительно соответствует объекту, т. е., если у вас в модели есть коробка, то она может называться Box.

#### 7. Добавляйте в начало имени материала имя модели в `camel_case`

#### 8. Называйте текстуры согласно следующией схеме: `"имя модели"_"дополнительная информация"_"тип текстуры"`. `"дополнительная информация"` может быть не указана. `"имя модели"` должно быть в `snake_case`. `"тип текстуры"` должен иметь суффикс `_map`

```bash
# Пример именования текстур для модели, названной "Some.fbx":

# для текстуры альбедо (basemap)
some_base_map.png

# для metallic map текстуры
some_metallic_map.png

# для normal map текстуры
some_normal_map.png

# для height map текстуры
some_height_map.png

# для emission map текстуры
some_emission_map.png

# для occlusion map текстуры
some_ao_map.png

# для height (deform) map текстуры
some_height_map.png
```

## Pivot

Размещайте pivot (origin, начало координат) следующим образом:

Если модель должна "соединиться" с чему-либо (например, предмет, который будет держать персонаж), pivot должен быть "точкой соединения".

В противном случае, pivot должен располагаться на bounding box'е (воображаемый параллелепипед, описанный вокруг модели), желательно его вершинах или точках пересечениях с осями координат.

Пример:
![Pivot example](img/pivot.png)
Считая, что сфера – модель и bounding box – желтый куб, возможное положение pivot'а обозначено красными точками.

## Transform

Для каждого объекта локальный масштаб должен быть `(1, 1, 1)`. Если нужно изменить масштаб, меняйте масштаб самого меша.

## Dimensions

Следите за размерами и углами в модели, особенно если вы моделите что-то архитектурное. Помните, что `1 unit = 1 meter`.

## Общее

#### 1. Для каждого материала должна быть хотя бы basemap-текстура

#### 2. Используйте такие UV-развертки, чтобы размер текстур был минимально возможным
