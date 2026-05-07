# 📊 Análisis de Embudo y Retención — MercadoLibre

> Análisis del comportamiento de usuarios en un flujo de conversión e-commerce para identificar puntos de fuga y oportunidades de mejora en conversión y retención.

---

## 🎯 Objetivo

Responder tres preguntas clave de negocio:

MercadoLibre enfrentaba un reto clave de crecimiento: entender en qué etapa del proceso se perdía la mayoría de los usuarios, cómo evolucionaba su retención a lo largo del tiempo y cómo variaba este comportamiento por país.

Para responderlo, se analizaron datos de embudo y retención con SQL, se evaluaron cohortes mensuales y se identificaron oportunidades de mejora para optimizar la conversión y fortalecer la permanencia de los usuarios.

---

## 📁 Datasets utilizados

| Dataset | Descripción |
|---|---|
| `mercadolibre_funnel` | Eventos del journey del usuario en el embudo de conversión |
| `mercadolibre_retention` | Datos de retención de usuarios por cohortes mensuales |

---

## 🛠️ Herramientas utilizadas

| Herramienta | Uso |
|---|---|
| **SQL** | Limpieza, transformación, CTEs, cálculo de conversiones y cohortes |
| **Excel** | Visualización, análisis final y presentación ejecutiva |
| **Análisis C-F-I** | Comunicación de hallazgos (Contexto → Hallazgo → Implicación) |

---

## 🔄 Metodología

### Embudo de conversión multietapa

Se midió la conversión entre los principales eventos del journey del usuario:

```
🛍️ select_item → 🛒 add_to_cart → 🧾 begin_checkout → 🚚 add_shipping_info → 💳 add_payment_info → ✅ purchase
```

### Retención por cohortes

Se analizaron ventanas de retención para cohortes mensuales (enero–agosto 2025):

- **D7** · **D14** · **D21** · **D28**

### Simulación de mejora

Se simuló una recuperación del **15% del drop-off** en la etapa crítica `select_item → add_to_cart` para estimar el impacto potencial sobre las compras.

---

## 📈 Análisis C-F-I

### 1. Embudo general de conversión

| Contexto | Hallazgo | Implicación |
|---|---|---|
| Entre enero y agosto de 2025 se analizó la tasa de conversión entre cada etapa clave del embudo. | Conversión general: **76.9%** en `select_item`, **11.0%** en `add_to_cart`, **4.0%** en `begin_checkout`, **2.4%** en `add_shipping_info`, **2.1%** en `add_payment_info` y **1.3%** en `purchase`. | La mayor oportunidad está entre `select_item` y `add_to_cart`. Optimizar esta etapa genera impacto en todo el flujo posterior. |

### 2. Principal punto de fuga

| Contexto | Hallazgo | Implicación |
|---|---|---|
| Se comparó la pérdida porcentual entre cada etapa del embudo. | La etapa con mayor caída es `add_to_cart`: solo el **11.0%** de los usuarios que interactúan con un producto llegan a agregarlo al carrito (**~89% de drop-off**). | Se recomienda priorizar mejoras en la transición `select_item → add_to_cart`, reduciendo fricción y mejorando confianza, precio, disponibilidad y llamados a la acción. |

### 3. Conversión por país

| Contexto | Hallazgo | Implicación |
|---|---|---|
| Se analizó el embudo segmentado por país. | **Uruguay** tuvo la mayor conversión final a compra con **4.55%**. **México** alcanzó **2.48%**. Ecuador, Colombia y Paraguay registraron **0.00%** de conversión final. | Conviene analizar las condiciones de Uruguay y México para identificar patrones replicables en mercados con menor conversión. |

### 4. Retención por cohortes

| Contexto | Hallazgo | Implicación |
|---|---|---|
| Se evaluó la retención por cohortes mensuales entre enero y agosto de 2025. | Patrón consistente: **D7**: 86%–88% · **D14**: 54%–57% · **D21**: 23%–27% · **D28**: 2%–3%. La cohorte de agosto es censurada por ventana temporal incompleta. | El mayor deterioro ocurre entre D14 y D21. Se necesitan estrategias de re-engagement durante la segunda y tercera semana. |

### 5. Retención por país

| Contexto | Hallazgo | Implicación |
|---|---|---|
| Se comparó la retención D7–D28 por país. | **Perú** y **México** lideraron retención D28 con **3.2%** y **3.1%**. **Chile** y **Colombia** tuvieron los niveles más bajos con **1.7%** y **1.6%**. | La similitud entre países sugiere que el problema podría estar en el producto o la experiencia de usuario, más que en factores de mercado. |

### 6. Simulación de mejora

| Contexto | Hallazgo | Implicación |
|---|---|---|
| Se simuló una recuperación del **15% del drop-off** en `select_item → add_to_cart`. | `add_to_cart` aumentó de **11.0% a 20.9%** (+89.8% relativo). La conversión final a compra pasó de **1.3% a 2.4%**. | Una mejora pequeña en la recuperación temprana puede casi duplicar las etapas posteriores del embudo: efecto multiplicador. |

---

## 🔑 Principales hallazgos

- La conversión general a compra fue baja: **1.3%**
- La mayor caída ocurre entre `select_item` y `add_to_cart` (~89% de drop-off)
- Solo el **11.0%** de los usuarios agrega productos al carrito
- **Uruguay** fue el país con mejor conversión final: **4.55%**
- **Paraguay, Ecuador y Colombia** no registraron conversión final en la muestra
- La retención **D7 es alta**, pero cae fuertemente hacia D14 y D21
- La retención **D28 se mantiene baja** (~2%–3%)
- La cohorte de **agosto debe interpretarse con cautela** por falta de ventana completa
- Recuperar solo el **15% del drop-off** puede elevar `add_to_cart` de 11.0% a 20.9%

---

## 💡 Recomendaciones de negocio

### 1. Optimizar `select_item → add_to_cart`

Revisar los siguientes factores de fricción:

- Claridad del botón "Agregar al carrito"
- Costos de envío visibles antes del checkout
- Información de disponibilidad del producto
- Confianza en la publicación y el vendedor
- Tiempo de carga de la página
- Experiencia en dispositivos móviles

### 2. Implementar estrategias de re-engagement

La mayor pérdida de retención ocurre entre **D14 y D21**. Se recomienda probar:

- Emails y notificaciones push de recordatorio
- Promociones personalizadas
- Recordatorios de carrito abandonado
- Mensajes basados en productos vistos
- Campañas de recuperación para usuarios inactivos

### 3. Analizar mercados con mejor desempeño

**Perú** y **México** lideran retención D28. **Uruguay** destaca en conversión final. Identificar prácticas replicables en estos mercados.

### 4. Validar mejoras con A/B Testing

Todas las recomendaciones deben probarse mediante experimentos controlados, especialmente en la etapa `add_to_cart`.

---

## 🧠 Habilidades aplicadas

- Construcción de embudos multietapa en SQL con CTEs
- Cálculo de tasas de conversión entre pasos
- Detección de caídas críticas en el funnel
- Análisis de retención por cohortes
- Segmentación de resultados por país
- Simulación de escenarios de mejora
- Validación y comunicación ejecutiva de hallazgos (enfoque C-F-I)

---

## 💬 Reflexión personal

> La etapa que mejoraría primero sería `add_to_cart`, porque es el principal punto de fuga del embudo y su mejora tiene un efecto multiplicador en todo el proceso de compra.
>
> También aprendí que un usuario puede mostrar interés inicial, pero si no se le reactiva adecuadamente después de los primeros días, la retención cae de forma considerable. Por eso, además de mejorar la conversión, es clave diseñar estrategias para mantener el interés del usuario a lo largo del tiempo.
