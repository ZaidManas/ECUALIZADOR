# Resultados

Durante el desarrollo del proyecto se logró implementar un ecualizador espectral funcional utilizando procesamiento digital de señales y la Transformada Rápida de Fourier (FFT). El sistema fue capaz de cargar archivos de audio en formato `.wav`, convertir la señal al dominio de la frecuencia, modificar las distintas bandas espectrales y reconstruir correctamente el audio mediante la IFFT.

El programa desarrollado incluye una interfaz gráfica avanzada construida con `Tkinter` y `CustomTkinter`, permitiendo la manipulación en tiempo real de las bandas de frecuencia mediante controles deslizantes independientes para graves, medios y agudos. Además, se integraron herramientas de visualización dinámica tanto en el dominio temporal como frecuencial.

---

## Lectura y procesamiento de audio

Se realizaron pruebas exitosas de lectura y escritura de archivos `.wav`, obteniendo correctamente:

- muestras de audio,
- frecuencia de muestreo,
- duración total de la señal,
- representación espectral mediante FFT.

El sistema permitió cargar múltiples archivos de audio utilizando una playlist integrada dentro de la interfaz.

---

## Transformada de Fourier (FFT)

La FFT permitió transformar la señal del dominio temporal al dominio de la frecuencia, obteniendo el espectro completo de magnitudes para cada audio cargado.

La representación espectral mostró correctamente:

- frecuencias bajas concentradas en graves,
- frecuencias medias asociadas principalmente a voces e instrumentos,
- frecuencias altas correspondientes a agudos y detalles armónicos.

---

## Ecualización espectral

Se implementó una separación de bandas mediante máscaras espectrales utilizando los siguientes rangos aproximados:

| Banda | Rango |
|---|---|
| Graves | 20 Hz – 250 Hz |
| Medios | 250 Hz – 4000 Hz |
| Agudos | 4000 Hz – 20000 Hz |

El sistema permitió modificar dinámicamente las ganancias de cada banda.

### Ejemplo de configuración utilizada

| Banda | Ganancia aplicada |
|---|---|
| Graves | × 2.4 |
| Medios | × 1.0 |
| Agudos | × 0.9 |

Con esta configuración se obtuvo un efecto “Bass Boost”, aumentando significativamente la presencia de frecuencias bajas.

---

## Reconstrucción mediante IFFT

Después de modificar el espectro, el audio fue reconstruido exitosamente mediante la Transformada Inversa de Fourier (IFFT).

Se implementó una etapa de normalización para evitar:

- clipping,
- saturación,
- distorsión digital.

El archivo procesado fue exportado correctamente en formato `.wav`.

---

## Interfaz gráfica

La interfaz desarrollada permitió:

- importar archivos de audio,
- visualizar la forma de onda temporal,
- visualizar el espectro de frecuencias,
- controlar reproducción, pausa y detención,
- modificar bandas en tiempo real,
- aplicar presets automáticos,
- exportar el audio procesado.

También se implementaron diferentes modos de visualización:

- vista dual,
- solo dominio temporal,
- solo espectro FFT.

---

## Presets implementados

El sistema integró presets preconfigurados para modificar automáticamente las ganancias espectrales:

- Bass Boost,
- Pop Vocal,
- Metal/Rock,
- Flat.

Cada preset alteró las bandas de frecuencia generando perfiles acústicos distintos según el tipo de audio deseado.

---

## Filtro avanzado Low-Cut

Se implementó un filtro Low-Cut para reducir frecuencias inferiores a 80 Hz.

Este filtro permitió:

- eliminar ruido de baja frecuencia,
- reducir vibraciones no deseadas,
- limpiar grabaciones de voz,
- mejorar claridad general del audio.

---

## Resultados visuales

Las gráficas generadas permitieron observar claramente:

- la señal original en el dominio temporal,
- la señal modificada después de la ecualización,
- el espectro de frecuencias antes del procesamiento,
- el espectro después de aplicar ganancias espectrales.

### Gráficas incluidas

- Señal temporal original
- Señal temporal procesada
- FFT original
- FFT procesada
- Comparación de bandas espectrales

---

## Rendimiento del sistema

El procesamiento mediante FFT permitió trabajar de manera eficiente incluso con archivos de audio de larga duración.

El sistema mostró:

- tiempos de procesamiento reducidos,
- estabilidad durante la reproducción,
- actualización dinámica de gráficas,
- manipulación fluida de sliders en tiempo real.

---

## Validación

Se realizaron pruebas con distintos tipos de audio:

- música instrumental,
- canciones,
- grabaciones de voz,
- sonidos ambientales.

En todos los casos el sistema logró modificar correctamente las bandas espectrales sin errores críticos de procesamiento.

---

## Observaciones generales

Durante las pruebas se observó que:

- aumentar excesivamente los graves puede generar saturación,
- incrementos elevados en agudos producen mayor presencia de ruido,
- la normalización posterior a la IFFT es fundamental,
- la FFT facilita enormemente la manipulación espectral del audio.

---

## Resultado final

El proyecto logró desarrollar un ecualizador espectral funcional capaz de:

- procesar audio digital mediante FFT,
- modificar bandas frecuenciales en tiempo real,
- visualizar señales y espectros,
- aplicar filtros y presets,
- reconstruir y exportar audio procesado correctamente.

Además, el sistema permitió aplicar conceptos fundamentales de:

- procesamiento digital de señales,
- análisis espectral,
- transformadas de Fourier,
- manipulación de audio digital en Python.
