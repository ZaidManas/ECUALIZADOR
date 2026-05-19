# Ecualizador espectral de audio usando DFT en Python

Proyecto enfocado en la creación de un ecualizador de audio de tres bandas: Bajos, Medios y Agudos.

Este sistema permite convertir una señal de audio del dominio del tiempo al dominio de la frecuencia mediante el uso de la DFT/FFT. Una vez en el dominio frecuencial, se modifican directamente los coeficientes espectrales dependiendo de la banda seleccionada y, finalmente, se reconstruye la señal normalizada utilizando la transformada inversa (IFFT).

## Descarga del proyecto

Antes de ejecutar el proyecto, es necesario descargar y descomprimir el archivo:

```text
ECUALIZADOR.zip
```

Después de extraerlo, acceder a la carpeta del proyecto desde la terminal o editor de código.

---

## Estructura

La arquitectura del proyecto está organizada de la siguiente manera, separando la lógica matemática, la interfaz y los archivos de prueba:

```text
ecualizador/
│
├── main.py            # Archivo principal de ejecución e interfaz
├── audio/             # Directorio para archivos .wav
│   ├── original.wav   # Audio de entrada para pruebas
│   └── procesado.wav  # Audio ecualizado exportado
│
├── modules/           # Módulos del sistema
│   ├── fft_tools.py   # Implementación y herramientas de FFT/IFFT
│   ├── equalizer.py   # Lógica de separación de bandas, máscaras y ganancias
│   ├── plots.py       # Visualización de señales (amplitud vs tiempo y frecuencia vs magnitud)
│   └── audio_io.py    # Lectura, escritura y normalización de archivos de audio
│
├── docs/              # Documentación del proyecto
│   └── reporte.md     # Documentación final con marco teórico, resultados y conclusiones
│
└── requirements.txt   # Dependencias del proyecto
```

---

## Instalación

Instalar las dependencias necesarias:

```text
pip install numpy scipy matplotlib soundfile sounddevice
```

---

## Uso

```text
Lectura y Análisis:
Se carga un archivo .wav para obtener sus muestras, duración y frecuencia de muestreo.

Transformación:
Se aplica la FFT para convertir la señal original al dominio de la frecuencia.

Ecualización:
Se configuran las ganancias manuales (o mediante sliders) para modificar los coeficientes espectrales, utilizando las siguientes bandas aproximadas:

Bajos: 20 – 250 Hz
Medios: 250 – 4000 Hz
Agudos: 4000 – 20000 Hz

Reconstrucción:
Se aplica la IFFT para volver al dominio temporal.

Exportación:
Se guarda el nuevo archivo (audio_ecualizado.wav) evitando clipping o distorsión.

Análisis Visual:
Se generan gráficas recomendadas para comparar la señal original contra la modificada y observar los cambios en el espectro antes y después de la ecualización.
```
