# Prototipo-ESP32-CAM

## Introducción
Este documento presenta el reporte técnico del prototipo desarrollado para la asignatura de Introducción a las TICs. El proyecto consiste en un sistema de detección de objetos en tiempo real utilizando la cámara ESP32-CAM, con indicadores visuales (LEDs) y (Display) para notificar al usuario sobre los objetos identificados.

## Objetivo
El objetivo principal de este proyecto es diseñar, implementar e integrar un prototipo funcional capaz de:
- Capturar imágenes con la ESP32-CAM
- Realizar detección de objetos mediante un modelo pre-entrenado
- Mostrar el resultado por un servidor web o captura local
- Demostrar estabilidad básica y funcionamiento continuo

## Materiales
### Hardware
- ESP32-CAM (AI Thinker)
- Módulo FTDI o CP2102 para programación
- Cable USB
- Jumpers hembra-hembra
- Pantalla OLED SSD1306
- (Opcional) Protoboard
### Software y Librerías 
IDE/Entorno de desarrollo:  Arduino IDE
Librerías esenciales: 
- **Arduino.h** – Funciones principales del entorno Arduino.
- **WiFi.h** – Conexión WiFi.  
- **Wire.h** – Comunicación I2C para la pantalla OLED.  
- **Adafruit_GFX.h** – Librería gráfica base.  
- **Adafruit_SSD1306.h** – Control de la pantalla OLED.  
- **Plataforma de ML:** Edge Impulse (Para la generación del modelo de inferencia).
- **Librería generada por Edge Impulse** (contiene el modelo entrenado, en este caso Archivo `Librería/Lentes.zip` ).

## Desarrollo del sistema
### Electrónica y Armado 
El prototipo se basa en el siguiente esquema de conexión, garantizando el montaje final y la correcta integración de los componentes (cámara, display, LEDs)
* [**VER ESQUEMA DE CONEXIÓN:**] Archivo `Electrónica/Esquema-conexion.png`
* [**VER EVIDENCIA DEL ARMADO:**] Archivo `Electrónica/Foto-Montaje-Final.jpg`

### Software y Código
El código completo y organizado se encuentra en la carpeta `/Código`. Incluye comentarios esenciales para su comprensión.
Procedimiento para crear la clase en Edge Impulse (resumen profesional)

### Modelo en Edge Impulse
Se creó un nuevo proyecto de tipo Object Detection en Edge Impulse.
Se generó una sola clase llamada "objetos", la cual agrupa ambos elementos a detectar.
Se capturaron y subieron imágenes de los dos objetos en diferentes ambientes, posiciones y distancias.
Todas las imágenes fueron etiquetadas con la misma clase (objetos).
En Labeling Queue, se dibujaron los bounding boxes alrededor de cada objeto presente.
Se entrenó el modelo hasta obtener precisión suficiente y sin sobreajuste.
En la sección Deployment, se exportó como Arduino Library (.zip).

## Instrucciones de Compilación y Flasheo para ESP32-CAM
1. Abrir Arduino IDE
2. Instalar soporte para ESP32:
3. File > Preferences > Additional Board URLs
**URL para instalar soporte ESP32 en Arduino IDE:**
`https://espressif.github.io/arduino-esp32/package_esp32_index.json`
4. Seleccionar placa: AI Thinker ESP32-CAM
5. Configurar velocidad: Upload speed: 115200
6. Conectar FTDI → ESP32-CAM y mantener GPIO0 a GND para flasheo
7. Cargar el programa y reiniciar el módulo

## Resultados
El prototipo se probó con éxito, demostrando su estabilidad básica y funcionamiento.

**Detección:** El sistema identifica la clase [lentes-marcatexto] correctamente (en este caso). Al detectar un objeto, la etiqueta correspondiente aparece claramente en el display.
**Indicadores:** Un LED distinto se enciende para cada objeto reconocido, y el LED rojo permanece encendido cuando no se detecta nada.

[**VER EVIDENCIAS DE PRUEBAS Y FUNCIONAMIENTO:**] Consulte los archivos en la carpeta `/Evidencias` (Capturas, videos y logs)

## Conclusión 
El proyecto permitió implementar un sistema funcional de detección de objetos con la ESP32-CAM, comprobando que el módulo es capaz de capturar imágenes y ejecutar un modelo ligero con buen desempeño. Se logró una comunicación estable, pruebas exitosas y una comprensión práctica del uso de visión por computadora

## Trabajos Futuros 

- Implementar varias clases independientes
- Mejorar iluminación y calidad de imagen

## Referencias Bibliográficas 

[1] Espressif Systems, “Guía Técnica del Módulo ESP32-CAM,” Documentación oficial, 2023. Disponible en: https://www.espressif.com/es/support/documents/technical-documents
[2] Arduino, “Instalación del ESP32 en Arduino IDE,” Tutorial oficial, 2024. Disponible en: https://support.arduino.cc/hc/es
[3] Edge Impulse, “Guía para el Entrenamiento de Modelos con Visión,” Documentación en español, 2024. Disponible en: https://docs.edgeimpulse.com/docs/es/
[4] Adafruit Industries, “Uso de la Librería Adafruit GFX y Pantallas OLED,” Manual técnico, 2023. Disponible en: https://learn.adafruit.com
[5] Edge Impulse, “FOMO: Faster Objects, More Objects — a Lightweight Object Detection Model,” Documentation, 2023. Disponible en: https://docs.edgeimpulse.com 
