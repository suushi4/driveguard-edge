# DriveGuard Edge

Production-oriented multilingual dashboard for ESP32-CAM driver drowsiness monitoring.

## Features
- Russian, English and Kazakh UI with persisted language/theme/device settings
- Live demo facial-landmark HUD and 60-second telemetry
- ESP32 connection test, alarm endpoints, servo control and auto-sync
- Web Audio + multilingual speech warning
- Incident filtering and CSV export
- Graceful offline demo mode; responsive light/dark UI
- Minimal Node API proxy for CORS-safe ESP32 requests

## Local setup
```bash
npm install
npm run build
npm start
```
Open `http://localhost:4173`.

## Environment
- `PORT` — HTTP port (default `4173`)

The device URL is configured in the dashboard and stored in LocalStorage. The backend proxies requests through `/api/esp32?url=...`. For production, restrict target hosts to your LAN/VPN allowlist and serve over HTTPS. Browsers cannot directly reach an ESP32 on a private network from a public cloud deployment unless the device is exposed through a secure gateway.

## ESP32 endpoints
- `GET /` — connection probe
- `GET /alert?drowsy=1|0`
- `GET /servo?angle=0..180`
- MJPEG stream URL can be extended in `HUD.tsx`.

## Deploy
Static frontend: publish `dist/`. Full stack: deploy with `npm run build && npm start` on any Node 20+ host. Health endpoint: `/api/health`.

## Camera sources

The Vision Source Hub supports:
- animated privacy-safe demo vision;
- every `videoinput` device exposed by the current browser (`getUserMedia` + `enumerateDevices`);
- an ESP32-CAM or phone IP-camera MJPEG URL.

Camera access requires HTTPS in production and explicit browser permission. A phone opened as a separate browser cannot be viewed remotely without a signaling/streaming service; for the current version, use an IP-camera app that exposes an MJPEG URL on the same network.

## Version 2 interface

Includes working Overview/Incidents/Settings navigation, localized logs and CSV export, camera switching, account drawer, animated emergency overlay, richer SOS audio, custom shield-eye branding, and refined responsive styling.
