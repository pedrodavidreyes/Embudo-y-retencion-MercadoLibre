Análisis de Embudo y Retención para MercadoLibre
Descripción del proyecto

Este proyecto analiza el comportamiento de usuarios en un flujo de conversión tipo e-commerce para MercadoLibre, con el objetivo de identificar en qué etapas del embudo se pierden más usuarios y cómo evoluciona su retención a lo largo del tiempo.

El análisis no se limita a detectar caídas: también propone acciones para mejorar la conversión y la retención mediante simulaciones, cohortes y recomendaciones ejecutivas basadas en datos.

Para el análisis se utilizaron dos datasets:

mercadolibre_funnel
mercadolibre_retention

El procesamiento principal se realizó con SQL, mientras que el reporte final y las visualizaciones fueron construidos en Excel.

Objetivo del análisis

Responder tres preguntas clave de negocio:

¿En qué etapa del embudo se pierden más usuarios?
¿Cómo varía la conversión por país?
¿Qué tan bien se retienen los usuarios a lo largo del tiempo?
Herramientas utilizadas
SQL: limpieza, transformación, CTEs, cálculo de conversiones y cohortes.
Excel: visualización, análisis final y presentación ejecutiva.
Análisis C-F-I: estructura de comunicación basada en Contexto, Hallazgo e Implicación.
Metodología

Se construyó un embudo multietapa para medir la conversión entre los principales eventos del journey del usuario:

select_item
add_to_cart
begin_checkout
add_shipping_info
add_payment_info
purchase

También se analizó la retención por cohortes en ventanas de:

D7
D14
D21
D28

Finalmente, se simuló un escenario de mejora en el drop-off para estimar el impacto potencial sobre las compras.

Análisis C-F-I
1. Embudo general de conversión
Contexto	Hallazgo	Implicación
Entre enero y agosto de 2025 se analizó la tasa de conversión entre cada etapa clave del embudo.	La conversión general fue: 76.9% en select_item, 11.0% en add_to_cart, 4.0% en begin_checkout, 2.4% en add_shipping_info, 2.1% en add_payment_info y 1.3% en purchase.	La mayor oportunidad de mejora está entre select_item y add_to_cart, donde ocurre la caída más fuerte del embudo. Optimizar esta etapa puede generar impacto en todo el flujo posterior.
2. Principal punto de fuga
Contexto	Hallazgo	Implicación
Se comparó la pérdida porcentual entre cada etapa del embudo.	La etapa con mayor caída es add_to_cart: solo el 11.0% de los usuarios que interactúan con un producto llegan a agregarlo al carrito. Esto representa un drop-off aproximado de 89% respecto a la etapa anterior.	Se recomienda priorizar mejoras en la transición de select_item a add_to_cart, reduciendo fricción, mejorando claridad del producto, confianza, precio, disponibilidad o llamados a la acción.
3. Conversión por país
Contexto	Hallazgo	Implicación
Se analizó el embudo segmentado por país para identificar diferencias de comportamiento entre mercados.	Uruguay tuvo la mayor conversión final a compra con 4.55%. México alcanzó 2.48%. En contraste, Ecuador, Colombia y Paraguay registraron 0.00% de conversión final en la muestra analizada.	Aunque todos los países muestran una caída fuerte en add_to_cart, conviene analizar prácticas o condiciones de Uruguay y México para detectar patrones replicables en mercados con menor conversión.
4. Retención por cohortes
Contexto	Hallazgo	Implicación
Se evaluó la retención de usuarios por cohortes mensuales entre enero y agosto de 2025.	La retención mantiene un patrón consistente: D7 entre 86% y 88%, D14 entre 54% y 57%, D21 entre 23% y 27%, y D28 cerca de 2% a 3%. La cohorte de agosto se considera censurada porque no tiene suficiente ventana temporal para medir todos los periodos completos.	El mayor deterioro ocurre después de D7, especialmente entre D14 y D21. Esto sugiere la necesidad de estrategias de re-engagement durante la segunda y tercera semana posterior al registro o primera interacción.
5. Retención por país
Contexto	Hallazgo	Implicación
Se comparó la retención D7, D14, D21 y D28 por país.	Perú y México tuvieron la mayor retención D28, con 3.2% y 3.1% respectivamente. Chile y Colombia tuvieron los niveles más bajos, con 1.7% y 1.6%. Sin embargo, las diferencias entre países no son muy amplias.	La similitud del patrón entre países sugiere que el problema podría estar más relacionado con el producto, la experiencia de usuario o la estrategia de reactivación que con factores específicos de cada mercado.
6. Simulación de mejora
Contexto	Hallazgo	Implicación
Se simuló una recuperación del 15% del drop-off en la etapa crítica entre select_item y add_to_cart.	La conversión de add_to_cart aumentó de 11.0% a 20.9%, lo que representa una mejora relativa aproximada de 89.8%. La conversión final a compra pasó de 1.3% a 2.4%.	Una mejora relativamente pequeña en la recuperación de usuarios perdidos puede casi duplicar las etapas posteriores del embudo. Esto refuerza que la optimización temprana del funnel puede tener un efecto multiplicador.
Principales hallazgos
La conversión general a compra fue baja: 1.3%.
La mayor caída ocurre entre select_item y add_to_cart.
Solo 11.0% de los usuarios llegan a agregar productos al carrito.
Uruguay fue el país con mejor conversión final a compra: 4.55%.
Paraguay, Ecuador y Colombia no registraron conversión final en la muestra analizada.
La retención D7 es alta, pero cae fuertemente hacia D14 y D21.
La retención D28 se mantiene baja, alrededor de 2% a 3%.
La cohorte de agosto debe interpretarse con cautela por falta de ventana temporal completa.
La simulación mostró que recuperar 15% del drop-off puede elevar add_to_cart de 11.0% a 20.9%.
Recomendaciones de negocio
1. Optimizar la etapa select_item → add_to_cart

Esta es la etapa con mayor pérdida de usuarios. Se recomienda revisar:

Claridad del botón de agregar al carrito.
Costos visibles antes del checkout.
Información de envío.
Disponibilidad del producto.
Confianza en la publicación.
Tiempo de carga.
Diseño mobile.
2. Implementar estrategias de re-engagement

La mayor pérdida de retención ocurre entre D14 y D21. Se recomienda probar:

Emails de recordatorio.
Notificaciones push.
Promociones personalizadas.
Recordatorios de carrito.
Mensajes basados en productos vistos.
Campañas de recuperación para usuarios inactivos.
3. Analizar mercados con mejor desempeño

Perú y México muestran mejor retención D28, mientras que Uruguay destaca en conversión final. Conviene analizar estos mercados para identificar prácticas replicables.

4. Validar mejoras con A/B Testing

Las recomendaciones deben probarse mediante experimentos controlados, especialmente en la etapa add_to_cart.

Reflexión personal

La etapa que mejoraría primero sería conversion_add_to_cart, porque es el principal punto de fuga del embudo. Mejorar esta etapa tiene un efecto multiplicador en todo el proceso de compra.

También aprendí que un usuario puede mostrar interés inicial, pero si no se le reactiva adecuadamente después de los primeros días, la retención cae de forma considerable. Por eso, además de mejorar la conversión, es clave diseñar estrategias para mantener el interés del usuario a lo largo del tiempo.

Habilidades aplicadas
Construcción de embudos multietapa en SQL usando CTEs.
Cálculo de tasas de conversión entre pasos.
Detección de caídas críticas en el funnel.
Análisis de retención por cohortes.
Segmentación de resultados por país.
Simulación de escenarios de mejora.
Validación de resultados.
Comunicación ejecutiva de hallazgos mediante el enfoque C-F-I.
