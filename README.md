# Frecuencia_tiempo
## 1. Introducción
**Actividad simpática y parasimpática del sistema nervioso autónomo**
Sistema nervioso autónomo es el encargado de las acciones involuntarias del organismo, para esta labor se divide en dos sistemas principales el simpático y el parasimpático
El sistema parasimpático es el encargado de las acciones de forma involuntaria y el control de la inhibición de los sistemas del cuerpo esto por medio de dos neurotransmisores principales la acetilcolina y la norepinefrina. Es el encargado de controlar la homeostasis de órganos particulares, lo que permite relacionarlo con la relajación del cuerpo, entre las funcione que tiene es la disminución de la frecuencia cardiaca, así como la presión arterial, estimular él tuvo digestivo, la contracción de las vías aéreas, la producción de lágrimas y salivación entre otros.

Por otro lado, el sistema simpático es el relacionado con el sistema de defensa y huida, por lo que se encarga de controlar el cuerpo en situaciones de estrés o de emergencia, entre sus funciones están, la aceleración del ritmo cardiaco, generar vasoconstricción lo que aumenta la presión arterial, dilata la pupila, estimular el sudor, inhibición dl tubo digestivo, estimular la producción de sustancias como la glucosa entre otros.

**Efecto de la actividad simpática y parasimpática en la frecuencia cardiaca**
Como se mencionó anteriormente, estos dos sistemas se encargan de las variaciones en la actividad cardiaca, como en la presión arterial siendo el sistema simpático el que se encarga de aumentar la frecuencia cardiaca, y la vaso construcción de las arterias, mientras el simpático de disminuir la frecuencia cardiaca y la vaso dilatación.
**Variabilidad de la frecuencia cardiaca (HRV) medida como fluctuaciones en el intervalo R-R, y las frecuencias de interés en este análisis** 
La variabilidad cardiaca (HRV) es el tiempo entre cada latido, este tiene una medida de ms, y este está influido por el sistema nervioso autónomo, lo que lo liga directamente a un equilibrio con el sistema simpático y el parasimpático, la adquisición de la desviación estándar, esta variabilidad depende de varios factores, en los que uno muy presente es la edad, esta variabilidad, está alrededor de los 70 ms entre los 60-70 años, y esta va disminuyendo con el tiempo. Existen otra serie de factores que pueden indicar variaciones en la frecuencia cardiaca, entre ellas están el estrés, sedentarismo, alimentación o el consumo de sustancias. Por lo cual se puede implementar como un indicador de Salud. Entre las frecuencias vinculadas encontramos las siguientes.
0.004- 015 Hz es asociada al a actividad simpática y parasimpática, mientras
0.15 – 0.4 Hz para el para simpático.
**Transformada Wavelet: definición, usos y tipos de wavelet utilizadas en señales biológicas.**
La transformada de wavelet es una herramienta matemática para la caracterización de las partes importantes de la señal representándola sintéticamente, esta se suele implementar para el análisis de la variación-tiempo o para señales no estacionarias en la descomposición del dominio tiempo frecuencia, por lo cual representa una señal en términos de versiones trasladadas y dilatadas de onda infinita. 
La transformada se define:

$W_f(s, \tau) = \int f(t) \psi_{(s, \tau)}^*(t) \, dt$

$\psi_{(s, \tau)}^*(t) = \frac{1}{\sqrt{2}} \, \psi\left(\frac{t - \tau}{s}\right)$


donde s es el factor de escala, y τ es el factor de traslación. Los factores son s>0. Son dilatadas cuando s > 1 y contraídas cuando s < 1. El valor de s corresponde a rangos de diferentes frecuencias.

**Wavelets ortonormales y discretas**
Si f(t) es continua, las wavelets son continuas con el factor de escala, y las traslaciones discretas, lo que deriva en que la trasformada de Wavelet resulte en una serie de coeficientes.
La función f(t) puede ser reconstruida desde los coeficientes wavelets discretos Wf(s,τ), de la siguiente manera, donde A es una constante

$f(t) = A \sum_{s} \sum_{\tau} W_f(s, \tau) \, \psi_{(s, \tau)}^*(t)$

Los factores de escala y traslación de las wavelets discretas pueden ser expresados como:
 $s = s_0^i \quad \text{y} \quad \tau = k \tau_0 s_0^i$

donde el exponente i y la constante k son enteros, y s0 > 1 es un paso fijo de dilatación.
