---
title: Creación de contido en Markdown
description: Unha descripción xeral da sintaxe Markdown que soporta Starlight.
---

Starlight admite a gama completa da sintaxe [Markdown](https://daringfireball.net/projects/markdown/) en arquvos `.md`, así coma o frontmatter en [YAML](https://dev.to/paulasantamaria/introduction-to-yaml-125f) para definir metadatos coma o título e a descrición.

Por favor, asegúrate de consultar a documentación de [MDX](https://mdxjs.com/docs/what-is-mdx/#markdown) ou [Markdoc](https://markdoc.dev/docs/syntax) se estás utilizando eses formatos de arquivo, xa que o soporte e o uso de Markdown poden variar.

## Estilos en liña

O texto pode estar **en negriña**, _en cursiva_, ou ~~tachado~~.

```md
O texto pode estar **en negriña**, _en cursiva_, ou ~~tachado~~.
```

Podes [enlazar a otra página](/es/getting-started/).

```md
Podes [enlazar a otra página](/es/getting-started/).
```

Podes resaltar `código en línea` con comillas invertidas.

```md
Podes resaltar `código en línea` con comillas invertidas.
```

## Imágenes

Las imágenes en Starlight utilizan el [soporte de assets optimizados incorporado en Astro](https://docs.astro.build/en/guides/assets/).

Markdown y MDX admiten la sintaxis Markdown para mostrar imágenes, que incluye alt-text para lectores de pantalla y tecnología de asistencia.

![Una ilustración de planetas y estrellas con la palabra “astro”](https://raw.githubusercontent.com/withastro/docs/main/public/default-og-image.png)

```md
![Una ilustración de planetas y estrellas con la palabra “astro”](https://raw.githubusercontent.com/withastro/docs/main/public/default-og-image.png)
```

También se admiten rutas de imágenes relativas para imágenes almacenadas localmente en tu proyecto.

```md
// src/content/docs/page-1.md

![Una nave espacial en el espacio](../../assets/images/rocket.svg)
```

## Encabezados

Podes estructurar el contenido utilizando encabezados. Los encabezados en Markdown se indican con uno o más `#` al comienzo de la línea.

### Cómo estructurar el contenido de la página en Starlight

Starlight está configurado para utilizar automáticamente el título de tu página como un encabezado de nivel superior y se incluirá un encabezado "Visión general" en la parte superior de la tabla de contenido de cada página. Recomendamos comenzar cada página con contenido de texto de párrafo regular y utilizar encabezados dentro de la página a partir de `<h2>` en adelante:

```md
---
title: Guía de Markdown
description: Cómo utilizar Markdown en Starlight
---

Esta página describe cómo utilizar Markdown en Starlight.

## Estilos en línea

## Encabezados
```

### Enlaces de anclaje automáticos para encabezados.

Al utilizar encabezados en Markdown, se generan automáticamente enlaces de anclaje para que puedas vincular directamente a ciertas secciones de tu página:

```md
---
title: Mi página de contenido
description: Cómo utilizar los enlaces de anclaje integrados de Starlight.
---

## Introducción

Puedo enlazar a [mi conclusión](#conclusión) más abajo en la misma página.

## Conclusión

`https://mi-sitio.com/page1/#introduction` navega directamente a mi Introducción.
```

Los encabezados de nivel 2 (`<h2>`) y nivel 3 (`<h3>`) aparecerán automáticamente en la tabla de contenido de la página.

## Apartados

Los apartados (también conocidos como “apartados” o ”contenido destacado”) son útiles para mostrar información secundaria junto al contenido principal de una página.

Starlight proporciona una sintaxis personalizada de Markdown para renderizar apartados. Los bloques de apartados se indican utilizando un par de triples dos puntos `:::` para envolver tu contenido, y poden ser de tipo `note`, `tip`, `caution` o `danger`.

Podes anidar cualquier otro tipo de contenido Markdown dentro de un apartado, pero los apartados son más adecuados para fragmentos de contenido cortos y concisos.

### Nota de apartados

:::note
Starlight es un conjunto de herramientas para crear sitios web de documentación construido con [Astro](https://astro.build/). Podes comenzar con este comando:

```sh
npm run create astro@latest --template starlight
```

:::

````md
:::note
Starlight es un conjunto de herramientas para sitios de documentación construido con [Astro](https://astro.build/). Podes comenzar con este comando:

```sh
npm run create astro@latest --template starlight
```

:::
````

### Títulos personalizados para los apartados

Podes especificar un título personalizado para el apartado utilizando corchetes cuadrados después del tipo del apartado, por ejemplo, `:::tip[¿Sabías esto?]`.

:::tip[¿Sabías esto?]
Astro te ayuda a construir sitios web más rápidos con la[“Arquitectura de Islas”](https://docs.astro.build/es/concepts/islands/).
:::

```md
:::tip[¿Sabías esto?]
Astro te ayuda a construir sitios web más rápidos con la[“Arquitectura de Islas”](https://docs.astro.build/es/concepts/islands/).
:::
```

### Máis tipos de apartados

Os apartados de caution y danger son útiles para llamar la atención del usuario sobre detalles que podrían generar problemas. Si te encuentras utilizando estos tipos de apartados con frecuencia, también pode ser una señal de que lo que estás documentando podría beneficiarse de una reestructuración o rediseño.

:::caution
Si no estás seguro de si deseas un sitio de documentación increíble, piénsalo dos veces antes de usar [Starlight](../../).
:::

:::danger
Tus usuarios poden ser más productivos y encontrar más fácil de usar tu producto gracias a las útiles características de Starlight.

- Navegación clara
- Tema de color configurable por el usuario
- [Soporte de i18n](/guides/i18n)

:::

```md
:::caution
Si no estás seguro de si deseas un sitio de documentación increíble, piénsalo dos veces antes de usar [Starlight](../../).
:::

:::danger
Tus usuarios poden ser más productivos y encontrar más fácil de usar tu producto gracias a las útiles características de Starlight.

- Navegación clara
- Tema de color configurable por el usuario
- [Soporte de i18n](/guides/i18n)

:::
```

## Citas en bloque

> Esto es una cita en bloque, que se utiliza comúnmente para citar a otra persona o documento.
>
> Las citas en bloque se indican con un `>` al inicio de cada línea.

```md
> Esto es una cita en bloque, que se utiliza comúnmente para citar a otra persona o documento.
>
> Las citas en bloque se indican con un `>` al inicio de cada línea.
```

## Bloques de código

Un bloque de código se indica con un bloque de tres comillas invertidas <code>```</code> al inicio y al final. Podes indicar el lenguaje de programación que se está utilizando después de las comillas invertidas de apertura.

```js
// Código JavaScript con resaltado de sintaxis.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l);
  return true;
};
```

````md
```js
// Código JavaScript con resaltado de sintaxis.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l);
  return true;
};
```
````

```md
Los bloques de código largos de una sola línea no deben ajustarse automáticamente. Deben desplazarse horizontalmente si son demasiado largos. Esta línea debe ser lo suficientemente larga para demostrar esto.
```

## Otras características comunes de Markdown

Starlight admite todas as demais sintaxes de autoría de Markdown, como listas e táboas. Podes consultar a [Guía de referenza de Markdown](https://www.markdownguide.org/cheat-sheet/) para obter unha descripción xeral rápida de todos os elementos de sintaxe de Markdown.
