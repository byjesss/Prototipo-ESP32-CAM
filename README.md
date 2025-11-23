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
- Arduino IDE
### Software y Librerías 
IDE/Entorno de desarrollo:  Arduino IDE
Librerías esenciales:  **Arduino.h** – Funciones principales del entorno Arduino.  
- **WiFi.h** – Conexión WiFi.  
- **Wire.h** – Comunicación I2C para la pantalla OLED.  
- **Adafruit_GFX.h** – Librería gráfica base.  
- **Adafruit_SSD1306.h** – Control de la pantalla OLED.  
- **ei_run_classifier.h** – Motor de inferencia para Edge Impulse (modelo de IA).
