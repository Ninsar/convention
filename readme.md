# Ninsar конвенции

Этот репозиторий содержит все кодовые стили, соглашения, рекомендации и т. д., принятые в нашей организации.

## Содержание

- `git`
  - Convention ([en](git/git-convention.md ) / [ru](git/git-convention-ru.md))
- `C#`
  - Convention ([en](csharp/csharp-convention.md ) / [ru](csharp/csharp-convention-ru.md))
  - [.editorconfig](csharp/.editorconfig)
- `3D Modelling`
  - Convention ([en](3d-modelling/3d-modelling-convention.md) / [ru](3d-modelling/3d-modelling-convention-ru.md))
  - Presets ([en](3d-modelling/presets.md) / [ru](3d-modelling/presets-ru.md))
- `Unity`
  - Convention ([en](unity/unity-convention.md ) / [ru](unity/unity-convention-ru.md))
  - C# Convention ([en](unity/unity-csharp-convention.md ) / [ru](unity/unity-csharp-convention-ru.md))
  - [C# Guide (WIP)](unity/unity-csharp-guide.md)
  - [Git LFS Settings](unity/.gitattributes)

## Файловая структура репозитория

В этом проекте файлы организованы следующим образом:

1. Для каждого инструмента создается отдельная папка `tool-name`
2. Конвенции (набор соглашений и рекомендаций по использованию какого-либо инструмента) располагаются по пути `<tool-name>/<tool-name>-convention.md` или `<tool-name>/convention/<tool-name>-convention-<lang>.md`, где `<lang>` – язык, `<tool-name>` – название инструмента
3. Гайды по работе с каким-либо инструментом располагаются по пути `<tool-name>/guides/<guide-name>.md`, где `<guide-name>` – название гайда. Если гайд содержит иллюстрации, они должны быть расположены по пути `<tool-name>/guides/<guide-name>.md`.
4. Если гайд единственный, его следует расположить в `<tool-name>/guide.md`, а его иллюстрации (при наличии) в `<tool-name>/img/`

## Поддержка проекта

Согласуйте изменения со всеми участниками, которых коснутся предлагаемые изменения, создайте пул-реквест и запросите проверку у мейнтейнеров проекта.
