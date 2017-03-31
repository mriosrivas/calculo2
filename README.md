# Proyecto Final Cálculo 2
---

[//]: # (Image References)

[image1]: ./Images/deceleration01.gif "Desaceleración Abrupta"
[image2]: ./Images/deceleration02.gif "Desaceleración Sutil"
[image3]: ./Images/crash_wtout.gif "Sin Bolsa de Aire"
[image4]: ./Images/crash_with.gif "Con Bolsa de Aire"
[image5]: ./Images/aibarg.png "Accidente"
[image6]: ./Images/eq_HIC.png "HIC"
[image7]: ./Images/crash_data.png "Datos"
[image8]: ./Images/function.png "Datos y Curva"
[image9]: ./Images/crash_airbag.png "Datos y Curva"
[eq_02]: ./Images/crash_eq_02.png "Ecuación"
[eq_03]: ./Images/crash_eq_03.png "Ecuación"
[eq_04]: ./Images/crash_eq_04.png "Ecuación"




## Un poco de historia
En los años 50's, los automóviles eran máquinas asesinas. No existían tales cosas como bolsas de aire, cinturones de seguridad, sistemas anti-bloqueo, etc. Fue hasta que Ralph Nader, en los años 60's y 70's, presionara a los fabricantes de automóviles para construir autos más seguros.

### Desaceleración
La desaceleración de un automóvil puede ser abrupta, como en un accidente:

![alt text][image1]

o más sutil, como en el frenado normal de un auto:

![alt text][image2]

Cualquiera que sea el caso, el área bajo la curva debe de ser la misma, debido a que la velocidad que se debe de reducir es siempre la misma.

## Choques de prueba
Compañías automotrices, como Mercedes Benz, han sido pioneras en la seguridad vehicular, realizando muchos choques con maniquíes de prueba, con el objetivo de reducir lesiones en humanos.

Nuestra cabeza es como un péndulo, lo que la convierte en la parte más vulnerable de nuestro cuerpo en un accidente. En automóviles sin bolsas de aire, la desaceleración es bastante violenta y su duración es de pequeños períodos de tiempo.

El Criterio de la Lesión Encefálica es bastante alta en estos casos, indicando que la cabeza del ocupante saldrá lastimada. 

Las figuras que se muestran a continuación comparan los resultados entre un auto sin y con bolsas de aire. Se puede notar que en el caso del auto con bolsas de aire las fuerzas pico de desaceleración son mucho menores. 

![alt text][image3]
![alt text][image4]

Los rectángulos de color azul indican la región de desaceleración más crítica, cuando la fuerza máxima es ejercida por un período de tiempo largo.

Con el uso de bolsas de aire, es más probable sobrevivir un choque.
![alt text][image5]



## Criterio de la Lesión Encefálica
El **criterio de lesión encefálica** (CLE) (también conocido por sus siglas en inglés HIC Head Injury Criterion) es un índice relacionado con la probabilidad de sufrir algún tipo de traumatismo craneoencefálico como resultado de un impacto o deceleración violenta de la cabeza en algún tipo de accidente. El CLE o HIC se usa como índice estándar en la industria automovilística para predecir posibles daños encefálicos.

El valor del HIC se obtiene a partir de la curva de deceleración, generalmente obtenida de ensayos mediante un acelerómetro colocado en el centro de gravedad de un maniquí de ensayos de choque sometido a las fuerzas típicas de un choque frontal.
[Wikipedia](https://es.wikipedia.org/wiki/Criterio_de_lesi%C3%B3n_encef%C3%A1lica)

La fórmula experimental del HIC es:
![alt text][image6]

El HIC es el máximo valor sobre el período de tiempo crítico t<sub>1</sub> a t<sub>2</sub> para la expresión entre llaves, { }. El índice 2.5 es escogido para la cabeza, basado en la experimentación.

Algunos valores HIC a considerar:
* 250 equivale a una contusión,
* 500 es el valor de seguridad aceptado por la industria automotriz,
* 700 representa un valor para un daño severo,
* 1000 representa una amenaza a la vida.

## Modelado de un choque
### Sin bolsas de aire
La siguiente figura muestra los datos obtenidos por un acelerómetro en un choque, donde el eje horizontal se encuentra el tiempo *(ms)* y el eje vertical muestra valores de aceleración (*g*). La región de desaceleración más crítica se muestra en el rectángulo de color rosado, $t_1=50$ ms y $t_2=105$ ms, para estos valores el valor HIC es de 684.
![alt text][image7]

Para generalizar y obtener un modelo matemático del sistema, ajustaremos los valores medidos por el acelerómetro por medio de una curva. En este caso utilizaremos la función:

$$a(t)= \frac{16400}{(t-68)^2+400} + \frac{1480}{(t-93)^2+18}$$
![alt text][eq_02]

La gráfica de la función $a(t)$ junto con los valores medidos se muestra a continuación:
![alt text][image8]

Al construir un modelo con esta función, se puede obtener la siguiente integral:


$$HIC = (105-50)\Bigg[\frac{1}{105-50}\int_{50}^{105}\Bigg(\frac{16400}{(t-68)^2+400} + \frac{1480}{(t-93)^2+18}\Bigg)dt\Bigg]^{2.5}=710$$
![alt text][eq_03]

Los resultados obtenidos muestran que en promedio el valor HIC se encuentra en 697, lo cual está muy cerca de de una lesión severa.


### Con bolsas de aire y cinturón
De forma comparativa para un choque donde existe el uso de bolsas de aire y cinturón de seguridad, como el mostrado en la figura, para $t_1=45$ ms y $t_2=100$ ms, se obtienen los siguientes resultados:
* Utilizando los datos reales se obtiene un HIC = 296.

![alt text][image9]

* Utilizando el modelo matemático, con $a(t)= \frac{22000}{(t-74)^2+500}$
![alt text][eq_04]

se obtine un valor HIC = 312.

### Conclusión
Se puede notar que la implementación de bolsas de aire y el uso del cinturón de seguridad puede disminuir el riesgo de una lesión severa a una contusión en un accidente de tránsito.

## Proyecto del Curso
---

El proyecto del curso consiste en analizar y elaborar un estudio del impacto que tiene el uso de las bolsas de aire y el cinturón de seguridad en los choques automovilísticos. 

Para ello, se han obtenido una serie de mediciones en choques automovilísticos que se han almacenado en archivos
CSV, los cuales se han clasificado en:
1. Ejemplos: 
    * `crash_example.csv`, 
    * `airbag_example.csv`
2. Entrenamientos: 
    * `crash.csv`, 
    * `airbag.csv`
3. Determinación: 
    * `unkown_01.csv`, 
    * `unkown_02.csv`

**Ejemplos:**
Los archivos clasificados en este tipo permitirán comparar los resultados con los mostrados en la descripción anterior.

**Entrenamientos:**
Estos archivos permitirán construir un nuevo modelo y escoger los valores críticos. El estudiante sabrá cuál modelo aplicar, pues se conoce con anterioridad si los datos son de un choque con o sin bolsas de aire.

**Determinación:**
Para este caso no se sabe si los datos proporcionados son para un choque con o sin bolsas de aire, por lo cual el estudiante debe de determinar a cuál grupo pertenecen para su adecuado análisis.

### Desarrollo
La elaboración del proyecto consiste en lo siguiente para cada conjunto de archivos CSV:
1. Modelar sus datos con una función característica $a(t)$
2. Determinar el área bajo la curva de los datos proporcionados y de la función característica
3. Determinar los valores HIC para los valores proporcionados y la función característica (en el caso de los valores desconocidos también se debe determinar a cuál grupo pertenecen)

### Reporte
El proyecto debe de ser elaborado a computadora, con sus respectivas gráficas y modelos matemáticos. Se deben de incluir en el reporte los siguientes apartados:
1. Introducción
2. Objetivos
3. Desarrollo
4. Conclusiones
5. Bibliografía

### Presentación
Cada grupo debe elaborar una presentación de 5 minutos de duración donde exponga la modelación del problema, sus resultados y conclusiones.

### Entrega
* Reporte: 28 de Mayo
* Presentación: Por definir

## Referencias:
* http://www.intmath.com/applications-integration/hic-head-injury-criterion.php
* https://www.emaze.com/@AOFLRFQO/The-Head-Injury-Criterion
