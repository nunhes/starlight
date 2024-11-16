---
title: Documentación ecolóxica
description: Aprende como Starlight pode axudarche a construir sitios de documentación máis ecolóxicos e a reducir a túa pegada de carbono.
---

As estimacións do impacto climático da industria web oscilan entre o [2%][sf] e o [4% das emisións globais de carbono][bbc], equivalente aproximadamente ás emisións da industria da aviación. Hai moitos factores complexos no cálculo do impacto ecolóxico dun sitio web, pero esta guía inclúe algúns consellos para reducir a pegada ambiental do teu sitio de documentación.

A boa noticia é que elegir Starlight é un excelente comienzo. Según el Website Carbon Calculator, este sitio é [más limpio que el 99% de las paxinas web analizadas][sl-carbon], produciendo 0.01g de CO₂ por visita a la paxina.

## Peso da paxina

Canto máis datos transfira unha paxina web, máis recursos enerxéticos requerirá. En abril de 2023, la mediana de unha paxina web requería que un usuario descargara más de 2.000 KB, según [los datos del HTTP Archive][http].

Starlight construye paxinas que son lo más livianas posible. Por ejemplo, en unha primera visita, un usuario descargará menos de 50 KB de datos comprimidos, lo que representa solo el 2.5% da mediana del archivo HTTP. Con unha buena estrategia de almacenamiento en caché, las navegacións posteriores poden descargar tan solo 10 KB.

### Imágenes

Si bien Starlight proporciona unha buena base, las imágenes que agregas a tus paxinas de documentación poden aumentar rápidamente el peso da paxina. Starlight utiliza el [soporte de assets optimizados][assets] de Astro para optimizar las imágenes locales en tus archivos Markdown e MDX.

### Componentes UI

Los componentes construidos con frameworks UI como React o Vue poden añadir fácilmente grandes cantidades de JavaScript a unha paxina. Sin embargo, debido a que Starlight está construido sobre Astro, los componentes como estos no cargan **ningún JavaScript del lado del cliente de forma predeterminada**, gracias a las [islas de Astro][islands].

### Caché

La caché se utiliza para controlar cuánto tiempo un navegador almacena e reutiliza los datos que ha estado descargando. unha buena estrategia de caché asegura que un usuario obtenga nuevo contenido tan pronto como sea posible cuando está cambiando, pero también evita descargar innecesariamente el mismo contenido unha e otra vez cuando no ha estado cambiando.

La forma más común de configurar la caché é mediante la [cabecera HTTP `Cache-Control`][cache]. Al utilizar Starlight, podes establecer un tiempo de caché prolongado para todo lo que se encuentra en el directorio `/_astro/`. Este directorio contiene CSS, JavaScript e outros activos empaquetados que se poden almacenar en caché de forma segura para siempre, reduciendo las descargas innecesarias.

```
Cache-Control: public, max-age=604800, immutable
```

como configurar a caché depende do teu provedor de aloxamento web. Por exemplo, Vercel aplica automáticamente esta estratexia de caché sen necesidade de configuración, mentras que en Netlify podes estabrecer [cabeceiras persoalizadas][ntl-headers] engadindo un arquivo `public/_headers` ao teu proxecto:

```
/_astro/*
  Cache-Control: public
  Cache-Control: max-age=604800
  Cache-Control: immutable
```

[cache]: https://csswizardry.com/2019/03/cache-control-for-civilians/
[ntl-headers]: https://docs.netlify.com/routing/headers/

## Consumo de energía

La forma en que se construye unha paxina web pode afectar la cantidad de energía necesaria para que funcione en el dispositivo de un usuario. Al utilizar un JavaScript mínimo, Starlight reduce la cantidad de potencia de procesamiento que necesita el teléfono, la tableta o la computadora de un usuario para cargar e renderizar las paxinas.

Ten en cuenta que al agregar funcións como scripts de seguimiento de análisis o contenido pesado en JavaScript como incrustacións de video, esto pode aumentar el consumo de energía da paxina. Si necesitas analíticas, considera elegir unha opción liviana como [Cabin][cabin], [Fathom][fathom] o [Plausible][plausible]. Las incrustacións de videos de servicios como YouTube e Vimeo se poden mejorar al [cargar el video cuando haya interacción del usuario][lazy-video]. Paquetes como [astro-embed][embed] poden ser útiles para servicios comunes.

:::tip[¿Sabías esto?]
O análise e compilación de JavaScript é unha de las tareas más costosas que los navegadores deben realizar. En comparación con el renderizado de unha imagen JPEG del mismo tamaño, [el procesamiento de JavaScript pode llevar más de 30 veces más tiempo][cost-of-js].
:::

[cabin]: https://withcabin.com/
[fathom]: https://usefathom.com/
[plausible]: https://plausible.io/
[lazy-video]: https://web.dev/iframe-lazy-loading/
[embed]: https://www.npmjs.com/package/astro-embed
[cost-of-js]: https://medium.com/dev-channel/the-cost-of-javascript-84009f51e99e

## Hospedaxe

O lugar donde se hospeda unha paxina web pode ter un gran impacto en la ecología de tu sitio de documentación. Los centros de datos e las granjas de servidores poden ter un alto consumo de electricidad e un uso intensivo del agua.

Elixir un provedor de aloxamento que empregue enerxía renovable significa ter emisións de carbono máis baixas para o teu sitio. O [Directorio da Web Ecolóxica][gwb] é unha ferramenta que pode ayudarte a encontrar empresas de alojamiento.

[gwb]: https://www.thegreenwebfoundation.org/directory/

## Comparacións

Curioso por saber como se comparan outros frameworks de documentación?
Estas probas coa [Calculadora de Carbono de Sitios Web][wcc] comparan paxinas similares construidas con diferentes ferramentas.

| Framework                   | CO₂ por visita a la paxina |
| --------------------------- | -------------------------- |
| [Starlight][sl-carbon]      | 0.01g                      |
| [VitePress][vp-carbon]      | 0.05g                      |
| [Docus][dc-carbon]          | 0.05g                      |
| [Sphinx][sx-carbon]         | 0.07g                      |
| [MkDocs][mk-carbon]         | 0.10g                      |
| [Nextra][nx-carbon]         | 0.11g                      |
| [docsify][dy-carbon]        | 0.11g                      |
| [Docusaurus][ds-carbon]     | 0.24g                      |
| [Read the Docs][rtd-carbon] | 0.24g                      |
| [GitBook][gb-carbon]        | 0.71g                      |

<small>Datos recompilados o 14 de maio de 2023. Fai clic nunha ligazón para ver cifras actualizadas.</small>

[sl-carbon]: https://www.websitecarbon.com/website/starlight-astro-build-getting-started/
[vp-carbon]: https://www.websitecarbon.com/website/vitepress-dev-guide-what-is-vitepress/
[dc-carbon]: https://www.websitecarbon.com/website/docus-dev-introduction-getting-started/
[sx-carbon]: https://www.websitecarbon.com/website/sphinx-doc-org-en-master-usage-quickstart-html/
[mk-carbon]: https://www.websitecarbon.com/website/mkdocs-org-getting-started/
[nx-carbon]: https://www.websitecarbon.com/website/nextra-site-docs-docs-theme-start/
[dy-carbon]: https://www.websitecarbon.com/website/docsify-js-org/
[ds-carbon]: https://www.websitecarbon.com/website/docusaurus-io-docs/
[rtd-carbon]: https://www.websitecarbon.com/website/docs-readthedocs-io-en-stable-index-html/
[gb-carbon]: https://www.websitecarbon.com/website/docs-gitbook-com/

## Máis recursos

### Ferramentas

- [Calculadora de Carbono de Sitios Web][wcc]
- [GreenFrame](https://greenframe.io/)
- [Ecograder](https://ecograder.com/)
- [Control de Carbono WebPageTest](https://www.webpagetest.org/carbon-control/)
- [Ecoping](https://ecoping.earth/)

### Artigos e charlas

- [“Construindo unha web máis ecolóxica”](https://youtu.be/EfPoOt7T5lg), charla de Michelle Barker
- [“Estratexias de desenvolvemento web sostible dentro dunha organización”](https://www.smashingmagazine.com/2022/10/sustainable-web-development-strategies-organization/), artículo de Michelle Barker
- [“Unha web sostible para todos”](https://2021.stateofthebrowser.com/speakers/tom-greenwood/), charla de Tom Greenwood
- [“Como o contido web pode afectar ao consumo de enerxía”](https://webkit.org/blog/8970/how-web-content-can-affect-power-usage/), artigo de Benjamin Poulain e Simon Fraser

[sf]: https://www.sciencefocus.com/science/what-is-the-carbon-footprint-of-the-internet/
[bbc]: https://www.bbc.com/future/article/20200305-why-your-internet-habits-are-not-as-clean-as-you-think
[http]: https://httparchive.org/reports/state-of-the-web
[assets]: https://docs.astro.build/en/guides/assets/
[islands]: https://docs.astro.build/en/concepts/islands/
[wcc]: https://www.websitecarbon.com/
