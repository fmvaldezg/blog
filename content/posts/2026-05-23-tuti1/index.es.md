---
title: "La estrategia de los supermercados TuTi en Ecuador"
date: 2026-05-24
draft: false
summary: "Un análisis de las fuentes de los datos de los supermercados TuTi en Ecuador. Se comparan los datos disponibles en OpenStreetMap, OvertureMaps y la web oficial de la cadena."
tags: ["GIS", "geography", "open data", "supermarkets"]
---

TuTi, es una cadena de supermercados de descuentos que opera en Ecuador desde inicios del 2020. Está bajo la corporación El Rosado que tiene a su vez otras cadenas de supermercados dentro de su conglomerado: HiperMarket, Mi Comisariato y Mini. 

Esta cadena en particular se ha vuelto famosa no solo por su expansión rápida sino por su agresiva estrategia [^1]. Con más de 800 locales a nivel nacional en 2026, TuTi se caracteriza por alquilar locales comerciales de tamaño perqueño y mediano. Esta estrategia, según algunos expertos, ha provocado la desaparición de las tiendas de barrio. 

Pero, ¿están mapeados todos los locales? ¿dónde se localizan y cómo han impactado en las tiendas de barrio?

Aquí, analizamos 3 fuentes de datos que pueden reflejar este fenómeno: OpenStreetMap, OvertureMaps y la página oficial de TuTi.

## La estrategia de TuTi

Según algunos expertos[^2][^3], la estrategia que le ha permitido a TuTi crecer de manera extraordinariamente rápida se enfoca la venta de grandes volumenes a precios bajos. Esto es posible gracias a muchas acciones como el tamaño de sus locales, las marcas de productos ofertados, el pago exclusivamente en efectivo, entre otras. 

Desde un punto de vista espacial, esta estrategia tiene como ejes:

1. Alquiler de locales pequeños sin servicios adicionales como parqueaderos.
2. Proximidad a áreas con mayor densidad de población.
3. No vender productos frescos como frutas y legumbres.
4. Una oferta limitada de productos con marcas propias.

Las dos primras son las más significativas en téminos espaciales. En primer lugar, el alquiler de locales comerciales genera una dinámica de precios en barrios y zonas de las ciudades donde antes no existía un actor corporativo tan grande. Esto peude afectar, a su vez, los precios de alquiler de locales comerciales. Por otro lado, la estrategia misma de localización de los supermercados, mucho más cerca de donde se ubica la demanda masiva, a diferencia de los grandes supermercados afecta directamente a las tiendas de barrio [^4][^5]. Ya en 2023, Gabriela Coba de Primicias, realizaba un interesante análisis de la estrategia de TuTi y la presencia de otras cadenas de supermercados en el Ecuador [^6].

Para un análisis del impacto que genera TuTi en las tiendas de barrio en el la economía local, es necesario contar con datos que contengan la localización de los locales de manera desagregada, es decir, no solamente la sumatoria de locales a nivel provincial o cantonal, sino sus coordenadas o direcciones específicas. 

A continuación, analizo la disponibilidad de esta información en tres fuentes: OpenStreetMap, OvertureMaps y la web de TuTi.

## TuTi en OpenStreetMap

[OpenStreetMap](www.osm.org) es un mapa colaborativo mundial que ofrece datos de manera abierta y gratuita para su uso. Los datos son añadidos y actualizados por la comunidad de usuarios. Se peude acceder a los datos de OSM directamente desde su web, donde se conculta en un mapa interactivo al estilo Google Maps. Existen otras herramientas para realizar consultas complejas. Overpass turbo es una de esas herramientas. Permite consultar los datos de la base de datos de manera efectiva y descargar o usar los datos en diferenetes formatos. 

Asi, en [Overpass Turbo](overpass-turbo.eu) se puede usar un 'query' como este para obtener todos los supermercados en Ecuador con nombre TuTi.

```html
[out:json][timeout:300];
area["ISO3166-1"="EC"][admin_level=2]->.ec;
nwr[shop=supermarket]["name"~"^tuti",i](area.ec);
out center;
```

| Provincia  | Número de locales Tuti |
|------------|-----------:|
| Guayas     |         57 |
| Pichincha  |         25 |
| Manabí     |         12 |
| Azuay      |          6 |
| Carchi     |          5 |
| Cotopaxi   |          2 |
| Los Ríos   |          4 |
| Imbabura   |          3 |
| Bolívar    |          2 |
| Tungurahua |          2 |
| Chimborazo |          2 |
| Napo       |          1 |
| **Total**  |    **121** |

<iframe title="TuTi en OpenStreetMap" aria-label="Mapa coroplético" id="datawrapper-chart-dr0hC" src="https://datawrapper.dwcdn.net/dr0hC/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="531" data-external="1"></iframe><script type="text/javascript">(function(){function e(){window.addEventListener(`message`,function(e){if(e.data[`datawrapper-height`]!==void 0){var t=document.querySelectorAll(`iframe`);for(var n in e.data[`datawrapper-height`])for(var r=0,i;i=t[r];r++)if(i.contentWindow===e.source){var a=e.data[`datawrapper-height`][n]+`px`;i.style.height=a}}})}e()})();</script>


{{< carousel images="{img/heatmap.png,img/entirehome.png,img/hotspots.png,img/clusters.png}" aspectRatio="9-8" captions="{img/heatmap.png:Mapa de calor de los anuncios,img/entirehome.png:Localización de anuncios de propiedad completa,img/hotspots.png:Puntos calientes y fríos de precios,img/clusters.png:Clusters de concentración de anuncios}" interval="1500">}}

Ver el resultado de la consulta en un mapa 
{{< button href="https://overpass-ultra.us/#map&m=6.55/-1.8446/-78.6032&q=LQhQBcEtwGwUwFwAIAqBXKSDKaAOcAnAWwEMCBrOcAZyUgDskBRAYzRIBMB7A0XL3HgDy9ABJcAboWTgCaOHwF4UcIrhglwiJACIA3ntwEBhKHGoA6eiSJwAvnZ2gWXerK4xqCUEiTAk4ACe+MgAciQSkADmmpCuAMKu7jA+vkgCUK5eqWlIkdTsMJAAXnAACtAsABYycgq5-NTQcfQyAsAE0VXgqf5BIUgA4nAeXCyacIluxim5GS3Zub6Nza5CuJn0i0u+cNYARvCiXQCCLGwEJCyBtfI5abJX5ACq1IQAMmOxrrcK1EHwby+DSBQjbXx9YLaFiQAgseD3XwwuHwDqcSBoLxIACciKQyPhcGALhgPGQoJgpIA7niCaj-sZKMTRgRkAByADEAGYeWzabDCcAGVwmVTIBxwDUkABGe6QgbUQJEfYePGQFz0YCQUhRbS4BhVOCcBDUKoCfX0KIAfXGBB6O3VrmZpNZSEOdwdGqFJW0AAYLABWNVeySEDS4ZAkGBUkiBajBp3Reg8InqK6qPbgX6pOAADy09A4WO64FwXgA9OWSPqLEYuOAuKQyxYXERy-9AvBqOWJAHy1FLnHxvBy3sLAAraiuAD8lECAF4AGYADjgLDgRs4ADZl9ityxsQAmUAgYCgADaXAwCEnrgAuueoLYr1npb7fXeANygMhG886ABJLAhC5aUty3YBpR0ecdCYeIdAfTgiAYK14CkGB50PO9gAAPgsNdv3oKkCHPU0BHnAp8GIMhKHAB8dGsWwdAAPx0AA9cAMEgHQABpIDvAAKX8SHwlgAEpvxffFM0IT8gA" target="_blank" >}}
Ver mapa
{{< /button >}}

## TuTi en Overture Maps

[Overture Maps](https://overturemaps.org/), or el otro lado, es una inciativa de datos abiertos en la que participan las gigantes de datos como Meta, Microsoft, Amazon y TomTom. Su idea es compartir un ecosistema de datos que en lugar de generar competencia entre ellas, las unifique en un soslo esfuerzo. Overture Maps aglutina, limpia y estandariza datos de diversas fuentes (entre esas OSM). Lo más interesante es que son de acceso libre. Cuentan con una web de exploración desde la que se pueden cnosultar y descargar datos, pero tambien se lo puede hacer de manera programática.

Para este caso, se creó un script en python con el que se consultaron y descragaron los datos de supermercados cuyo nombre sea TuTi en Ecuador, usando paquetes como duckdb, geopandas y shapely. 

Sorpresivamente se obtuvieron menos resultados en OvertureMaps que en OSM. 

| Provincia  | Número de locales Tuti |
|------------|-----------:|
| Guayas     |         34 |
| Pichincha  |          4 |
| Manabí     |          7 |
| Carchi     |          5 |
| Imbabura   |          2 |
| Azuay      |          1 |
| El Oro     |          1 |
| Napo       |          1 |
| **Total**  |     **55** |

<iframe title="TuTi en Overture Maps" aria-label="Mapa coroplético" id="datawrapper-chart-uG44K" src="https://datawrapper.dwcdn.net/uG44K/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="531" data-external="1"></iframe><script type="text/javascript">(function(){function e(){window.addEventListener(`message`,function(e){if(e.data[`datawrapper-height`]!==void 0){var t=document.querySelectorAll(`iframe`);for(var n in e.data[`datawrapper-height`])for(var r=0,i;i=t[r];r++)if(i.contentWindow===e.source){var a=e.data[`datawrapper-height`][n]+`px`;i.style.height=a}}})}e()})();</script>

## TuTi en web oficial

Finalmente, está la opción de extraer los datos directamente de la web de TuTi usando un script de webscrapping. Hicimos dos procesos de extracción de la página de TuTi, uno en abril 2025 y uno en Abril 2026. Como se ve en la tabla, el número de locales pasó de 654 a 808. Es decir un incremento de más del 23% en un solo año. TuTi, ahora tiene presencia en 18 de las 24 provincias del Ecuador. Guayas y Pichincha siguen siendo las provincias de mayor concentración.

| Provincia  | Número de locales Tuti (Abril 2025) | Número de locales Tuti (2026) |
|------------|-----------:|-----------:|
| Guayas     |        227 |        273 |
| Pichincha  |        160 |        193 |
| Manabí     |         73 |         83 |
| Azuay      |          4 |         22 |
| Carchi     |          1 |          2 |
| Cotopaxi   |          7 |         13 |
| Los Ríos   |         31 |         36 |
| Imbabura   |         22 |         25 |
| Bolívar    |          6 |          7 |
| Tungurahua |         21 |         32 |
| Chimborazo |         21 |         27 |
| Napo       |          3 |          5 |
| Cañar      |          3 |          4 |
| EL Oro     |         33 |         31 |
| Esmeraldas |          4 |          5 |
| Pastaza    |          1 |          4 |
| Santa Elena|         21 |         23 |
| Santo Domingo|       16 |         23 |
| **Total**  |    **654** |    **808** |

<iframe title="Locales Tuti por provincia 2026" aria-label="Mapa coroplético" id="datawrapper-chart-Sk222" src="https://datawrapper.dwcdn.net/Sk222/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="541" data-external="1"></iframe><script type="text/javascript">(function(){function e(){window.addEventListener(`message`,function(e){if(e.data[`datawrapper-height`]!==void 0){var t=document.querySelectorAll(`iframe`);for(var n in e.data[`datawrapper-height`])for(var r=0,i;i=t[r];r++)if(i.contentWindow===e.source){var a=e.data[`datawrapper-height`][n]+`px`;i.style.height=a}}})}e()})();</script>


## Tabla resumen

| Provincia     | OSM | Overturemaps | Website 2025 | Website 2026 |
|---------------|----:|-------------:|-------------:|-------------:|
| Guayas        |  57 |           34 |          227 |          273 |
| Pichincha     |  25 |            4 |          160 |          193 |
| Manabí        |  12 |            7 |           73 |           83 |
| Los Ríos      |   4 |            0 |           31 |           36 |
| Tungurahua    |   2 |            0 |           21 |           32 |
| El Oro        |   0 |            1 |           33 |           31 |
| Chimborazo    |   2 |            0 |           21 |           27 |
| Imbabura      |   3 |            2 |           22 |           25 |
| Santa Elena   |   0 |            0 |           21 |           23 |
| Santo Domingo |   0 |            0 |           16 |           23 |
| Azuay         |   6 |            1 |            4 |           22 |
| Cotopaxi      |   2 |            0 |            7 |           13 |
| Napo          |   1 |            1 |            3 |            5 |
| Esmeraldas    |   0 |            0 |            4 |            5 |
| Pastaza       |   0 |            0 |            1 |            4 |
| Cañar         |   0 |            0 |            3 |            4 |
| Bolívar       |   2 |            0 |            6 |            7 |
| Carchi        |   5 |            5 |            1 |            2 |
| **Total**     | **121** |       **55** |        **654** |       **808** |

Aunque los datos extraídos de la web de TuTi superan ampliamente a los de las otras plataformas, estos contienen algunas inconsistencias, especialmente en las coordenadas geográficas. Esto muestra que, probablemente, no existe un proceso de verificación y control de calidad en los datos que almacena TuTi sobre sus propios locales. Fue necesario relocalizar algunos puntos de manera manual usando la dirección como referencia.

<!--El script usado para extraer los datos es este.

{{< gist "fmvaldezg" "ed386e63d063d3fdd635bacbad108fcf" >}}-->

En todo caso, con los datos obtenidos, se puede realiazr un análisis más fino de la distribución de los locales en cada ciudad y sus posibles impactos en las tiendas de barrio y la economía local. En un próximo post compartiré algunas impresiones sobre este tipo de análisis.

## Conclusiones parciales

A manera de conclusión, la fuente más confiable y completa de datos para este tipo de análisis es la página web de la empresa. A pesar de la popularidad de TuTi en Ecuador, al parecer los usuarios no han añadido a la plataforma de OSM la totalidad de locales. 

Los datos de la empresa tienen algunas incosistencias, especialmente en las coordenadas geográficas almacenadas. Con los adtos obtenidos, hemos podido crear algunas herramientas y resultados que servirán para un análisis más profundo.

## Referencias

[^1]: [Ayala Sarmiento, S. (2025, Diciembre 29). TuTi roza las 800 tiendas tras siete años de su creación en ecuador y de una expansión agresiva. Primicias.](https://www.primicias.ec/economia/empresas/tuti-locales-tienda-descuento-supermercado-santamaria-tia-112709/)

[^2]: [Almeida, C. (2025, October 22). El discounter en Ecuador: La Nueva fuerza que está reconfigurando el retail. Kantar. Shape your brand future.](https://www.kantar.com/latin-america/inspiracion/consumidor/2025/el-discounter-en-ecuador-esta-reconfigurando-el-retail )

[^3]: [Vivar Espinosa, E. (2025, March 17). El Fenómeno Tuti: ¿Cuál es su estrategia?. Forbes Ecuador.](https://www.forbes.com.ec/negocios/el-fenomeno-tuti-cual-su-estrategia-n68943 )

[^4]: [Hualca, A. (2025, Mayo 19). Tuti quiebra a las tiendas de barrio. La Naranja Ec.](https://lanaranjaec.com/tutiquiebra/)

[^5]: [Ayala, S. (2025, February 17). La inseguridad y Tuti Ponen en Terapia intensiva a las tiendas de barrio. Primicias.](https://www.primicias.ec/primicias-empresas/inseguridad-tuti-tiendas-barrio-89846/)

[^6]: [Coba, G. (2023, Septiembre 16). El Formato de Tuti desata una guerra de precios y promociones. Primicias.](https://www.primicias.ec/noticias/economia/promociones-precios-supermercados-descuentos-tuti/)

