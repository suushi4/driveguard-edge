# driveguard-fullstack

Полный full-stack сайт без внешних зависимостей и этапа сборки. Node.js обслуживает интерфейс, REST API, SSE-телеметрию, журнал, CSV и прокси команд ESP32.

## Локально
```bash
npm start
```
Откройте `http://localhost:4173`.

## Render
1. Загрузите содержимое ZIP в корень нового GitHub-репозитория.
2. Render → New → Blueprint.
3. Подключите репозиторий → Apply.

`render.yaml` уже содержит все команды. Root Directory должен быть пустым. Никакие `cd` и `npm install` не нужны.

## API
- `GET /api/health`, `/api/state`, `/api/config`, `/api/incidents`
- `PUT /api/config`
- `POST /api/incidents`, `/api/command`
- `GET /api/events` — SSE
- `GET /api/incidents.csv`

Render не видит `192.168.x.x`. Для реальной ESP32 публичному сайту нужен защищённый HTTPS-мост (например, Cloudflare Tunnel к локальному edge-service). Не публикуйте ESP32 напрямую.
