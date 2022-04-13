# Настройка Visual Studio Code для работы с C# и Unity

Установить расширения из списка, приведенного ниже.

## Список рекомендуемых расширений

- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) – проверка орфографии
- [Russian - Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker-russian) – Русский словарь для расширения  [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker), инструкции по включению в описании расширения
- [C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) – поддержка C#
- [Debugger for Unity](https://marketplace.visualstudio.com/items?itemName=deitry.unity-debug) – отладка Unity
- [3d Viewer for VSCode](https://marketplace.visualstudio.com/items?itemName=slevesque.vscode-3dviewer) – просмоторщик 3d моделей в vscode
- [Unity3D Meta Files Watcher](https://marketplace.visualstudio.com/items?itemName=PTD.vscode-unitymeta) – следит за `.meta` файлами

## Настройка Omnisharp

Для того, чтобы пользоваться omnisharp'ом, небходимо включить поддержку Roslyn (ID свойства – `omnisharp.enableRoslynAnalyzers`)

Подробнее написано в [офф. гайде microsoft](https://code.visualstudio.com/docs/other/unity).

## Отладка

Есть два способа:

### 1. Подключение к процессу напрямую

Для того чтобы подключится к процессу редактора воспользуйтесь командой `Unity Attach Debugger`.

### 2. Создание конфигурации `launch.json`

В панели `Run and Debug` нажмите кнопку `Run and Debug`. Далее выберите `Unity debugger`, после этого `.vscode/launch.json` будет создан автоматически и иметь примерно следующие содержание:

```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Unity Editor",
            "type": "unity",
            "path": "Library/EditorInstance.json",
            "request": "launch"
        },
        {
            "name": "Windows Player",
            "type": "unity",
            "request": "launch"
        },
        {
            "name": "OSX Player",
            "type": "unity",
            "request": "launch"
        },
        {
            "name": "Linux Player",
            "type": "unity",
            "request": "launch"
        },
        {
            "name": "iOS Player",
            "type": "unity",
            "request": "launch"
        },
        {
            "name": "Android Player",
            "type": "unity",
            "request": "launch"
        },
        {
            "name": "Xbox One Player",
            "type": "unity",
            "request": "launch"
        },
        {
            "name": "PS4 Player",
            "type": "unity",
            "request": "launch"
        },
        {
            "name": "SwitchPlayer",
            "type": "unity",
            "request": "launch"
        }
    ]
}
```

### Особенности

По умолчанию Unity скрывает не-`.cs` файлы. Настроить это можно в `.vscode/settings.json`