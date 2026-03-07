# Análisis de Errores - Modelo de Visión AECO

A partir de la inferencia realizada en las imágenes de validación y de prueba, se identificaron los siguientes patrones:

### 3 Falsos Positivos (FP)
1. **Confusión por color:** El modelo ocasionalmente detecta objetos del fondo (como barriles o conos) como si fueran chalecos de seguridad (`Safety Vest ON`) debido a la similitud cromática (naranja/amarillo reflectante).
2. **Geometría similar:** Se detectaron falsos positivos donde partes redondeadas de la maquinaria pesada fueron clasificadas como cascos (`Hard Hat ON`).
3. **Clasificación cruzada de maquinaria:** Confusión esporádica entre `Front End Loader` (cargador frontal) y `Excavator` (excavadora) cuando la imagen está tomada desde un ángulo muy cerrado donde no se aprecia el brazo de la máquina.

### 3 Falsos Negativos (FN)
1. **Oclusión severa:** No se detectan trabajadores (`Worker`) ni su equipo de protección cuando están parcialmente tapados por la maquinaria, andamios o zanjas.
2. **Distancia y escala:** Trabajadores o equipos ubicados al fondo de la imagen, con muy pocos píxeles de resolución, no son detectados (pérdida de features al redimensionar a `imgsz=640`).
3. **Condiciones de iluminación:** Falla en la detección de cascos (`Hard Hat`) en zonas de sombra profunda proyectada por las estructuras en construcción.

### 3 Mejoras Prioritarias de Datos
1. **Aumentación de datos (Data Augmentation):** Aplicar variaciones de brillo y contraste al dataset original para simular diferentes horas del día en la obra.
2. **Imágenes de Dron (Ángulos picados):** Incorporar imágenes aéreas, ya que actualmente el dataset es mayoritariamente a nivel de suelo, lo cual no es representativo de las cámaras de seguridad en grúas.
3. **Recortes (Crops) en alta resolución:** Entrenar con parches de imágenes de alta resolución para que los trabajadores lejanos no pierdan calidad al escalar la imagen entera.
