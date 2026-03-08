# Checklist de Gobernanza y Licencias

### 1. Privacidad y Consentimiento
* **Estado:** Las imágenes provienen de un dataset público.
* **Acción en producción:** Para la implementación en un sitio de construcción real, se deberá aplicar una capa de pre-procesamiento para difuminar los rostros de los trabajadores, enfocando el modelo únicamente en la detección de EPP (Equipos de Protección Personal) y maquinaria.

### 2. Minimización de Datos
* El sistema está diseñado para extraer únicamente metadatos de detección (clase, confianza y bounding box). No se almacena metraje de video continuo, minimizando el almacenamiento de datos personales.

### 3. Declaración de Limitaciones
* **Cuándo NO usar:** Este modelo es una herramienta de asistencia ("human-in-the-loop"). NO debe utilizarse para emitir sanciones automáticas a los trabajadores, ni para reemplazar la figura del prevencionista de riesgos o supervisor de seguridad en obra. Su precisión actual no permite auditorías legales automatizadas.

### 4. Nota de Riesgos (FN vs FP)
* En este contexto AECO, un **Falso Negativo** (no detectar la falta de un casco o chaleco) representa un riesgo crítico de seguridad. Se prefiere calibrar el umbral de confianza para tolerar algunos **Falsos Positivos** (alertas de seguridad innecesarias) a cambio de minimizar los Falsos Negativos en situaciones de riesgo vital.

### 5. Licencia y Derechos del Dataset
* **Licencia del Repositorio:** MIT License (Uso abierto con atribución).
* **Derechos del Dataset:** El dataset "Construction Equipment" original está bajo licencia CC BY 4.0, de uso público mediante Roboflow Universe.
