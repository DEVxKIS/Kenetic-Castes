<p align="center"><img src="./app/assets/images/SealCircle.png" width="150px" height="150px" alt="Aventium Softworks"></p>

<h1 align="center">Пусковая установка Гелиоса</h1>

<em><h5 align="center">(ранее Electron Launcher)</h5></em>

[<p align="center"><img src="https://img.shields.io/github/actions/workflow/status/dscalzi/HeliosLauncher/build.yml?branch=master&style=for-the-badge" alt="gh actions">](https://github.com/dscalzi/HeliosLauncher/actions) [ <img src="https://img.shields.io/github/downloads/dscalzi/HeliosLauncher/total.svg?style=for-the-badge" alt="downloads">](https://github.com/dscalzi/HeliosLauncher/releases) <img src="https://forthebadge.com/images/badges/winter-is-coming.svg" height="28px" alt="зима близко"></p>

<p align="center">Присоединяйтесь к модифицированным серверам, не беспокоясь об установке Java, Forge или других модов. Мы позаботимся об этом за вас.</p>

! [Скриншот 1](https://i.imgur.com/6o7SmH6.png)
! [Скриншот 2](https://i.imgur.com/x3B34n1.png)

## Функции

* 🔒 Полное управление счетом.
  * Добавляйте несколько учетных записей и легко переключайтесь между ними.
  * Аутентификация Microsoft (OAuth 2.0) + Mojang (Yggdrasil) полностью поддерживается.
  * Учетные данные никогда не хранятся и не передаются непосредственно в Mojang.
* 📂 Эффективное управление активами.
  * Получайте обновления клиента, как только мы их выпустим.
  * Файлы проверяются перед запуском. Поврежденные или неправильные файлы будут загружены повторно.
* ☕ **Автоматическая валидация Java.**
  * Если у вас установлена несовместимая версия Java, мы установим подходящую *для вас*.
  * Вам не нужно устанавливать Java для запуска лаунчера.
* 📰 Новостная лента встроена в лаунчер.
* ⚙️ Интуитивно понятное управление настройками, включая панель управления Java.
* Поддерживает все наши серверы.
  * Легко переключайтесь между конфигурациями серверов.
  * Просмотр количества игроков на выбранном сервере.
* Автоматические обновления. Правильно, лаунчер обновляется.
* Просмотр состояния служб Mojang.

Это не исчерпывающий список. Загрузите и установите лаунчер, чтобы оценить все, на что он способен!

#### Нужна помощь? [См. вики. ][вики]

#### Понравился проект? Оставьте звездочку ⭐ на репозитории!

## Загрузки

Вы можете скачать с [GitHub Releases](https://github.com/dscalzi/HeliosLauncher/releases)

#### Последний релиз

[! [](https://img.shields.io/github/release/dscalzi/HeliosLauncher.svg?style=flat-square)](https://github.com/dscalzi/HeliosLauncher/releases/latest)

#### Последняя предварительная версия
[! [](https://img.shields.io/github/release/dscalzi/HeliosLauncher/all.svg?style=flat-square)](https://github.com/dscalzi/HeliosLauncher/releases)

**Поддерживаемые платформы**

Если вы загружаете с вкладки [Releases](https://github.com/dscalzi/HeliosLauncher/releases), выберите установщик для вашей системы.

| Платформа | Файл |
| -------- | ---- |
| Windows x64 |  'Helios-Launcher-setup-VERSION.exe' |
| macOS x64 |  'Helios-Launcher-setup-VERSION-x64.dmg' |
| macOS arm64 |  'Helios-Launcher-setup-VERSION-arm64.dmg' |
| Линукс x64 |  'Helios-Launcher-setup-VERSION.AppImage' |

## Консоль

Чтобы открыть консоль, используйте следующую привязку клавиш.

```консоль
Ctrl + Shift + I
```

Убедитесь, что выбрана вкладка консоли. Не вставляйте ничего в консоль, если вы не уверены на 100% в том, что она будет делать. Вставка неправильного элемента может привести к раскрытию конфиденциальной информации.

#### Экспорт выходных данных в файл

Если вы хотите экспортировать вывод консоли, просто щелкните правой кнопкой мыши в любом месте консоли и выберите **Сохранить как..**

! [пример консоли](https://i.imgur.com/T5e73jP.png)


## Развитие

В этом разделе подробно описывается настройка базовой среды разработки.

### Начало работы

**Требования к системе**

* [Node.js][nodejs] v20

---

**Клонирование и установка зависимостей**

```консоль
> git clone https://github.com/dscalzi/HeliosLauncher.git
> cd HeliosLauncher
> Установка npm
```

---

**Запустить приложение**

```консоль
> Запуск npm
```

---

**Сборка установщиков**

Для сборки для текущей платформы.

```консоль
> npm run dist
```

Сборка для конкретной платформы.

| Платформа | Команда |
| ----------- | -------------------- |
| Windows x64 |  'npm run dist:win' |
| macOS |  'npm run dist:mac' |
| Линукс x64 |  'npm run dist:linux' |

Сборки для macOS могут не работать в Windows/Linux и наоборот.

---

### Код Visual Studio

Вся разработка лаунчера должна выполняться с использованием [Visual Studio Code][vscode].

Вставьте следующее в '.vscode/launch.json`

```Формат JSON
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Отладка основного процесса",
      "type": "узел",
      "request": "запустить",
      "cwd": "${workspaceFolder}",
      "program": "${workspaceFolder}/node_modules/electron/cli.js",
      "args" : ["."],
      "outputCapture": "std"
    },
    {
      "name": "Отладка процесса рендеринга",
      "type": "хром",
      "request": "запустить",
      "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/electron",
      "windows": {
        "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/electron.cmd"
      },
      "runtimeArgs": [
        "${workspaceFolder}/. ",
        "--remote-debugging-port=9222"
      ],
      "webRoot": "${workspaceFolder}"
    }
  ]
}
```

При этом добавляются две конфигурации отладки.

#### Отладка основного процесса

Это позволяет отлаживать [основной процесс][mainprocess]. Вы можете отлаживать скрипты в [renderer process][rendererprocess], открыв окно DevTools.

#### Процесс отладки рендерера

Это позволяет отлаживать [renderer process][rendererprocess]. Для этого необходимо установить расширение [Отладчик для Chrome][chromedebugger].

Обратите внимание, что вы **не можете** открыть окно DevTools при использовании этой конфигурации отладки. Chromium допускает только один отладчик, открытие другого приведет к аварийному завершению программы.

---

### Примечание об использовании третьими лицами

Пожалуйста, укажите автора оригинала и дайте ссылку на первоисточник. Это свободное программное обеспечение, пожалуйста, сделайте хотя бы столько-то.

Инструкции по настройке проверки подлинности Майкрософт см. в разделе https://github.com/dscalzi/HeliosLauncher/blob/master/docs/MicrosoftAuth.md.

---

## Ресурсы

* [Вики][вики]
* [Туманность (Создать Distribution.json)][туманность]
* [v2 Ветка перезаписи (неактивная)][v2ветка]

Лучший способ связаться с разработчиками — через Discord.

[! [дискорд](https://discordapp.com/api/guilds/211524927831015424/embed.png?style=banner3)][дискорд]

---

### До встречи в игре.


[nodejs]: https://nodejs.org/en/ 'Node.js'
[vscode]: https://code.visualstudio.com/ 'Visual Studio Code'
[mainprocess]: https://electronjs.org/docs/tutorial/application-architecture#main-and-renderer-processes 'Основной процесс'
[rendererprocess]: https://electronjs.org/docs/tutorial/application-architecture#main-and-renderer-processes 'Процесс рендеринга'
[chromedebugger]: https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome 'Отладчик для Chrome'
[discord]: https://discord.gg/zNWUXdt 'Discord'
[wiki]: https://github.com/dscalzi/HeliosLauncher/wiki 'wiki'
[nebula]: https://github.com/dscalzi/Nebula 'dscalzi/Nebula'
[v2branch]: https://github.com/dscalzi/HeliosLauncher/tree/ts-refactor 'ветка v2'
