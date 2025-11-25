# Dashboard de Ofertas de Mercado Libre (Qlik Sense)
Dashboard de análisis de la sección Ofertas de Mercado Libre con Qlik Sense, modelo estrella y SQL.

Este proyecto es un análisis de la sección **Ofertas** de Mercado Libre, a partir de datos obtenidos por web scraping, con modelado en **esquema estrella** y visualización en **Qlik Sense**.

El objetivo principal es responder a una pregunta simple:

> 💡 *“¿Qué ofertas realmente valen la pena para el usuario?”*

---

## 🧾 Dataset

- **Fuente:** Sección *Ofertas* de Mercado Libre (08/10/2022).
- **Obtención:** Web scraping.
- **Archivo:** `data/meli.csv`
- **Campos principales:**
  - `title` – Nombre del producto  
  - `price` – Precio actual  
  - `discount` – % de descuento  
  - `rating` – Calificación promedio  
  - `reviews` – Cantidad de reseñas  
  - `productlink-href` – URL del producto  

---

## 🧱 Modelado: esquema estrella

Para facilitar el análisis se construyó un modelo estrella con:

- **Tabla de hechos:** `Fact_Ofertas`
  - product_id  
  - date_id  
  - price  
  - discount  
  - rating  
  - reviews  
  - product_url  

- **Dimensiones:**
  - `Dim_Product`  
    - product_id  
    - product_name  
    - product_url  
  - `Dim_Fecha`  
    - date_id  
    - día / mes / año  

El modelo permite hacer análisis más claros, reusables y escalables.

> 📎 El diagrama del modelo se puede ver en:  
> `img/modelo_estrella.png`

---

## 🔁 Proceso ETL (resumen)

Antes de llegar al dashboard, se realizó:

- Limpieza de datos (precios, descuentos, ratings, reviews).
- Normalización de tipos de datos.
- Creación de `product_id` a partir de la URL del producto.
- Manejo de valores nulos.
- Carga del modelo en Qlik Sense usando tablas `RESIDENT`.

---

## 📊 Dashboard en Qlik Sense

El archivo del proyecto está en:

- `qlik/Ofertas_MercadoLibre.qvf`

### Principales elementos del dashboard

- **KPIs iniciales:**
  - Precio promedio  
  - Descuento promedio  
  - Rating promedio  
  - Total de productos analizados  
  - Total de reseñas  

- **Gráficos y tablas:**
  - Top 10 productos por **descuento**.  
  - Top 10 productos por **reseñas** (popularidad real).  
  - “Mapa de gangas”: cruza % de descuento, rating y cantidad de reviews.  
  - Descuento promedio por **rango de precio**.  
  - Tabla con un **índice de oportunidad** propio combinando:
    - descuento  
    - rating  
    - volumen de reseñas  

> 📎 Algunas capturas del dashboard se encuentran en `img/`.

---

## 🎨 Diseño y UX

El dashboard se diseñó usando:

- Colores de marca de Mercado Libre (amarillo y azul).
- KPIs alineados y jerarquía visual clara.
- Gráficos organizados por bloques:
  1. Contexto general (KPIs).
  2. Ranking de ofertas.
  3. Popularidad real.
  4. Gangas y rangos de precio.

El objetivo fue lograr un tablero que sea **claro para negocio** y a la vez visualmente agradable.

---

## 🚀 Cómo abrir el proyecto

1. Descargar el archivo:
   - `qlik/Ofertas_MercadoLibre.qvf`
2. Abrirlo con **Qlik Sense Desktop**.
3. Ver/editar el modelo de datos y las hojas de análisis.

---

## 💭 Ideas de uso

Este proyecto puede servir como ejemplo de:

- Modelado en esquema estrella para e-commerce.
- Proceso ETL básico aplicado a datos scrapeados.
- Construcción de dashboards en Qlik Sense con enfoque en negocio.
- Presentación de proyectos de data analytics en portafolio / LinkedIn.

---

## 📬 Contacto

Si te interesa ver más detalles del proceso (scripts de carga, SQL, etc.) o tenés feedback, ¡bienvenido! 🙂
