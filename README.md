# Paradixe

Un mundo 3D compartido que corre en el navegador. Un solo servicio Node entrega la página y conecta a los jugadores por WebSocket.

## Archivos

- `index.html`: el mundo 3D y la conexión con el servidor.
- `server.js`: entrega la página y reparte las posiciones de los jugadores.
- `package.json`: dependencias (solo `ws`) y el comando de inicio.

Mantén los tres archivos juntos, en la raíz del repositorio.

## Probarlo en el celular con Termux

```
pkg install nodejs
npm install
npm start
```

Abre `http://localhost:3000` en el navegador del mismo celular. Para probar con otro dispositivo en tu red, usa la IP del celular en lugar de `localhost`.

## Publicarlo con tu dominio

1. Crea un repositorio en GitHub y sube los tres archivos desde la web (Add file, Create new file o Upload files).
2. En un hosting que ejecute Node (por ejemplo Render, Railway o Fly.io) crea un servicio nuevo desde ese repositorio.
   - Comando de instalación: `npm install`
   - Comando de inicio: `npm start`
   - El hosting define el puerto con la variable `PORT`; el servidor ya la lee.
3. Cuando el servicio funcione con su dirección de prueba, entra a su sección de dominios personalizados y agrega `paradixe.space`.
4. El hosting te mostrará los registros DNS que debes crear. Agrégalos en el panel donde compraste el dominio. Los cambios pueden tardar desde minutos hasta unas horas.
5. El hosting activa el candado HTTPS por su cuenta. Con HTTPS el multijugador usa `wss://` sin que tengas que cambiar nada.

Comprueba que el servicio responde abriendo `/health`: debe mostrar `ok`.

Si también usas `www.paradixe.space`, agrégalo a la variable de entorno `ALLOWED_ORIGINS` (por ejemplo `www.paradixe.space`) y también como dominio personalizado en el hosting.

## Qué incluye

- Hasta 100 jugadores a la vez (cambia `MAX_PLAYERS` para ajustarlo) y hasta 10 conexiones por dirección IP.
- El servidor limpia los nombres, mantiene a cada jugador dentro de la plaza, limita los mensajes por segundo y desconecta las conexiones que dejan de responder.
- Solo entrega la página principal y `/health`; ningún otro archivo del proyecto queda expuesto.

## Qué no incluye todavía

- No guarda nada: sin cuentas, sin progreso, sin base de datos. Al cerrar la página se pierde todo.
- Hay una sola sala para todos los jugadores.
- Los portales de la plaza todavía no llevan a otros mundos.
- Un servicio gratuito puede dormirse tras un tiempo sin visitas; al despertar tarda en responder y corta las conexiones abiertas. Para que esté siempre activo hace falta un plan de pago.
