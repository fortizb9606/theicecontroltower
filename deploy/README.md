# Torre de Control — The Ice Mind

Carpeta lista para subir a GitHub y desplegar en Netlify (theicecontroltower.netlify.app).

## Qué hay acá

- **index.html** — el sitio completo (HTML + CSS + JS en un solo archivo, sin build step).
  Vista principal "Cerebro" con Ice Mind, más Radar, Muro, Agentes, Detalle del día,
  Sala de reuniones y Estructura.
- **firestore.rules** — reconstruidas según lo documentado del proyecto (lectura pública
  de `chiefs`, escritura con sesión anónima para el resto). **Revísalas contra las que ya
  están desplegadas en Firebase antes de reemplazarlas** — no es una descarga del archivo
  real, es una reconstrucción para que el deploy quede completo.
- **netlify.toml** — config mínima (publica la carpeta raíz, todo enruta a index.html).

## Cómo subirlo

```bash
git add .
git commit -m "Cerebro operativo + Ice Mind"
git push
```

Si tu Netlify está conectado a este repo, el deploy sale solo. Si lo subes por
drag-and-drop en vez de por git, recuerda que el repo se queda con la versión
vieja — conviene igual pushear para que ambos quedan sincronizados.

## Firestore

El `index.html` ya trae la configuración de Firebase del proyecto `theicecontroltower`
adentro (es pública por diseño). No hace falta tocar nada para que conecte — apenas se
abre, se conecta solo y muestra el badge **EN VIVO** si todo está bien.

Para que la pestaña **Sala de reuniones → Generar conversación** persista entre
sesiones (hoy tira "Missing or insufficient permissions" y solo se ve mientras no
recargues la página), hay que subir `firestore.rules` con la regla de `meetingRequests`
que ya viene incluida acá.

## Chiefs con datos reales hoy

`fin`, `rev`, `leg`, `dst` — ya están escribiendo agentes de Cowork.
`rrhh` y `vta` existen en Firestore pero sin contenido todavía.
`mkt` y `prd` no tienen documento en Firestore — se ven con datos de ejemplo
hasta que sus agentes empiecen a escribir.
