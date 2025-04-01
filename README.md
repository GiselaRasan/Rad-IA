# RadIA: Clasificación y Detección de Fracturas y Enfermedades Torácicas

## Descripción del Proyecto
RadIA es un sistema basado en redes neuronales para la clasificación y análisis de radiografías, que permite determinar la ubicación anatómica de la imagen, identificar fracturas y detectar enfermedades torácicas. Además de la clasificación, el modelo proporciona una estimación de la severidad de la condición detectada en un rango de 0 a 1.

## Metodología
1. **Preprocesamiento de Imágenes**
   - Conversión a escala de grises.
   - Redimensionamiento a 320x320 px.
   - Normalización del rango de valores (0-1).
   - Corrección de contraste y brillo.

2. **Clasificación Anatómica**
   - Se utiliza `Main.keras` para clasificar la imagen en una de tres regiones:
     - **Tronco Central**
     - **Extremidades Altas**
     - **Extremidades Bajas**

3. **Clasificación Específica**
   - Si la imagen es de **Tronco Central**, se usa `Central.keras` para clasificar entre:
     - Cráneo, Pecho, Pelvis.
   - Si la imagen es de **Extremidades Altas**, se usa `Alta.keras` para clasificar entre:
     - Hombro, Codo, Mano.
   - Si la imagen es de **Extremidades Bajas**, se usa `Baja.keras` para clasificar entre:
     - Coxis-Femoral, Rodilla, Pie.

4. **Detección de Fracturas y Enfermedades**
   - Para fracturas:
     - `AltasFracture.keras` (Extremidades Altas)
     - `BajasFracture.keras` (Extremidades Bajas)
     - `HipFracture.keras` (Cadera)
   - Para enfermedades torácicas:
     - `ChestDisease.keras`, que clasifica entre:
       - Absceso, ARDS, Atelectasia, Cardiomegalia, Neumonía, Tuberculosis, etc. (ver imagen de referencia).

5. **Estimación de Severidad**
   - El modelo de predicción de severidad está diseñado para abordar el problema de predicción de la gravedad o intensidad de una condición médica a partir de imágenes. La predicción de la severidad se trata como una tarea de regresión, lo que significa que el modelo genera un valor continuo que cuantifica la severidad de la condición diagnosticada.

6. **Visualización de Resultados**
   - La imagen procesada se muestra junto con la clasificación obtenida.

## Instalación
1. Clonar el repositorio:
   ```bash
   git clone https://github.com/tu_usuario/RadIA.git
   cd RadIA
   ```
2. Instalar dependencias:
   ```bash
   pip install -r requirements.txt
   ```
3. Descargar los modelos preentrenados desde GitHub o Drive y colocarlos en la carpeta `models/`.

## Uso
Ejecutar el archivo Jupyter Notebook para realizar predicciones:
```bash
jupyter notebook RadIA.ipynb
```
O ejecutar el script en Python:
```python
python predict.py --image path/to/image.png
```

## Autores
- Gisela Briseida Ramirez Santiago


