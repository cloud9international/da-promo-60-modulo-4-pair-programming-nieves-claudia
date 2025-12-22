# Pair

## **Objetivo**

El objetivo de esta sesión es tener los datos preparados para poder hacer las visualizaciones. Para ello necesitamos hacer una serie de transformaciones.

**Acciones requeridas:** Para realizar las transformaciones necesarias, lo primero que necesitamos es conocer nuestros datos correctamente. El primer paso debería ser hacer un pequeño EDA o al menos una exploración visual para conocer los tipos de datos.

## **1. Descarga de datasets**

Obtén los siguientes datasets desde Kaggle:

1. [Dataset principal (friends\_episodes\_v3.csv)](https://www.kaggle.com/datasets/rezaghari/friends-series-dataset?select=friends_episodes_v3.csv)\
   \&#xNAN;*⚠️ Asegúrate de descargar la versión **v3**.*
2. [Dataset complementario (friends\_info.csv)](https://www.kaggle.com/datasets/sujaykapadnis/friends?select=friends_info.csv)

**Nota:** Estos datos son los mismos que usamos en el pair de Tableau, si ya los tienes, no deberías tener que descargarlos de nuevo.

***

## **2. Carga inicial y transformaciones**

1. **Primer dataset** (`friends_episodes_v3.csv`):

   * Carga el csv en un "Informe en blanco".
   * En este paso tenemos que seleccionar -> Transformar datos ![Transformar](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-1a74a690e43672bb0d4283ca6637fa57c93a1d61%2Ft_datos.png?alt=media)
   * Ahora toca verificar que los datos son correctos, especialmente tenemos que fijarnos en los que sabemos que son decimales.
   * Lo primero vamos a eliminar en los pasos aplicados: Tipo cambiado

   ![Transformar](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-0595f4fab0d271a30988e4850a67a1188e52fcc6%2Ftipo_cambiado.png?alt=media)

   * Ahora verifica todos los datos, algunas columnas deberías transformarlas en entero y fíjate especialmente en la columna "Stars". A esta columna tenemos que cambiarle el punto por una coma antes de poder transformarla en decimal.

   ![Transformar](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-b8dafd674421b60d85a735abab8277b9ff2d5de3%2Freemplazar.png?alt=media)

   * En este punto todos nuestros datos deberían tener el tipo de dato correcto.
2. **Crear columna con id**

Para poder unir más tarde nuestros dos datasets, necesitamos crear una columna que nos sirva cómo id. Tiene sentido que esa columna sea la unión de temporada y capítulo, el objetivo es tener una columna con datos con este formato: "T1C1". Esto nos va a permitir poder unir ambos conjuntos de datos usando esa columna.

* Empezamos por duplicar las columnas de "Season" y Episode Number", usa el botón derecho en cada columna para poder hacer esta acción:

  ![Transformar](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-f0978225a11c1541f5d6e42f1defa0881201ccd2%2Fduplicada.png?alt=media)
* Con la columna seleccionada, ve a Transformar y busca en Formato: Agregar prefijo. Vamos a poner una C delante de cada número de episodio y una T delante de cada temporada:

  ![Transformar](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-dbce294d0f777f861d0d012b447f029097040c71%2Fprefijo.png?alt=media) ![Asignar prefijo](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-0b5a90eef3f8c8ec8ae37dd2c4502cfe2006b8b3%2Fagregar_prefijo.png?alt=media)
* Una vez realizado este cambio, podemos seleccionar ambas columnas y unirlas poniendo - entre ambos valores:

  ![Transformar](https://github.com/Adalab/da-materiales-del-curso/blob/master/modulo-4/pairprogramming/assets/tableau/combinar.png)

Ya hemos creado la columna de id para poder identificar cada una de nuestras filas con un valor único. Haz click en Cerrar y aplicar y los datos se habrán cargado correctamente.

3. **Segundo dataset:** (`friends_info.csv`):

   Realiza las mismas acciones con el segundo dataset hasta que los datos sean todos correctos y tengas una columna de id similar a la creada en el paso anterior.

   ![Transformar](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-8539bcab981085e4c4cac220752e3d8217ecb287%2Fd2.png?alt=media)
4. **Combinar consultas:**

   Es hora de combinar las consultas para poder usar ambas tablas unidas en una misma consulta. Para ello vamos a ir al menú de Inicio y buscar "Combinar consultas" y presionamos en "Combinar consultas":

   ![Transformar](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-06f2c1ee5d57b4dd3b4dc6d8c9f4ad487c0e15e6%2Fcombinar1.png?alt=media)

   Seleccionamos las columnas de unión y pulsamos Aceptar. Esto nos crea una columna al final del dataset que tendremos que expandir (puedes seleccionar las columnas que deseas tener unidas).

   ![Transformar](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-4c92c69cfeb937d27d7d4d990d449559b5120e88%2Fexpand.png?alt=media)

Ha sido un largo paseo por las opciones de transformación que nos ofrece Power Bi, pero ahora tenemos nuestros datos transformados y listos para poder empezar con las visualizaciones!!


# Pair

Hoy comenzaremos a generar las primeras gráficas de análisis.

**Nota:** Los gráficos iniciales no serán totalmente representativos. Los refinaremos iterativamente hasta alcanzar el resultado final.

***

### **1. Big Numbers**

**Objetivo:** Familiarizarse con métricas clave y funciones de agregación.\
Crea estos indicadores:

* Número de episodios *(conteo total)*
* Número de temporadas *(valores únicos)*
* Puntuación media en IMDb *(promedio)*
* Millones de visualizaciones *(suma)*

**Nota:** recuerda que puedes copiar y pegar los elementos. *⚠️ Usa las funciones correctas para visualizaciones.*

![Preparación de KPIs](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-d248ff5f091ec9b42fe4b7732cd22863dbd26666%2Fbn.png?alt=media)

***

### **2. Gráfico de barras**

**Objetivo:** Comparar categorías usando codificación visual dual (altura + color).

* Representa **media de visualizaciones por temporada** (eje Y).
* Añade `season` a la leyenda para diferenciar temporadas por color.
* *Prueba a cambiar el tipo de agregación (media vs. suma).*

![Barras: visualizaciones por temporada](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-bb0928ceb852640de7d8f78083968c4dc33690c9%2Fbarras.png?alt=media)

***

### **3. Gráfico de líneas/area**

**Objetivo:** Analizar tendencias temporales.

* Muestra **total de visualizaciones por fecha de emisión** (eje X: air\_date, eje Y: visualizaciones).
* *Nota: prueba a cambiar las jerarquías de la fecha para profundizar en los datos.*

![Líneas: evolución de audiencia](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-81d03572f6648d699156fe2e50243d1203b98105%2Farea1.png?alt=media)\
![Líneas: evolución de audiencia](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-36c047bfb5ed9cb01288610ef5c008cdfdab8e96%2Farea2.png?alt=media)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### **4. Añadir segmentación de datos**

**Objetivo:** Para poder filtrar los datos y hacer nuestro proyecto más interactivo vamos añadir dos elementos de segmentación de datos, uno de los años de emisión y otro con las temporadas.

![Líneas: evolución de audiencia](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-60f1946bc112a7d59a99d36c4426b5522cb0930b%2Fsegmentos.png?alt=media)


# Pair

### **1. Imagen**

**Objetivo:** En este proyecto vamos a añadir una imagen cómo título para que quede más atractivo:

![Imagen](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-c28ddb4ddf0b8a0bf18f2b7a97f75e293121318d%2Fimagen.png?alt=media)

***

### **2. Formato Big Numbers**

**Objetivo:** Para que nuestras visualizaciones sean más descriptivas debemos mostrar los datos de forma sencilla y con un buen diseño que permitan su lectura:

![Formato BN](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-56edc0d0e4ae1ef6735d42da11619b4eafb6f32e%2Fformato_bn.png?alt=media)

***

### **3. Añadir formas**

**Objetivo:** Podemos agrupar elementos de forma visual con las formas.

**Nota:** no te olvides de poner el orden correcto de las "capas" en Selección:

![Formas](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-40f4f5d42f356997d3c9cee0d741c7a6df6ee5a1%2Fformas.png?alt=media)

***

### **4. Gráfico circular (Quotes por Author)**

**Objetivo:** Identificar proporciones en una variable categórica.\
1\. Importa `friends_quotes.csv`. 2. Crea un gráfico circular con la proporción de frases por autor:

![Gráfico circular](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-512616fc1cb78e8c64ad34c8e14e16f7e8643fc2%2Fcircular.png?alt=media)

```
3. Añade un filtro para que se muestre a los 6 protagonistas.
```

![Top N](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-549fb2240b5a8e0369d54ec26abff934f1fe038a%2Ftop_n.png?alt=media)


# Pair

### **1. Gráfica detalles**

**Objetivo:** Vamos a ñadir una gráfica con detalles para poder mostrar u ocultar usando marcadores:

**Nota:** este es un ejemplo, busca alguna visualización que te guste par mostrar los detalles de los capítulos.

![Detalle por capítulo](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-162c01580de02866e0469c5d6b787c9b32ecbc98%2Fdetalle.png?alt=media)

***

### **2. Marcadores**

**Objetivo:** Vamos a añadir unos marcadores para poder ocultar y mostrar la gráfica de detalles. El objetivo es poder tener mayor profundidad de análisis dentro del mismo Dashboard sin tener que sacrificar el espacio.

![Mostrar detalle por capítulo](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-70400eb276148c110857ead8c8725b9a87634834%2Fmostrar.png?alt=media)

![Ocultar detalle por capítulo](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-a3e4780dd48d6b7a67d3b1a33066719f6125fdbf%2Focultar.png?alt=media)

***

### **3. Borrar segmentaciones**

**Objetivo:** Crear un botón que elimine las segmentaciones que hemos aplicado a nuestro Dashboard. De esta manera, cuando tenemos varias segmentaciones, es más sencillo volver al estado inicial de las gráficas:

![Borrar segmentaciones](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-34424770dbfa911af24068fc388716f2f7c37bac%2Fborrar_seg.png?alt=media)


# Pair

### **1. Oh my God**

**Objetivo:** Al igual que hicimos en el pair de Tableau, vamos a ver cómo podemos incluir una gráfica que nos muestre quién ha dicho más veces la mítica frase de la serie.

* Ve a la pestaña de Modelado, Nueva columna y crea la fórmula para identificar "oh my god" en la frase:

**Nota:** Explora la función IF, CONTAINSSTRING y asegurate de tener en cuenta que la frase puede estar mayúscula o minúscula.

* Después crea una gráfica de barras incluyendo el recuento y el autor:

![OMG](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-1967f7cec0c128e852804fb050c564317b3457fc%2FOMG.png?alt=media)

* Añade los filtros necesarios para que se muestren sólo los 6 protagonistas y el recuento de la frase mítica.

![OMG](https://931940412-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FiDkWIWBqfl4XxuhVbroM%2Fuploads%2Fgit-blob-41c704eed6b6bfa1657e91c3a0f736f66d5717b6%2Ffiltro_omg.png?alt=media)

### **2. Ajustes finales**

**Objetivo:** Ahora es el momento de dejar brillar tu creatividad. Haz los cambios y ajustes necesarios en el Dashboard para que tenga un buen diseño y muestre los datos de forma completa. Intenta añadir más elementos visuales a la segunda página para que sea más informativa.

### **3. Contestar preguntas**

**Objetivo:** Intenta contestar a varias preguntas usando los Dashboards que has creado:

* ¿Todas las temporadas tienen el mismo número de capítulos?
* ¿Cuál es la temporada con mejor puntuación en IMDB? ¿Y el capítulo?
* ¿Quién dijo más veces la frase "Oh my god" en la primera temporada?