# webhook-whatsapp-api

Webhook mínimo en **Node.js + Express** para recibir eventos de la **WhatsApp Cloud API** (Meta).

## Requisitos

- Node.js 18+

## Instalación

```bash
npm install
```

## Variables de entorno

| Variable       | Descripción                                        | Default |
| -------------- | -------------------------------------------------- | ------- |
| `PORT`         | Puerto del servidor                                | `3000`  |
| `VERIFY_TOKEN` | Token de verificación configurado en Meta          | —       |

Ejecución (PowerShell):

```powershell
$env:PORT=3000; $env:VERIFY_TOKEN="mi_token_secreto"; npm start
```

## Endpoints

- `GET /` → verificación del webhook. Meta envía `hub.mode`, `hub.verify_token` y `hub.challenge`; si el token coincide responde el challenge con `200`, si no `403`.
- `POST /` → recepción de eventos. Imprime el JSON recibido en consola y responde `200`.

## Probar localmente

1. Arranca el servidor: `npm start`.
2. Expón el puerto con un túnel, por ejemplo: `ngrok http 3000`.
3. En Meta → WhatsApp → Configuration → Webhook, usa la URL pública del túnel y el mismo valor de `VERIFY_TOKEN`.
