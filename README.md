# GG_EQUIPMENT_DETECTION
# Prototipo AECO CV: Detección de Maquinaria y EPP en Obra 🏗️

## 1. Planteamiento del Problema
En el sector AECO, la supervisión manual del uso de Equipos de Protección Personal (EPP) y la ubicación de maquinaria pesada consume muchas horas hombre y es propensa a errores. Este modelo automatiza la detección de 19 clases (cascos, chalecos, excavadoras, trabajadores, etc.) mediante Visión por Computadora para apoyar la seguridad y logística en el sitio de construcción.

## 2. Clases y Reglas de Etiquetado
El modelo detecta 19 clases con cajas delimitadoras (Bounding Boxes), incluyendo:
* `Hard Hat ON` / `Hard Hat OFF` (Control de cascos)
* `Safety Vest ON` / `Safety Vest OFF` (Control de chalecos reflectantes)
* Maquinaria: `Excavator`, `Dump Truck`, `Front End Loader`, etc.
* Personal: `Worker`, `Person`.

## 3. Dataset y Evidencias
* **Dataset Base:** Construction Equipment Computer Vision Model (Roboflow Universe).
* **Split de Entrenamiento:** 80% Train, 20% Valid/Test.
* **Evidencias:** Las imágenes con las predicciones del modelo se encuentran en la carpeta `/results/evidence/`.
* **Análisis y Gobernanza:** Los análisis de fallos y checklist de ética/privacidad se encuentran en la carpeta `/docs/`.

## 4. Checklist de Reproducibilidad (Cómo reproducir)
Este proyecto puede reproducirse 100% en la nube utilizando Google Colab, sin necesidad de instalaciones locales.
1. Abre Google Colab y carga el notebook ubicado en `/notebooks/entrenamiento_yolov8.ipynb`.
2. Asegúrate de configurar el entorno con Aceleración por Hardware (`T4 GPU`).
3. El código instalará automáticamente `ultralytics`.
4. Ejecuta las celdas en orden. El dataset se descargará vía API.
* **Modelo Variante:** YOLOv8n (Nano - para inferencia rápida en dispositivos de borde).
* **Parámetros:** Epochs: 30 | Batch: 16 | Imgsz: 640
* **Versión Ultralytics:** Recomendada `8.0.196` o superior.

## 5. Resumen de Resultados
El modelo se entrenó con éxito por 30 épocas. Las curvas completas están en `/results/results.png`.
* **Conclusión Clave 1:** El modelo logra converger rápidamente identificando bien las clases más frecuentes (Workers y maquinaria grande).
* **Conclusión Clave 2:** Tiene dificultades con clases de menor tamaño como guantes (`Gloves`) si la imagen no tiene suficiente resolución (`imgsz`).
