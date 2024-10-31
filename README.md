# Frecuencia_tiempo

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
**Actividad simpática y parasimpática del sistema nervioso autónomo**

Sistema nervioso autónomo es el encargado de las acciones involuntarias del organismo, para esta labor se divide en dos sistemas principales el simpático y el parasimpático
El sistema parasimpático es el encargado de las acciones de forma involuntaria y el control de la inhibición de los sistemas del cuerpo esto por medio de dos neurotransmisores principales la acetilcolina y la norepinefrina. Es el encargado de controlar la homeostasis de órganos particulares, lo que permite relacionarlo con la relajación del cuerpo, entre las funcione que tiene es la disminución de la frecuencia cardiaca, así como la presión arterial, estimular él tuvo digestivo, la contracción de las vías aéreas, la producción de lágrimas y salivación entre otros.[1]

Por otro lado, el sistema simpático es el relacionado con el sistema de defensa y huida, por lo que se encarga de controlar el cuerpo en situaciones de estrés o de emergencia, entre sus funciones están, la aceleración del ritmo cardiaco, generar vasoconstricción lo que aumenta la presión arterial, dilata la pupila, estimular el sudor, inhibición dl tubo digestivo, estimular la producción de sustancias como la glucosa entre otros.[1]

**Efecto de la actividad simpática y parasimpática en la frecuencia cardiaca**

Como se mencionó anteriormente, estos dos sistemas se encargan de las variaciones en la actividad cardiaca, como en la presión arterial siendo el sistema simpático el que se encarga de aumentar la frecuencia cardiaca, y la vaso construcción de las arterias, mientras el simpático de disminuir la frecuencia cardiaca y la vaso dilatación.

**Variabilidad de la frecuencia cardiaca (HRV) medida como fluctuaciones en el intervalo R-R, y las frecuencias de interés en este análisis** 

La variabilidad cardiaca (HRV) es el tiempo entre cada latido, este tiene una medida de ms, y este está influido por el sistema nervioso autónomo, lo que lo liga directamente a un equilibrio con el sistema simpático y el parasimpático, la adquisición de la desviación estándar, esta variabilidad depende de varios factores, en los que uno muy presente es la edad, esta variabilidad, está alrededor de los 70 ms entre los 60-70 años, y esta va disminuyendo con el tiempo. Existen otra serie de factores que pueden indicar variaciones en la frecuencia cardiaca, entre ellas están el estrés, sedentarismo, alimentación o el consumo de sustancias. Por lo cual se puede implementar como un indicador de Salud. Entre las frecuencias vinculadas encontramos las siguientes.[4], en lo referente a las frecuencias predominantes encontramos unos valores estimados de 0.004- 015 Hz es asociada al a actividad simpática y parasimpática, mientras
0.15 – 0.4 Hz para el para simpático.

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

Incluir un diagrama de flujo que muestre los pasos del proyecto:
1. **Carga de datos**: Lectura de la señal ECG desde el archivo.
2. **Preprocesamiento de la señal**: Aplicación de filtros (pasaaltos y pasabajos) para reducir el ruido.
3. **Detección de picos R**: Uso de `find_peaks` para identificar los picos R en la señal filtrada.
4. **Cálculo de intervalos R-R**: Extracción y cálculo de intervalos entre picos R consecutivos.
5. **Interpolación de señal HRV**: Creación de una señal continua a partir de los intervalos R-R.
6. **Transformada Wavelet Continua**: Descomposición de la señal en frecuencia usando la wavelet Morlet.
7. **Análisis de Potencia**: Análisis de bandas LF y HF para interpretar la modulación simpática y parasimpática.

## Análisis de la Señal Cruda

Muestra la señal ECG original e incluye:
- **Frecuencia de muestreo**: Especificar 1000 Hz como frecuencia de muestreo utilizada.
- **Tiempo total de muestreo**: Mencionar que la señal representa 5 minutos de duración.
- **Niveles de cuantificación**: Especificar el número de bits de cuantificación si se conoce.
- **Estadísticas**: Calcular y mostrar la media, desviación estándar, y otras estadísticas de interés para la señal cruda.

### Código para Cálculo de Estadísticas

```python
# Estadísticas principales de la señal cruda
mean_ecg = np.mean(ecg_signal)
std_ecg = np.std(ecg_signal)
print(f"Media de la señal cruda: {mean_ecg}")
print(f"Desviación estándar de la señal cruda: {std_ecg}")
```

## Diseño y Justificación de Filtros

**Filtros Utilizados**: Implementación de un filtro pasaaltos y un pasabajos para eliminar ruidos indeseados.
- **Pasaaltos**: 0.5 Hz, para reducir el ruido de baja frecuencia asociado a movimientos.
- **Pasabajos**: 40 Hz, para atenuar las altas frecuencias no relacionadas con la señal ECG.

### Justificación de la Elección
Explica por qué estas frecuencias son adecuadas para el ECG:
- El pasaaltos permite preservar los componentes de frecuencia de interés.
- El pasabajos elimina ruidos de alta frecuencia y permite una detección precisa de los picos R.

## Cálculo y Análisis de Parámetros Básicos de HRV

**Parámetros Calculados**:
1. **Media de intervalos R-R**: Calculada y convertida a frecuencia cardíaca promedio.
2. **Desviación estándar de intervalos R-R**: Refleja la variabilidad en la frecuencia cardíaca.

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

**Espectrograma**:
Presenta el espectrograma de la señal de HRV usando la wavelet Morlet. Explica la visualización de las bandas LF y HF.

**Análisis Crítico de Bandas LF y HF**:
1. **Bandas de baja frecuencia (LF, 0.04-0.15 Hz)**: Asociadas a la actividad simpática y regulación de presión arterial.
2. **Bandas de alta frecuencia (HF, 0.15-0.4 Hz)**: Corresponden a la modulación parasimpática, como la respiración.

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

**Descripción Crítica**:
Describe cómo varían las potencias en LF y HF a lo largo del tiempo y qué significa esto en términos de balance simpático-parasimpático.

## Conclusión

Resume los hallazgos principales del análisis de HRV. Menciona cómo el SNA influye en la frecuencia cardíaca a través de la modulación en bandas LF y HF y explica la utilidad de la Transformada Wavelet Continua en este contexto.


## Referencias
[1]Elizabeth Coon. (2023) Generalidades sobre el sistema nervioso autónomo. Mayo Clinic
https://www.msdmanuals.com/es/professional/trastornos-neurol%C3%B3gicos/sistema-nervioso-aut%C3%B3nomo/generalidades-sobre-el-sistema-nervioso-aut%C3%B3nomo#Anatom%C3%ADa_v1032284_es


[2] Vizzarri, P., Vampa, V., & Martín, M. T. (2019). TRANSFORMADA WAVELET Y TEORÍA DE LA INFORMACIÓN EN EL ANÁLISIS DE SEÑALES BIOLÓGICAS. Investigación Joven, 6(Especial), 187. Recuperado a partir de https://revistas.unlp.edu.ar/InvJov/article/view/7118

[3] DESCOMPOSICIÓN DE SEÑALES, A. D. T. (2006). Introducción a la Transformada Wavelet. Departamento de Señales y sistemas. Universidad de Navarra. https://users.exa.unicen.edu.ar/catedras/escuelapav/cursos/wavelets/apunte.pdf

[4]A. Galan (2023).¿Qué es la variabilidad de frecuencia cardíaca (HRV)? Neolifesalud. https://www.neolifesalud.com/blog/prevencion-y-antiaging/que-es-la-variabilidad-de-frecuencia-cardiaca-hrv/



