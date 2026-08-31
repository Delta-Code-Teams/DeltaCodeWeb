# Delta Code Enterprise — sitio web

## Estructura

```
/
├── index.html              ← página principal
├── favicon.ico, *.png      ← favicon en todos los formatos estándar
├── site.webmanifest
└── img/
    ├── nombre.webp          ← formato liviano, se usa primero
    └── nombre.png           ← fallback para navegadores viejos
```

## Cómo se resolvieron las imágenes

Antes: 10 imágenes venían incrustadas como `base64` directo en el HTML
(archivo de 462 KB). Ahora son archivos reales en `/img`, servidos en
WebP (con PNG como respaldo vía `<picture>`), lo que:

- Reduce el HTML a 54 KB
- Permite que el navegador cachee cada imagen por separado
- Baja el peso de las imágenes ~35-45% gracias a WebP

## Deploy en Vercel o Netlify

1. Subí este repo a GitHub (código + carpeta `img/` + favicons).
2. En Vercel: "Add New Project" → importá el repo → sin build command,
   sin framework (Other/Static) → Deploy.
   En Netlify: "Add new site" → "Import an existing project" → mismo repo,
   dejá "Build command" vacío y "Publish directory" en `.` (raíz).
3. Listo, el dominio que te asigna Vercel/Netlify sirve todo directo,
   sin depender de GitHub Pages ni de rutas `raw.githubusercontent.com`.

## Favicon

Los archivos ya están referenciados en el `<head>` de `index.html`:
`favicon.ico`, `favicon-16x16.png`, `favicon-32x32.png`,
`apple-touch-icon.png`, `android-chrome-192x192.png`,
`android-chrome-512x512.png` y `site.webmanifest` (con el theme color
de la marca, `#090511`).

## Cursor personalizado

El cursor (punto + anillo violeta) ya no se transforma nunca en el
cursor nativo de Windows. En vez de eso, al pasar sobre algo clickeable
(links, botones, price cards, preguntas del FAQ, mockups interactivos)
el punto central se convierte en una pequeña flecha con glow blanco,
dentro del mismo anillo neon que se agranda — mantiene la identidad
visual pero deja clarísimo qué se puede clickear.
