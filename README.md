# Análisis de Variabilidad de la Frecuencia Cardíaca (HRV) usando Transformada Wavelet Continua

## Tabla de Contenidos
1. [Introducción](#introducción)
2. [Resumen Teórico](#resumen-teórico)
3. [Diagrama de Proyecto](#diagrama-de-proyecto)
4. [Análisis de la Señal Cruda](#análisis-de-la-señal-cruda)
5. [Diseño y Justificación de Filtros](#diseño-y-justificación-de-filtros)
6. [Cálculo y Análisis de Parámetros Básicos de HRV](#cálculo-y-análisis-de-parámetros-básicos-de-hrv)
7. [Espectrograma y Análisis de Bandas de Frecuencia](#espectrograma-y-análisis-de-bandas-de-frecuencia)
8. [Conclusión](#conclusión)


## 1. Introducción

La respuesta de variabilidad de la frecuencia cardíaca es un aspecto fisiológico que puede tener repercusión en varios indicadores de salud, siendo así que permite evaluar la salud del sistema cardiovascular y su respuesta a diferentes estímulos. Teniendo en cuenta lo antes mencionado, el siguiente laboratorio tiene el propósito de procesar una señal EMG, para establecer como la variabilidad cardiaca puede llegar a ser un indicador de salud, a la señal luego de su filtrado y el establecimiento de datos estadísticos referentes a la frecuencia cardiaca, Se le realizara una trasformada de wavelet teniendo una Molet como la onda madre, que permita rescatar las características necesarias de la señal.

**Actividad simpática y parasimpática del sistema nervioso autónomo**

Sistema nervioso autónomo es el encargado de las acciones involuntarias del organismo, para esta labor se divide en dos sistemas principales el simpático y el parasimpático
El sistema parasimpático es el encargado de las acciones de forma involuntaria y el control de la inhibición de los sistemas del cuerpo esto por medio de dos neurotransmisores principales la acetilcolina y la norepinefrina. Es el encargado de controlar la homeostasis de órganos particulares, lo que permite relacionarlo con la relajación del cuerpo, entre las funcione que tiene es la disminución de la frecuencia cardiaca, así como la presión arterial, estimular él tuvo digestivo, la contracción de las vías aéreas, la producción de lágrimas y salivación entre otros.[1]

Por otro lado, el sistema simpático es el relacionado con el sistema de defensa y huida, por lo que se encarga de controlar el cuerpo en situaciones de estrés o de emergencia, entre sus funciones están, la aceleración del ritmo cardiaco, generar vasoconstricción lo que aumenta la presión arterial, dilata la pupila, estimular el sudor, inhibición dl tubo digestivo, estimular la producción de sustancias como la glucosa entre otros.[1]

**Efecto de la actividad simpática y parasimpática en la frecuencia cardiaca**

Como se mencionó anteriormente, estos dos sistemas se encargan de las variaciones en la actividad cardiaca, como en la presión arterial siendo el sistema simpático el que se encarga de aumentar la frecuencia cardiaca, y la vaso construcción de las arterias, mientras el simpático de disminuir la frecuencia cardiaca y la vaso dilatación.

**Variabilidad de la frecuencia cardiaca (HRV) medida como fluctuaciones en el intervalo R-R, y las frecuencias de interés en este análisis** 

La variabilidad cardiaca (HRV) es el tiempo entre cada latido, este tiene una medida de ms, y este está influido por el sistema nervioso autónomo, lo que lo liga directamente a un equilibrio con el sistema simpático y el parasimpático, la adquisición de la desviación estándar, esta variabilidad depende de varios factores, en los que uno muy presente es la edad, esta variabilidad, está alrededor de los 70 ms entre los 60-70 años, y esta va disminuyendo con el tiempo. Existen otra serie de factores que pueden indicar variaciones en la frecuencia cardiaca, entre ellas están el estrés, sedentarismo, alimentación o el consumo de sustancias. Por lo cual se puede implementar como un indicador de Salud. Entre las frecuencias vinculadas encontramos las siguientes.[4], en lo referente a las frecuencias predominantes encontramos unos valores estimados para un filtro pasa banda estaria entre 0.5 -12 Hz

**Transformada Wavelet: definición, usos y tipos de wavelet utilizadas en señales biológicas.**

La transformada de wavelet es una herramienta matemática para la caracterización de las partes importantes de la señal representándola sintéticamente, esta se suele implementar para el análisis de la variación-tiempo o para señales no estacionarias en la descomposición del dominio tiempo frecuencia, por lo cual representa una señal en términos de versiones trasladadas y dilatadas de onda infinita.[2] 
La transformada se define:

$W_f(s, \tau) = \int f(t) \psi_{(s, \tau)}^*(t) \, dt$

$\psi_{(s, \tau)}^*(t) = \frac{1}{\sqrt{2}} \, \psi\left(\frac{t - \tau}{s}\right)$


donde s es el factor de escala, y τ es el factor de traslación. Los factores son s>0. Son dilatadas cuando s > 1 y contraídas cuando s < 1. El valor de s corresponde a rangos de diferentes frecuencias.

**Wavelets ortonormales y discretas**

Si f(t) es continua, las wavelets son continuas con el factor de escala, y las traslaciones discretas, lo que deriva en que la trasformada de Wavelet resulte en una serie de coeficientes.

La función f(t) puede ser reconstruida desde los coeficientes wavelets discretos Wf(s,τ), de la siguiente manera, donde A es una constante [3]

$f(t) = A \sum_{s} \sum_{\tau} W_f(s, \tau) \, \psi_{(s, \tau)}^*(t)$

Los factores de escala y traslación de las wavelets discretas pueden ser expresados como:
 $s = s_0^i \quad \text{y} \quad \tau = k \tau_0 s_0^i$

donde el exponente i y la constante k son enteros, y s0 > 1 es un paso fijo de dilatación.

Mientras que la ortonormal, representa una señal con su mismo comportamiento

$\int \psi_{(s, \tau)}^*(t) \, \psi_{(m, n)}(t) \, dt = 1 \quad \text{si} \quad i = m \, \text{y} \, k = n$

 $\int \psi_{(s, \tau)}^*(t) \, \psi_{(m, n)}(t) \, dt = 0 \quad \text{en cualquier otro caso}$

**Tipos de Ondas Wavelets**

Con el propósito de representar ciertas funciones en diferentes escalas y posiciones, existen una serie de tipos de señales estandarizadas, para permitirnos suele implementar para el análisis de la variación-tiempo, en la siguiente imagen encontraremos varios tipos de señales, de las culés se implementará la Morlet como la transformada implementada en la señal madre, esto debido a que nos permitirá identificar frecuencias especificas en la señal adquirida, junto a su locación temporal.

![image](https://github.com/user-attachments/assets/68d02e11-ea0a-4a4a-be5c-cc85876a67a0)


La elección de la trasformada de Wavelet Morlet se implementó debido a sus características de eliminar ruido, preservando así las propiedades ECG, evitando la pérdida importante de detalles fisiológicos, desde un punto de vista computacional, permitiendo evidenciar la detección como lo puede ser el complejo QRS como otras características, en este caso permite detallar con más claridad los intervalos R-R que se aprovecharan principalmente en el siguiente laboratorio.

## Diagrama de Proyecto

Para la elaboración del proyecto se realizó una planificación con los procesos desarrollados para adquirir la señal y su procesamiento. Como resultado se obtuvo el siguiente diagrama de flujo, que detalla el paso a paso del procedimiento realizado a lo largo del laboratorio. 

![Flowchart (1)](https://github.com/user-attachments/assets/0f7832ca-c8c2-431d-912f-1f4191a7235d)


Detallando en las más relevantes luego de la adquisición de la señal ECG y el pre-procesamiento de la señal, se establecieron los datos de la media y desviación estándar de los intervalos R-R, creando así una señal continua, que será interpolada con el fin de poderla graficar, para su posterior procesamiento, donde ya podremos implementar la trasformada de Wavelet continua, teniendo como referencias la onda Morlet, ya pasando a su análisis, se aplicara un espectrograma que nos permita ver todas las característica de la onda como lo es el tiempo, la frecuencia y su potencia. Con los datos ya adquiridos, logramos realizar el respectivo análisis a los datos obtenidos


## Análisis de la Señal Cruda
![image](https://github.com/user-attachments/assets/261f8a1c-f2d2-4608-82fd-b727f693e7d8)
### Frecuencia de Muestreo
La señal ECG fue registrada con una frecuencia de muestreo de **1000 Hz**, lo cual es adecuado para capturar los detalles finos de la actividad cardíaca, dado que el ECG contiene componentes de frecuencia que se encuentran típicamente entre 0.05 y 150 Hz. La frecuencia de muestreo alta permite una representación precisa de la señal, lo cual es fundamental para identificar los picos R de manera fiable y calcular los intervalos R-R con precisión.

### Tiempo Total de Muestreo
La duración de la señal es de **5 minutos** (300 segundos), lo cual proporciona suficiente información para el análisis de la variabilidad de la frecuencia cardíaca (HRV) en una escala de tiempo relativamente larga. La HRV es un indicador robusto del equilibrio autonómico y cardiovascular cuando se mide en períodos largos de tiempo, ya que permite observar las variaciones naturales en la frecuencia cardíaca asociadas al sistema nervioso autónomo (SNA).

### Niveles de Cuantificación
La señal fue cuantificada con **16 bits**, lo que permite un total de $2^{16}$ niveles de cuantificación, es decir, 65,536 niveles discretos. Este alto nivel de cuantificación garantiza que los detalles sutiles de la amplitud de la señal se capturen con precisión, lo cual es importante para evitar errores en la detección de los picos R y para un análisis de HRV más preciso.

### Estadísticas Principales de la Señal Cruda

#### Cálculo de Intervalos R-R
A partir de los picos R detectados en la señal ECG, se calculó una serie de intervalos R-R, que representan el tiempo entre picos R consecutivos. Los valores de los intervalos R-R en segundos son:

```
[0.623, 0.735, 0.629, 0.572, 0.506, 0.73,  0.52,  0.521, 0.701, 0.533, 
 0.623, 0.547, 0.546, 0.831, 0.797, 1.045, 0.817, 0.607, 0.909, 0.985, 
 0.646, 0.518, 0.622, 0.86, 0.776, 0.514, 0.614, 0.97,  0.79,  0.619, 
 0.832, 0.773, 0.611, 0.737, 0.776, 0.957, 0.629, 0.624, 0.624, 0.528, 
 0.712, 0.812]
```

#### Media y Desviación Estándar de los Intervalos R-R
Los valores promedio y de dispersión calculados para los intervalos R-R son:
- **Media de Intervalos R-R**: \(0.698\) segundos
- **Desviación Estándar de Intervalos R-R**: \(0.144\) segundos

#### Análisis de los Valores Calculados
La **media de los intervalos R-R** de \(0.698\) segundos sugiere una **frecuencia cardíaca promedio** de aproximadamente:

$$
\text{Frecuencia cardíaca} = \frac{60}{\text{Media de R-R}} = \frac{60}{0.698} \approx 86 \text{ bpm}
$$

Este valor indica que el sujeto tiene una frecuencia cardíaca en el rango normal para un adulto en reposo, que suele encontrarse entre 60 y 100 bpm. La frecuencia cardíaca promedio ligeramente elevada (86 bpm) podría ser normal o estar influenciada por factores como el estrés, la actividad física reciente o el estado emocional, ya que todos estos factores afectan el equilibrio del sistema nervioso autónomo (SNA) sobre el corazón.

La **desviación estándar de los intervalos R-R** de \(0.144\) segundos refleja la **variabilidad de la frecuencia cardíaca (HRV)**. Una desviación estándar mayor indica una variabilidad en los intervalos R-R, lo cual es generalmente positivo en términos de salud, ya que sugiere un sistema cardiovascular adaptable y con una buena capacidad de respuesta autonómica. Por otro lado, valores de desviación estándar bajos (baja HRV) pueden estar asociados con factores de riesgo cardiovascular y estados de estrés o ansiedad crónicos, que tienden a reducir la modulación parasimpática sobre el corazón.

En la literatura, valores de HRV más elevados en bandas de frecuencia baja (LF) se relacionan con la actividad simpática, mientras que los valores en bandas de frecuencia alta (HF) suelen reflejar la modulación parasimpática. En este caso, la variabilidad medida es moderada, lo cual podría indicar un equilibrio razonable entre ambas ramas del SNA.

**Comparación con Referencias**:
En estudios de referencia, como los publicados por Task Force of The European Society of Cardiology y The North American Society of Pacing and Electrophysiology, se establece que una HRV moderada es un buen indicador de resiliencia autonómica. El valor de desviación estándar obtenido en esta medición (0.144) se encuentra en un rango esperado para individuos en reposo, lo que sugiere que el sistema cardiovascular del sujeto puede responder adecuadamente a los cambios ambientales y emocionales.


## Diseño y Justificación de Filtros

**Filtros Utilizados**: **Segun el articulo publicado por Ge Healthcare [4] los filtros recomendados para una señal ECG son de:
- **Pasa altos**: 0.5 Hz, para reducir el ruido de baja frecuencia asociado a movimientos**.
- **Pasa bajos**: 150 HZ Hz, para atenuar las altas frecuencias no relacionadas con la señal ECG.
por los cuales se utilizaron filtros butterwoth y para saber el orden del filtro primero se diseño uno pasa bajos dejeando lo siguiente:

**si sabemos que la frecuencia de corte se encuentra en -3db en 150hz y asumimos que la atenuacion se encontrara en -10db en 300hz**
  
![Captura de pantalla (3)](https://github.com/user-attachments/assets/d74b202f-a182-468f-b2d9-c994c4fc5805)


funcion de transferencia del orden 4:

![Captura de pantalla (4)](https://github.com/user-attachments/assets/376016c0-2431-4257-bbd2-171b2dea83ce)

### Justificación de la Elección
Explica por qué estas frecuencias son adecuadas para el ECG:
- El pasaaltos permite preservar los componentes de frecuencia de interés.
- El pasabajos elimina ruidos de alta frecuencia y permite una detección precisa de los picos R.
- De acuerdo a los valores obtenidos se utilizo un filtro butterworth de orden 4.
- los filtros butterworth son utlizados por sus características de suavidad y estabilidad en la respuesta de frecuencia
## Cálculo y Análisis de Parámetros Básicos de HRV


### Código para Cálculo de Parámetros Básicos

```python
# Calcular frecuencia cardíaca promedio y desviación estándar
mean_rr = np.mean(rr_intervals)
std_rr = np.std(rr_intervals)
heart_rate = 60 / mean_rr  # Frecuencia cardíaca promedio en bpm
print(f"Media de intervalos R-R: {mean_rr} s")
print(f"Desviación estándar de intervalos R-R: {std_rr} s")
print(f"Frecuencia cardíaca promedio: {heart_rate} bpm")
```

**Análisis**:
- Comenta sobre el significado de estos valores en términos de la actividad simpática y parasimpática. Por ejemplo, una desviación estándar baja indica menos variabilidad, lo que podría estar relacionado con el predominio del sistema simpático.

## Espectrograma y Análisis de Bandas de Frecuencia
![image](https://github.com/user-attachments/assets/852dad49-e5f8-4f17-aee5-3f4ec0470336)

### Análisis de Bandas de Frecuencia

En el análisis de la señal de variabilidad de la frecuencia cardíaca (HRV), se observan dos representaciones clave en las imágenes proporcionadas. La primera imagen muestra la potencia de las bandas de baja frecuencia (LF) y alta frecuencia (HF) a lo largo del tiempo, mientras que la segunda imagen presenta el espectrograma de la señal utilizando la transformada wavelet de Morlet.

#### Transformada Wavelet de Morlet
La wavelet de Morlet es una herramienta matemática utilizada para descomponer una señal en diferentes componentes de frecuencia a lo largo del tiempo, permitiendo visualizar cómo cambia el contenido de frecuencia de la señal en distintos momentos. Esto es particularmente útil para analizar la HRV, ya que permite observar la actividad en bandas de frecuencia específicas asociadas a la modulación simpática y parasimpática del sistema nervioso autónomo.

#### Visualización de las Bandas de Frecuencia (LF y HF)
En la primera gráfica, se observan las bandas de baja frecuencia (LF) de 0.04 a 0.15 Hz en color azul y las de alta frecuencia (HF) de 0.15 a 0.4 Hz en color verde. Estas bandas son relevantes en el análisis de la HRV porque están asociadas a distintos aspectos de la regulación autonómica:

- **Banda de Baja Frecuencia (LF, 0.04-0.15 Hz):** Esta banda está vinculada principalmente con la actividad simpática y con la regulación de la presión arterial. La potencia en esta banda refleja la actividad del sistema nervioso simpático y se asocia con la respuesta del organismo a factores de estrés y cambios en la postura.
  
- **Banda de Alta Frecuencia (HF, 0.15-0.4 Hz):** La potencia en esta banda está relacionada con la modulación parasimpática, especialmente con el control de la frecuencia cardíaca a través de la respiración (respiratory sinus arrhythmia). Esta banda es un indicador de la actividad del sistema nervioso parasimpático y suele aumentar durante la respiración profunda y en momentos de relajación.

### Código de Cálculo de Potencia en LF y HF

```python
# Análisis de Potencia en LF y HF
lf_band = (frequencies >= 0.04) & (frequencies < 0.15)
hf_band = (frequencies >= 0.15) & (frequencies < 0.4)

lf_power = power[lf_band, :].mean(axis=0)
hf_power = power[hf_band, :].mean(axis=0)

plt.figure(figsize=(10, 4))
plt.plot(time_interp, lf_power, label='LF Power (0.04-0.15 Hz)', color='blue')
plt.plot(time_interp, hf_power, label='HF Power (0.15-0.4 Hz)', color='green')
plt.xlabel('Time (s)')
plt.ylabel('Power')
plt.legend()
plt.title('Low and High Frequency Power over Time')
plt.show()
```
#### Descripción Crítica de la Variación de Potencias en LF y HF
A lo largo del tiempo, se observan variaciones en las potencias de las bandas LF y HF, lo cual proporciona una visión del balance simpático-parasimpático del individuo. Aumentos en la potencia de la banda LF pueden indicar una activación simpática, sugiriendo que el sistema nervioso está respondiendo a estímulos de estrés o cambios posturales. Por otro lado, incrementos en la potencia de la banda HF reflejan una mayor actividad parasimpática, indicando un estado de relajación o un patrón respiratorio regular.

Este balance entre las potencias de las bandas LF y HF a lo largo del tiempo permite evaluar la respuesta autonómica del sujeto y el equilibrio entre las influencias simpáticas y parasimpáticas. En situaciones de salud, se espera un balance dinámico, donde ambos sistemas contribuyen a la regulación adecuada de la frecuencia cardíaca.

## Conclusión

En conclusión, la transformada de wavelet durante el laboratorio se demostró como una herramienta útil para la descomposición del dominio del tiempo y la frecuencia, implementada así en el laboratorio la onda Molet que en señales EMG permite resaltar los datos más relevantes de los complejos QRS de la señales cardiacas, dando como resultado que podamos analizar a una persona desde el conocimiento de su variabilidades en la frecuencia cardiaca, donde pudimos analizar a una persona que da valores normales con respecto a la literatura.

(Resume los hallazgos principales del análisis de HRV. Menciona cómo el SNA influye en la frecuencia cardíaca a través de la modulación en bandas LF y HF y explica la utilidad de la Transformada Wavelet Continua en este contexto.)


## Referencias
[1]Elizabeth Coon. (2023) Generalidades sobre el sistema nervioso autónomo. Mayo Clinic
https://www.msdmanuals.com/es/professional/trastornos-neurol%C3%B3gicos/sistema-nervioso-aut%C3%B3nomo/generalidades-sobre-el-sistema-nervioso-aut%C3%B3nomo#Anatom%C3%ADa_v1032284_es


[2] Vizzarri, P., Vampa, V., & Martín, M. T. (2019). TRANSFORMADA WAVELET Y TEORÍA DE LA INFORMACIÓN EN EL ANÁLISIS DE SEÑALES BIOLÓGICAS. Investigación Joven, 6(Especial), 187. Recuperado a partir de https://revistas.unlp.edu.ar/InvJov/article/view/7118

[3] DESCOMPOSICIÓN DE SEÑALES, A. D. T. (2006). Introducción a la Transformada Wavelet. Departamento de Señales y sistemas. Universidad de Navarra. https://users.exa.unicen.edu.ar/catedras/escuelapav/cursos/wavelets/apunte.pdf

[5] GE Healthcare. A Guide to ECG Signal Filtering. https://www.gehealthcare.com/insights/article/a-guide-to-ecg-signal-filtering



[4]A. Galan (2023).¿Qué es la variabilidad de frecuencia cardíaca (HRV)? Neolifesalud. https://www.neolifesalud.com/blog/prevencion-y-antiaging/que-es-la-variabilidad-de-frecuencia-cardiaca-hrv/



