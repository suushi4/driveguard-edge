# DriveGuard Monitor — zero-build Render edition

Статический проект без Node.js, npm и сборщика. Он разворачивается через Render Blueprint одной кнопкой.

## GitHub

Загрузите в корень репозитория:

```text
render.yaml
README.md
public/
```

Не помещайте файлы в дополнительную папку с пробелами.

## Render

1. Render → New → Blueprint.
2. Подключите репозиторий.
3. Render прочитает `render.yaml`.
4. Нажмите Apply.

Ручные настройки не требуются. Если создаёте сервис вручную:

```text
Service type: Static Site
Build Command: echo "DriveGuard static site ready"
Publish Directory: public
```

## ESP32-CAM

Публичный Render не видит локальные IP `192.168.x.x`. Для аппаратного режима укажите защищённый HTTPS-адрес локального моста. Не открывайте ESP32 напрямую в интернет. При локальном открытии `public/index.html` адрес локальной камеры можно использовать при корректном CORS.
