##  Especificación: Ecualizador espectral de audio usando DFT
Procesamiento y Manipulación de Señales en Frecuencia
Versión: 1.0
Curso: Procesamiento Digital de Señales — Ingeniería en Tecnología Computacional, 4.º semestre


Lenguaje: Python 3

---

## 1. Propósito
El proyecto consiste en crear un ecualizador de audio de tres bandas: bajos, medios y agudos.  

La idea principal será convertir una señal de audio del dominio del tiempo al dominio de la frecuencia usando la DFT/FFT. Una vez transformado, se busca modificar directamente los coeficientes espectrales según la banda. Para finalizar el proceso, se debe reconstruir la señal usando la transformada inversa.

---

## 2. Estructura de archivos en orden de uso
```text
ecualizador/ [cite: 182]
├── main.py [cite: 184]
├── audio/ [cite: 185]
│   ├── original.wav [cite: 186]
│   └── procesado.wav [cite: 187]
├── modules/ [cite: 189]
│   ├── fft_tools.py [cite: 190]
│   ├── equalizer.py [cite: 191]
│   ├── plots.py [cite: 192]
│   └── audio_io.py [cite: 193]
├── docs/ [cite: 195]
│   └── reporte.md [cite: 196]
└── requirements.txt [cite: 198]
```

---

## 3. Restricciones e Independencias

```text
Manejo numérico: numpy.  

Cálculos científicos (opcional): scipy.  

Graficación: matplotlib.  

Manejo de audio: soundfile o wave.  

Reproducción en tiempo de ejecución (opcional): sounddevice.

```

---

## 4. Módulo `audio_io.py`

### 4.1 Lectura de Audio

- Debe leer un archivo WAV.  

- Debe extraer y retornar las muestras, la frecuencia de muestreo y la duración del archivo.

### 4.2 Escritura de Audio

- Antes de exportar, se debe normalizar la señal para evitar clipping o distorsión.  

- Debe exportar el resultado final en un nuevo archivo llamado `audio_ecualizado.wav`.

---

## 5. Módulo `fft_tools.py`
Este módulo concentra las operaciones matemáticas para cambiar de dominio.

### 5.1 Transformada Directa (FFT)
- Debe aplicar la FFT para convertir la señal al dominio de frecuencia.  

- La operación fundamental a representar computacionalmente es: $$X[k] = \sum_{n=0}^{N-1} x[n]e^{-j2\pi kn/N}$$

### 5.2 Transformada Inversa (IFFT)
- Debe aplicar la IFFT para volver al dominio temporal.
- La transformada inversa a computar se basa en:$$x[n] = \frac{1}{N} \sum_{k=0}^{N-1} X[k]e^{j2\pi kn/N}$$

---

## 6. Módulo `equalizer.py`
Contiene la lógica central de la separación del espectro y la manipulación de coeficientes.  

### 6.1 Diseño de Bandas
Se deben identificar qué coeficientes pertenecen a cada banda creando máscaras espectrales. El rango aproximado definido es el siguiente:

| Banda | Rango aproximado | 
|---|---|
| Bajos | 20 - 250 Hz | 
| Medios | 250 - 4000 Hz | 
| Altos | 4000 - 20000 Hz |

### 6.2 Modificación Espectral
- Se deben implementar ganancias que permitan aumentar bajos, reducir medios o aumentar agudos.  

- La modificación se aplica al multiplicar los coeficientes FFT por los factores de ganancia correspondientes.

---

## 7. `Módulo plots.py`
El objetivo de este módulo es mostrar claramente el efecto del ecualizador a través de análisis visual.

### Gráficas Obligatorias
- Amplitud vs tiempo (para visualizar la señal temporal).
- Frecuencia vs magnitud (para graficar el espectro). 
- Señal original vs señal modificada.  
- Espectro antes/después y comparación de bandas.  

---

## 8. `Módulo main.py` e Interfaz

Niveles de Interfaz y Control

- Opción básica: Variables manuales definidas directamente en el código (ej. `gain_bass = 1.5`, `gain_mid = 0.8`, `gain_treble = 1.2`).  


- Opción intermedia: Uso de sliders implementados con `matplotlib.widgets` o `tkinter`.  


- Opción avanzada: Interfaz gráfica completa.

---

## 9. Criterios de Validación y Pruebas

- La ausencia de ruido.  

- La estabilidad del procesamiento.  

- La calidad general del audio resultante.  

- Los tiempos de ejecución.

---

## 10. Entregables

1. Directorio `ecualizador/` con el código fuente y audios de prueba según la estructura definida.

2. Documentación final recomendada (en `reporte.md`) que incluya: 
- Introducción: Explicación de qué es un ecualizador espectral. 
- Marco teórico: Fundamentos sobre FFT, DFT y procesamiento digital. 
- Desarrollo: Explicación de la lectura de datos, aplicación de FFT, modificación espectral e IFFT. 
- Resultados: Inclusión de gráficas, comparaciones y observaciones. 
- Conclusiones: Análisis de ventajas, limitaciones y posibles mejoras futuras.  
