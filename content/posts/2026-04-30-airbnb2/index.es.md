---
title: "¿Se debe regular Airbnb? Parte 2"
date: 2026-04-27
draft: false
summary: "Un breve análisis de la situación de las rentas a corto plazo en Ecuador y algunas ideas para su regulación."
tags: ["GIS", "geography", "short-term retanls", "Airbnb"]
---

En mi post anterior presenté algunas reflexiones sobre el tema de la regulación de las rentas de corto plazo en Ecuador. En esta ocasión me centraré más en cómo obtener y analizar los datos que permitan una eficiente regulación de este tipo de actividades. Antes de eso, quisiera aclarar algunas razones por las que se debe regular esta actividad. 

El informe ["The Threat of Short-TermRentals to Housing:A Critical Perspective onAirbnb’s Global Expansion"](https://insideairbnb.com/reports/the-threat-of-short-term-rentals-to-housing-en.pdf) elaborado por [Inside Airbnb](https://insideairbnb.com/) y el Housing Justice Data Lab detalla cómo las plataformas de alquiler a corto plazo han pasado de ser sitios web de 'alquiler entre particulares' a convertirse en amenazas sistémicas para la estabilidad de la vivienda a nivel mundial. Analizando datos de más de 200 países, los autores encontraron que el predominio de los anuncios de viviendas completas sin anfitrión (unhosted entire-home listings) retira millones de unidades del mercado residencial a largo plazo. Cada vez existen más operadores comerciales y no residentes locales detrás de los anuncios. Esto eleva los costes de la vivienda y agrava la desigualdad urbana, especialmente en el Sur Global. Además, analizan cómo los grandes eventos internacionales y la falta de una regulación gubernamental eficaz aceleran el fenómeno. Es así que sugieren elaborar herramientas políticas estrictas, como los requisitos de residencia principal y el registro obligatorio, para proteger a las comunidades locales del desplazamiento[^1].

De aquí, podemos extraer 2 elementos para el análisis de los datos:

1. El tipo de propiedad que se anuncia: cuarto vs. propiedad entera
2. El tipo de anunciante: anfitrión vs. comercial

El primero puede ser extraído directamente de la plataforma de Airbnb que incluso ofrece esta opció como filtro de búsqueda. El segundo, puede ser un poco más complicado de identificar puesto que los anunciantes comerciales pueden ofrecer propiedades bajo diferentes nombres o bajo el nombre de una empresa. Es aquí precisamente que el registro ante una autoridad gubernamental es fundamental ya que se puede, no solo verificar la autenticidad del anunciante sino su relación con la propiedad ofertada. 

Veamos un ejemplo de como obtener y analizar los datos. Analizaremos el panorama de rentas de corto plazo en la Isla de Santa Cruz en Galápagos. 
Las Galápagos son un caso de estudio particular por x razones. Primero, dado su estatus de protección como Parque Nacional, tiene muchas regulaciones especiales que buscan limitar el número de residentes y de turistas en las islas. Segundo, la principal actividad económica desde hace varias décadas es el turismo, lo que innegablemente puede ser contradictorio frente a los objetivos de conservación. Tercero, al ser una isla alejada del continente, muchos de los recursos son escasos y costosos, entre ellos el acceso al agua potable, la generación de energía eléctrica e incluso los alimentos. 

## Obtener los datos

Aunque la API de Airbnb no está disponible al público, existen algunas alternativas para extraer los datos. La primera, es una serie de proveedroes de datos externos como AirROI o Apify[^2]. Estas dos ofrecen los datos de Airbnb por un pago aunque también tienen algunas opciones gratuitas de visualización de los datos. La segunda opción es extraer los datos con webscrappers abiertos usando python u otro lenguage de programación. Para esto se puede usar pyairbnb o ScrapeBnB. 

{{< alert >}}
Usar un webscrapper para extraer los datos de Airbnb viola sus políticas del servicio. No obstante, dependiendo del uso que se de a los datos, no constituye una actividad ilegal.
{{< /alert >}}

## Análisis de las tendencias

Según los datos de AirROI, en Puerto Ayora la oferta de propiedades en Airbnb ha fluctuado entre 200 y 420 en los ultimos 3 años. Al relizar una búsqueda en la plataforma de Airbnb, la cifra de propiedades disponibles para 5 noches durante el mes de mayo 2026 es de 421. En el gráfico se puede ver como la oferta de propiedades ha ido en aumento desde julio del 2024 aunque parece haberse estabilizado en los primeros meses de 2026. Esto es particularmente interesante ya que, a partir de mayo de 2025 el Ministerio de Turismo de Ecuador inició actividades de control en cumplimiento de la Ley Orgánica de Régimen Especial para la Provincia de Galápagos - LOREG. Esta ley, en su artículo 72 prohibe la construcción de nueva infraestructura hotelera y, en su artículo 102, establece sanciones para nuevas construcciones o ampliaciones de la infraestructura existente que on cumpla con lo previsto en Plan de Regulación Hotelera (aprobado en junio de 2024). Se esperaría entonces que a partir de esa fecha el número de anuncios en Airbnb disminuya. 

{{< figure src="img/trend.png" alt="captura de pantalla de AirROI" caption="Tendencia de anuncios en Airbnb desde mayo 2023 a marzo 2026 tomada de AirROI, consultado el 28 de abril de 2026" >}}

<div style="max-width: 400px; margin: 0 auto;">
{{< x user="minturgalapagos" id="1923478044527689776" >}}
</div>

Esta es una de las ventajas de los proveedores de datos externos como AirROI, el poder consultar una serie histórica y realizar cálculos cmoparativos entre las propiedades anunciadas y las propiedades reservadas. En el siguiente gráfico, por ejemplo, se puede observar la evolución del total de ingresos mensuales que generan las propiedaes según tipo. Se pueden observar las variaciones estacionales con picos en los meses de junio, julio y agosto. Ahora bien, es interesante ver como el ingreso total para el mes de abril de 2025, luego de las regulaciones, es más del doble del ingreso total para el mismo mes del año anterior. 

{{< figure src="img/revenue.png" alt="captura de pantalla de AirROI" caption="Tendencia de ingresos totales por tipo de propiedad desde mayo 2023 a marzo 2026 tomada de AirROI, consultado el 28 de abril de 2026" >}}

Esto quiere decir que aunque el número total de anuncios comparados con los meses previos a los controles parece haber disminuido (de 415 en julio 2025 a 362 en marzo de 2026), los ingresos que se han percibido son mayores. Es decir que la aparente dsminución en oferta puede haber causado un incremento en los precios de oferta de los anuncios o en la cantidad efectiva de propiedades rentadas al mes. Recordemos que no todas las propiedades anunciadas se rentan, la ocupación es de alrededor del 20% para el mes de abril 2026. 

## Análisis del tipo de propiedades

Otro punto interesante para el análisis, como ya mencioné, es el tipo de propiedad que se oferta. Los datos de AirROI muestran que en Santa Cruz el 60% de anuncios son de propiedades completas y el 36% de habitaciones. Aunque no se puede asumir que el total de las rentas de la propiedad completa son ofertadas por anunciates comerciales, este fenómeno si puede afectar de manera general la oferta de vivienda, como lo sostiene el informe de InsideAirbnb.

<div style="max-width: 60%; margin: 0 auto;">
{{< figure src="img/types.png" alt="captura de pantalla de AirROI" caption="Proporción de anuncios por tipo de propiedad ofertada en Airbnb desde mayo 2023 a marzo 2026 tomada de AirROI, consultado el 28 de abril de 2026" >}}
</div>

A partir de esto se puede asumir que debido a la no regulación de esta actividad en Puerto Ayora existen 239 viviendas que no están disponibles para los habitantes locales en promedio entre 2023 y 2026. Segun el Censo de 2020[^3], en Puerto ayora existen 5888 viviendas particulares. Es decir que, Airbnb está ocupando un 4% de las viviendas en la parroquia. 

Ahora bien, realizando una búsqueda directa en Airbnb para las primeras cinco noches del mes de mayo de 2026, encontramos que existen 855 propiedades disponibles. De estas, 417 son rentas de la propiedad entera, representando el 7% de el stock de vivienda total. 

<div style="max-width: 60%; margin: 0 auto;">
{{< figure src="img/types2.png" alt="captura de pantalla de AirROI" caption="Proporción de anuncios por tipo de propiedad ofertada en Airbnb para los primeros días de abril 2026" >}}
</div>

El número no parece tan abrumador pero, hay que considerar que, de ser así, en Santa Cruz existe una presión y captura de la oferta de vivienda por parte de Airbnb similar a la que se identifica en mercados de alta presión y profunda saturación en América Latina donde más del 60% de los anuncios son de propiedades completas a la renta. 

## Distribución de la oferta y saturación profunda "deep saturation"

La "saturación profunda" (en inglés, deep saturation) se refiere a una concentración extrema de anuncios de alquiler a corto plazo en escalas espaciales muy pequeñas, como barrios o manzanas específicas. Este fenómeno se hace visible cuando se analizan los datos a nivel local, revelando áreas donde la vivienda residencial ha sido absorbida casi por completo para fines turísticos. En algunas ciudades se evidencia una hiper concentración de propiedades en barrios o zonas de alto valor turístico. Esto, sin duda, puede ser un factor incidente en la denominada 'turistificación', que provoca el desplazamiento y exclusión de la población local en estas zonas. 

Para identificar esta saturación, es necesario analizar la localización de las propiedades anunciadas y consecuentemente se requiere que los datos tengan esta información. Las fuentes o formas de extraer datos antes presentadas hacen posible visualizar la localización de las propiedades porque contienen las coordenadas de las mismas. 

En el siguiente mapa se puede ver como en el caso de Puerto Ayora, existe una concentración notable de anuncios, especialmente de propiedades completas en alquiler, concentrado hacia la zona de la bahía ya se esta es la zona más atractiva al turismo por su cercanìa al mar, al muelle, a los comercios. Este mapa fue construido con los datos extraidos directamente de Airbnb realizando una consulta de propiedades disponibles para los cinco primeros días del mes de abril de 2026. El mapa es interactivo y permite filtrar la vista por el tipo de propiedad, en la ventana de la izquierda muestra el totla de propiedades por tupo, el rango de precios por noche y la valoración de huéspedes anteriores. Herramientas como estas que permitan, no solo visualizar el fenómeno sino monitorearlo en el tiempo son escenciales para la formulación y aplicación de políticas de regulación eficientes. Se puede construir sobre una herramienta de este tipo añadiendo, por ejemplo, los precios de la vivienda de alquiler en la isla, la infraestructura, la estructura socio-demográfica, entre otras.


{{< figure src="img/map_airbnb.png" alt="captura de pantalla de AirROI" caption="Mapa interactivo de anuncios de Airbnb en Puerto Ayora para abril 2026 por tipo." >}}

Pueden ver una versión interactiva del mapa aquí. 


{{< button href="https://fmvaldezg.codeberg.page/ptoayora-abb2026/airbnb_map.html" target="_blank" >}}
Ver mapa
{{< /button >}}

## Conclusiones

En los dos post anteriores he intentado mostrar la utilidad de usar datos para informar las políticas de regulación de las rentas de corta estancia. Entonce, ¿Se debe regular Airbnb? Definitivamente se debe regular una actividad de este tipo que, aunque pueda presentarse como una oportunidad para complementar los ingresos de la poblaicón local, existe evidencia suficiente de que al ser tan lucrativa termina siendo captada por grandes capitales. Es así que, al mediano y largo plazo, la no regulación de esta actividad puede terminar siendo mucho más perjudicial para la población local que lo que ahora parece ser la aplicación de la misma. 

Ahora bien, es muy importante que la regulación apunte seriamente a proteger el bienestar de la gran mayoría, por ejemplo evitando el incremento en el precio de las rentas o el crecimiento descontrolado del número de visitantes. Por eso, esta regulación debe, por un lado, responder al análksis específico del fenómeno en el ámbito local y, por otro, debe complementarse con otras políticas de regulación de otros aspectos espaciales como la habilitación de suelo urbano, control de construcciones, proyección de servicios básicos, entre otros. 

## Referencias

[^1]: [Cruvinel, A., & Cox, M. (2026, March). The Threat of Short-Term Rentals to Housing: A Critical Perspective on Airbnb’s Global Expansion. Housing Justice Data Lab / Inside Airbnb.](https://insideairbnb.com/reports/the-threat-of-short-term-rentals-to-housing-en.pdf)

[^2]: [Zhou, J. (2026, February 2). Is it legal to scrape Airbnb data?. AirROI. https://www.airroi.com/blog/is-it-legal-to-scrape-airbnb-data ](https://www.airroi.com/blog/is-it-legal-to-scrape-airbnb-data).

[^3]: INEC, VIII Censo de Población y VII de Vivienda 2022. 