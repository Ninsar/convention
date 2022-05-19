# Macos workflow guide

## Как добавить пустые ячейки между ярлыками в Dock'е Macos, чтобы он выглядел удобно и лаконично?

### 1. Для начала нужно выстроить порядок приложений и понять где между ними будет пробел для их отделения.

![Dock initial view](img/Macos/DockWhiteSpaces/img1.png)

#### Как видно на данном скрине, то все, что касается кодинга - Unity, терминал, Fork, Android Studio, VS Code - будут отдельной секцией. Keynote, Safari, Numbers, Pages - другой и календарь, Mattermost, Telegram, Почта - третьей.

### 2. Далее, открываем Terminal и прописываем следующие команды: 

```bash

> defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="spacer-tile";}'

> killall Dock
```
