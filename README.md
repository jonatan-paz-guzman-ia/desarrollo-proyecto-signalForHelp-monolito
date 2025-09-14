## Integrantes

- Dayana Muñoz Muñoz 
  - dayana.munoz_m@uao.edu.co 
  - 22500272

- Jonatan Paz Guzman 
  - jonatan.paz@uao.edu.co 
  - 22500269


# Detección de Gestos de Ayuda (Signal for Help) con Segmentación usando YOLOv8

Este proyecto tiene como objetivo desarrollar un sistema capaz de detectar gestos silenciosos de auxilio, específicamente la señal conocida como **Signal For Help**, utilizada para pedir ayuda ante situaciones de violencia o peligro.

Dado que la señal completa es una secuencia dinámica de gestos, este MVP (Producto Mínimo Viable) se enfoca en la **segmentación de clases individuales**, específicamente las posiciones de **palma abierta** y **puño cerrado**, como paso previo a una detección más compleja basada en secuencias.

## Descripción del Proyecto

Utilizamos un modelo **YOLOv8** para realizar **segmentación de objetos en tiempo real** usando la cámara del computador. Además, se aplican **dos filtros tradicionales de procesamiento de imagen** (desenfoque gaussiano y realce de bordes) para mejorar la calidad visual sin perder color ni forma.

## Dataset
[Link](https://drive.google.com/drive/folders/1qsxRhJxr5ayyyQ3ZqAJ-D38_9cDhfbBB?usp=sharing)

El conjunto de datos fue creado manualmente utilizando **Roboflow**, etiquetando imágenes con las siguientes clases:

- **Palma** (mano abierta)
- **Puño** (mano cerrada)

### Detalles del dataset:

- 30 imágenes por clase (60 imágenes totales).
- División automática:
  - **70%** entrenamiento
  - **15%** validación
  - **15%** testeo

### Preprocesamiento y aumentaciones aplicadas en Roboflow:

**Preprocessing:**
- Auto-Orient: aplicado
- Resize: stretch a 640x640

**Augmentations:**
- 10 versiones por cada imagen de entrenamiento
- Rotaciones:
  - 90° en sentido horario y antihorario
  - Aleatorias entre -10° y +10°
- Saturación: entre -25% y +25%
- Ruido: hasta 1.53% de los píxeles

### Dataset final generado:
- **Train Set:** 410 imágenes  
- **Validation Set:** 9 imágenes  
- **Test Set:** 9 imágenes  


## Requisitos

Instala las dependencias necesarias ejecutando:

```bash
pip install -r requirements.txt
```

## ¿Cómo ejecutar el proyecto?

1. Abre una terminal y ubícate en la carpeta raíz del proyecto:

```bash
cd ruta/a/tu/proyecto
```

2. Instala las dependencias (si aún no lo hiciste):

```bash
pip install -r requirements.txt
```

3. Ejecuta la aplicación principal:

```bash
python main.py
```

Esto iniciará la cámara del computador, aplicará los filtros de procesamiento a cada frame y realizará la segmentación de objetos en tiempo real utilizando el modelo YOLOv8.

> Para detener la ejecución, simplemente presiona la tecla **"s"** en la ventana del video.