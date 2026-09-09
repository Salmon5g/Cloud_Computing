# Cloud Computing

Sistema web desarrollado en la asignatura **Computación en la Nube** del Instituto Profesional Santo Tomás.

Página principal: [`Html/index.html`](Html/index.html)

## Descripción

Sitio estático con temática del FC Barcelona que pone en práctica conceptos de computación en la nube. Incluye una encuesta de opinión almacenada en el navegador (localStorage) y un CRUD de jugadores conectado a **Firestore** (Base de Datos como Servicio) de Google Cloud.

## Páginas

| Archivo | Descripción | Almacenamiento |
|---|---|---|
| [`index.html`](index.html) | Redirige a la página principal (evita el 404 en GitHub Pages) | — |
| [`Html/index.html`](Html/index.html) | Inicio con acceso a las funcionalidades | — |
| [`Html/formulario.html`](Html/formulario.html) | Encuesta de opinión sobre Raphinha | localStorage |
| [`Html/votos.html`](Html/votos.html) | Muestra los votos guardados en el navegador | localStorage |
| [`Html/jugadores.html`](Html/jugadores.html) | CRUD de jugadores del Barça | Firestore |

## Validaciones

Los formularios validan sus campos en el cliente (JavaScript) antes de guardar:

**Formulario de opinión**
- **ID**: debe ser un RUT chileno válido (verifica el dígito verificador, Ej: `12345678-9`), acepta puntos y guion.
- **Nombre**: solo letras (incluye tildes y ñ), mínimo 3 caracteres.
- **Elección**: obligatoria (Sí / No).
- **Motivo**: mínimo 10 caracteres.

**CRUD de jugadores**
- **Nombre**: solo letras, entre 3 y 60 caracteres.
- **Posición**: solo letras, entre 2 y 60 caracteres.
- **Dorsal**: número entero entre 1 y 29, y que no esté repetido entre los jugadores ya guardados en Firestore.
- **Nacionalidad**: solo letras, entre 3 y 60 caracteres.

Los campos inválidos se marcan en rojo con un mensaje de ayuda que desaparece al corregirlos.

## Tecnologías

- HTML5, CSS3 y JavaScript (Vanilla JS)
- [Firebase / Firestore](https://firebase.google.com/) (Base de Datos como Servicio)
- Web Storage API (`localStorage`)
- GitHub Pages (hosting estático)

## Cómo ejecutar el proyecto

1. Clona el repositorio:
   ```bash
   git clone https://github.com/Salmon5g/Cloud_Computing.git
   ```
2. Abre `index.html` en tu navegador (o ábrelo con Live Server de VS Code).
3. Para el módulo de Firestore (`jugadores.html`) necesitas conexión a internet; Firestore usa las credenciales configuradas en el archivo.

También está disponible online en GitHub Pages:
<https://salmon5g.github.io/Cloud_Computing/>

## Estructura del proyecto

```
Cloud_Computing/
├── index.html              # Redirección a Html/index.html
├── README.md
├── Css/
│   └── style.css           # Estilos compartidos
└── Html/
    ├── index.html          # Página de inicio
    ├── formulario.html     # Encuesta (localStorage)
    ├── votos.html          # Votos guardados (localStorage)
    └── jugadores.html      # CRUD Jugadores (Firestore)
```

## Nota de seguridad

El `apiKey` de Firebase se expone en el cliente porque así es como funcionan las aplicaciones web con Firebase. La seguridad de los datos depende de las **reglas de seguridad de Firestore** (`Security Rules`), que deben restringir lecturas y escrituras solo a documentos y usuarios autorizados. No se debe dar por segura la base de datos por el simple hecho de tener una API key.

## Autor

Proyecto académico — Instituto Profesional Santo Tomás, 2026.