# ProyectoMachineLearning1B
# Parte 1b - Alineación de Transcripción y Detección de Errores Fonéticos

Este módulo corresponde a la **Parte 1b** del proyecto de alineación automática de audio con transcripciones, basado en etiquetas de IPU y transcripción generada por ASR (Whisper). Su propósito es alinear automáticamente el contenido textual con los segmentos de voz y detectar errores fonéticos entre el audio y la transcripción.

---

## 🧩 Funcionalidad

### 1. Alineación ASR por IPU
- Utiliza la herramienta `Whisper` para transcribir **cada intervalo IPU** (Inter-Pausal Unit).
- La transcripción por segmento se guarda en un nuevo tier `Transc` dentro del archivo `.TextGrid`.

### 2. Detección de errores fonéticos
- Usa `espeak-ng` para obtener representaciones fonéticas del texto.
- Compara las IPUs originales con las transcripciones ASR para identificar diferencias significativas (palabras omitidas, cambiadas o mal reconocidas).
- Los errores se almacenan en un nuevo tier `TranscErrors` en el `.TextGrid`.

### 3. Exportación de errores
- Además de la marca en el `TextGrid`, se genera un archivo `.txt` con los errores fonéticos detectados por cada segmento.

---

## ⚙️ Mejoras implementadas

- **Carga única del modelo Whisper** para mejor rendimiento.
- **Manejo robusto de errores** en cada segmento: si una IPU falla, no detiene el resto del procesamiento.
- **Transcripción ignorada para segmentos menores a 0.2s**, mejorando la precisión general.
- **Generación automática del tier `TranscErrors`** con alineación fonética.
- **Exportación silenciosa**: sin mensajes en consola, ideal para procesamiento por lotes.
- **Estructura modular y reutilizable** de funciones.

---

