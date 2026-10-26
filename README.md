# Paradixe.space v0.2

Un universo digital. Infinitas posibilidades por explorar.

Plaza Central es la primera experiencia 3D multijugador que corre en el navegador. Un solo servicio Node entrega la página y conecta jugadores por WebSocket.

## Qué hay en v0.2 (lo que pediste)

1. **Fix index.html** - El servidor buscaba `index.html` pero venía como `index-1.html`. Ahora los 3 archivos están alineados y listos para GitHub.
2. **Chat de proximidad** - Nuevo. Solo te leen jugadores a <18m. Rate limit 5 mensajes / 10s, 120 chars max, filtro de <>.
3. **Portales con toast mejorado** - Ahora muestra "Próximamente: Arcadia" + nota + badge + mensaje en chat sistema.
4. **Landing oficial** - `landing.html` con descripción oficial, visión, 4 mundos proyectados, base tecnológica y posicionamiento honesto.

## Archivos para GitHub (raíz del repo)

- `index.html` - Plaza Central v0.2 con chat
- `server.js` - HTTP + WebSocket + chat proximidad
- `package.json` - v0.2.0, dependencia ws 8.18.0
- `landing.html` - Landing oficial (opcional, ruta /landing.html)

Mantén los 3 primeros juntos en la raíz.

## Probar en celular con Termux

```
pkg install nodejs
npm install
npm start
```

Abre http://localhost:3000 -> Plaza Central
Abre http://localhost:3000/landing.html -> Landing oficial
/health debe responder ok

## Publicar con tu dominio paradixe.space

1. Repo en GitHub, sube los 3 archivos (Add file > Upload files)
2. Hosting Node (Render, Railway, Fly.io):
   - Install: npm install
   - Start: npm start
   - PORT lo pone el hosting, ya lo lee
3. Dominio personalizado: agrega paradixe.space en el hosting, copia los DNS al panel donde compraste el dominio
4. Si usas www.paradixe.space, agrégalo a ALLOWED_ORIGINS=www.paradixe.space en env vars del hosting

HTTPS lo activa el hosting. El cliente usa wss:// automático.

## Qué incluye / qué no

Incluye: hasta 100 jugadores (MAX_PLAYERS), 10 por IP, limpieza de nombres, límite mundo radio 35, 40 msgs/s, ping/pong, solo expone / y /health, chat proximidad 18m.

No incluye aún: cuentas, progreso, base de datos, múltiples salas, portales funcionales a otros mundos, inventario/economía. Al cerrar se pierde todo. Servicio gratis puede dormirse.

## Próximos pasos sugeridos (de tu doc oficial)

- Verificar multijugador real y rendimiento
- Definir qué social aporta valor además de caminar (emotes, fotos, voz?)
- Diseñar mundos de forma modular para conectar progresivamente
- Comunicar estado honesto: experiencia inicial en desarrollo con potencial de expansión

---
Medellín 2026 · Ander Song
Explora nuevos mundos. Conecta experiencias. Descubre Paradixe.
