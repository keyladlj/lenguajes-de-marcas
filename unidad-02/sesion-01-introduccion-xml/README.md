# Sesión 1. Introducción práctica a XML

**Módulo:** Lenguajes de Marcas y Sistemas de Gestión de Información  
**Curso:** 1.º DAW · 2026-2027  
**Alumna:** Keyla de León Jacinto

> Esta es mi primera actividad trabajando con XML. Por eso he intentado explicar los conceptos con palabras sencillas y comprobar los documentos paso a paso.

## 1. Preparación del entorno

He utilizado Visual Studio Code y la extensión **XML de Red Hat** (`redhat.vscode-xml`) para trabajar con los archivos XML y detectar errores.

La captura de la extensión instalada debe guardarse como:

`img/01-extension-xml.png`

## 2. Investigación inicial

### 2.1 ¿Qué significa XML?

XML significa **eXtensible Markup Language**, es decir, **Lenguaje de Marcado Extensible**. Es un lenguaje que permite organizar información mediante etiquetas. Una de sus características es que podemos crear etiquetas que tengan sentido para los datos que queremos guardar. MDN explica que XML no tiene un conjunto fijo de etiquetas como HTML, sino que permite definir las propias. [MDN, Introducción a XML](https://developer.mozilla.org/es/docs/Web/XML/Guides/XML_introduction)

### 2.2 ¿Por qué es extensible?

Es extensible porque podemos crear nuestras propias etiquetas según la información que necesitemos representar. Por ejemplo, para una película puedo utilizar `<titulo>`, `<director>` o `<genero>`.

### 2.3 Diferencia entre XML y HTML

HTML se utiliza principalmente para estructurar el contenido de las páginas web. XML se utiliza para representar y organizar información de forma estructurada. Aunque ambos utilizan etiquetas, XML permite crear etiquetas propias. [MDN, XML](https://developer.mozilla.org/es/docs/Glossary/XML)

### 2.4 Tres usos de XML

Algunos usos de XML son:

1. **Intercambiar información** entre diferentes programas o sistemas.
2. **RSS**, que utiliza XML para organizar información que puede distribuirse.
3. **Configuración y almacenamiento estructurado** de información de diferentes aplicaciones.

### 2.5 ¿Puede leerlo una persona y una máquina?

Sí. Una persona puede entender el significado de las etiquetas y un programa puede interpretar la estructura del documento. Por ejemplo:

```xml
<titulo>Harry Potter</titulo>
```

Una persona entiende que el dato es un título y un programa puede localizar ese dato dentro de la estructura XML.

### 2.6 ¿XML es una base de datos?

No. Un archivo XML puede guardar información organizada, pero eso no significa que sea una base de datos. XML es un formato para representar datos. Una base de datos utiliza sistemas específicos para almacenar y gestionar información.

## 3. Mi primer documento XML

El archivo `primer-documento.xml` contiene:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<videojuego>
  <titulo>Hollow Knight</titulo>
  <desarrolladora>Team Cherry</desarrolladora>
  <genero>Metroidvania</genero>
  <precio moneda="EUR">14.99</precio>
</videojuego>
```

### Elemento raíz

El elemento raíz es `<videojuego>`, porque es el elemento principal y contiene todos los demás.

### Elementos

Los elementos que aparecen son:

- `videojuego`
- `titulo`
- `desarrolladora`
- `genero`
- `precio`

### Atributo y valor

En:

```xml
<precio moneda="EUR">14.99</precio>
```

`moneda` es el atributo y `EUR` es su valor.

### Relación entre `videojuego` y `titulo`

`titulo` está dentro de `videojuego`, por lo que `titulo` es un elemento hijo de `videojuego`.

### Elementos hermanos

`titulo`, `desarrolladora`, `genero` y `precio` están dentro del mismo elemento `videojuego`, por lo que son elementos hermanos.

La captura del XML abierto en el navegador debe guardarse como:

`img/02-primer-xml.png`

## 4. Ampliación del catálogo

He ampliado el catálogo hasta **10 videojuegos**.

### ¿Por qué `plataformas` funciona como contenedor?

He utilizado `plataformas` para agrupar varias plataformas de un mismo videojuego:

```xml
<plataformas>
  <plataforma>PC</plataforma>
  <plataforma>Switch</plataforma>
</plataformas>
```

Así puedo guardar una o varias plataformas dentro del mismo videojuego.

### Diferencia entre `id` y `titulo`

El `id` identifica cada videojuego y debe ser diferente para cada uno. El `titulo` contiene el nombre que tiene el videojuego.

### Recuento

- Elementos `videojuego`: **10**
- Elementos `plataforma`: **28**
- Identificadores diferentes: **10**
- Comentario XML antes del tercer videojuego: **sí**

### Modificaciones realizadas

- Añadí 8 videojuegos al catálogo inicial.
- Asigné un `id` diferente a cada videojuego.
- Añadí plataformas.
- Añadí precios con moneda.
- Añadí algunas descripciones opcionales.
- Añadí un comentario antes del tercer videojuego.

## 5. Laboratorio de errores

Antes de corregir el archivo, el código proporcionado tenía varios errores:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<equipo nombre="Vengadores">
  <heroe id=H01>
    <alias>Iron Man</Alias>
    <nombre>Tony Stark</nombre>
    <habilidad>Tecnología & estrategia</habilidad>
  </heroe>
  <heroe id="H02">
    <alias>Capitana Marvel</alias>
    <nombre>Carol Danvers
  </heroe>
</equipo>
```

La captura de los errores detectados antes de corregirlos debe guardarse como:

`img/03-error-xml.png`

### Errores encontrados

| Error detectado | Regla que incumple | Corrección |
|---|---|---|
| `id=H01` no tiene comillas | Los valores de los atributos deben ir entre comillas | `id="H01"` |
| `<alias>` termina como `</Alias>` | XML distingue mayúsculas y minúsculas | `</alias>` |
| Aparece `&` directamente | `&` es un carácter reservado | `&amp;` |
| `<nombre>Carol Danvers` no está cerrado | Todos los elementos deben cerrarse | `</nombre>` |

### Archivo corregido

El archivo `errores.xml` contiene la versión corregida y ya está bien formada.

## 6. Actividad final independiente

### Tema elegido

He elegido **películas y series** porque es un tema que conozco y me resulta fácil pensar qué información quiero guardar.

### ¿Qué representa?

El documento representa una pequeña colección de películas y series. Cada contenido tiene un identificador, un título, un tipo y otros datos que pueden variar según sea una película o una serie.

### Árbol

```text
peliculas-series
├── contenido
│   ├── titulo
│   ├── tipo
│   ├── generos
│   │   ├── genero
│   │   └── genero
│   ├── director
│   ├── reparto
│   │   ├── actor
│   │   ├── actor
│   │   └── actor
│   ├── año
│   └── descripcion
├── contenido
│   ├── titulo
│   ├── tipo
│   ├── generos
│   ├── creadores
│   │   ├── creador
│   │   └── creador
│   ├── reparto
│   └── temporadas
└── contenido
    ├── titulo
    ├── tipo
    ├── generos
    ├── director
    ├── reparto
    └── año
```

### Código completo

El código completo está en `actividad-final.xml`.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<peliculas-series>

  <!-- Colección de películas y series para practicar XML -->

  <contenido id="P001">
    <titulo>Harry Potter y la piedra filosofal</titulo>
    <tipo>Película</tipo>
    <generos>
      <genero>Fantasía</genero>
      <genero>Aventura</genero>
    </generos>
    <director>Chris Columbus</director>
    <reparto>
      <actor>Daniel Radcliffe</actor>
      <actor>Emma Watson</actor>
      <actor>Rupert Grint</actor>
    </reparto>
    <año>2001</año>
    <descripcion>Una historia de magia &amp; aventuras.</descripcion>
  </contenido>

  <contenido id="P002">
    <titulo>Stranger Things</titulo>
    <tipo>Serie</tipo>
    <generos>
      <genero>Ciencia ficción</genero>
      <genero>Misterio</genero>
    </generos>
    <creadores>
      <creador>Matt Duffer</creador>
      <creador>Ross Duffer</creador>
    </creadores>
    <reparto>
      <actor>Millie Bobby Brown</actor>
      <actor>Finn Wolfhard</actor>
      <actor>Winona Ryder</actor>
    </reparto>
    <temporadas>5</temporadas>
  </contenido>

  <contenido id="P003">
    <titulo>El señor de los anillos: La comunidad del anillo</titulo>
    <tipo>Película</tipo>
    <generos>
      <genero>Fantasía</genero>
      <genero>Aventura</genero>
    </generos>
    <director>Peter Jackson</director>
    <reparto>
      <actor>Elijah Wood</actor>
      <actor>Ian McKellen</actor>
      <actor>Orlando Bloom</actor>
    </reparto>
    <año>2001</año>
  </contenido>

</peliculas-series>
```

### Decisiones de diseño

| Dato | Elemento o atributo | Justificación |
|---|---|---|
| Identificación | `id` | Cada contenido necesita un identificador diferente. |
| Tipo de contenido | `tipo` | Permite indicar si es una película o una serie. |
| Géneros | `generos` + `genero` | Permite guardar varios géneros para un mismo contenido. |
| Actores | `reparto` + `actor` | Permite guardar varios actores. |
| Director | `director` | Guarda el nombre del director cuando corresponde. |

### Elemento opcional

He utilizado `descripcion` como elemento opcional. No aparece en todos los registros. De esta forma puedo comprobar que no todos los registros tienen que contener exactamente la misma información.

### Recuento

- Registros principales: **3**
- Atributos `id`: **3**
- Nombres de elementos diferentes: **14**
- Colecciones internas repetidas: `generos`, `reparto` y `creadores`
- Comentario XML: **1**
- Texto con `&amp;`: **1**

La captura del documento final debe guardarse como:

`img/04-actividad-final.png`

## 7. Revisión final

Antes de entregar comprobaré:

- [ ] `README.md` terminado.
- [ ] `primer-documento.xml` bien formado.
- [ ] `catalogo-ampliado.xml` con 10 videojuegos.
- [ ] `errores.xml` corregido.
- [ ] `actividad-final.xml` bien formado.
- [ ] Extensión XML de Red Hat instalada.
- [ ] `01-extension-xml.png` realizada.
- [ ] `02-primer-xml.png` realizada.
- [ ] `03-error-xml.png` realizada antes de corregir los errores.
- [ ] `04-actividad-final.png` realizada.
- [ ] Fuentes consultadas enlazadas.
- [ ] Cambios subidos a GitHub.

## 8. Fuentes consultadas

- [MDN Web Docs — Introducción a XML](https://developer.mozilla.org/es/docs/Web/XML/Guides/XML_introduction)
- [MDN Web Docs — XML](https://developer.mozilla.org/es/docs/Glossary/XML)

## 9. Entrega con Git

Cuando todos los archivos y capturas estén terminados:

```bash
git status
```

Después:

```bash
git add unidad-02/sesion-01-introduccion-xml
```

```bash
git commit -m "Completa la sesión inicial de XML"
```

```bash
git push
```

Por último:

```bash
git status
```

El resultado esperado es:

```text
nothing to commit, working tree clean
```

La entrega final será el enlace de la carpeta de la sesión en GitHub.
