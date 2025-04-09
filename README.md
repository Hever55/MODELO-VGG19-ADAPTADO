
- **Tamaño de imagen**: 256x256 px  
- **Ubicación en Google Drive**:
  - `/content/drive/MyDrive/entrenamiento`
  - `/content/drive/MyDrive/validacion`
  - `/content/drive/MyDrive/prueba`

---

## Modelo

Se utilizó el modelo `VGG19` con pesos preentrenados en `ImageNet` y sin las capas superiores (`include_top=False`).  
Se aplicó **fine-tuning** descongelando las últimas capas.

### Arquitectura adicional:
- `GlobalAveragePooling2D`
- `Dense(512) + BatchNormalization + Dropout(0.5)`
- `Dense(256) + BatchNormalization + Dropout(0.3)`
- `Dense(3, activation='softmax')`

---

##  Aumento de Datos

Utilizando `ImageDataGenerator` con los siguientes parámetros:

- `rotation_range=30`
- `width_shift_range=0.2`
- `height_shift_range=0.2`
- `shear_range=0.2`
- `zoom_range=0.3`
- `horizontal_flip=True`
- `vertical_flip=True`
- `brightness_range=[0.8, 1.2]`

---

##  Entrenamiento

- **Optimización**: `Adam(lr=0.0001)`
- **Loss**: `categorical_crossentropy`
- **Métrica**: `accuracy`
- **Batch Size**: 32
- **Épocas**: hasta 50
- **Callbacks**:
  - `EarlyStopping(patience=15)`
  - `ReduceLROnPlateau(patience=5, factor=0.5, min_lr=1e-5)`

---

##  Evaluación

Se evaluó en conjuntos de validación y prueba con las siguientes métricas:

- **Accuracy**
- **Cohen's Kappa**
- **Matthews Correlation Coefficient (MCC)**
- **Balanced Accuracy**
- **Reporte de Clasificación**
- **Matriz de Confusión**
- **Curvas ROC por clase**
- **AUC promedio**

---

##  Visualizaciones

- Curvas de entrenamiento (precisión y pérdida)
- Matriz de confusión en estilo profesional con anotaciones
- Curvas ROC y AUC por clase

---

##  Requisitos

Este proyecto fue desarrollado y probado en **Google Colab**. Requiere las siguientes librerías:

- `TensorFlow`
- `scikit-learn`
- `matplotlib`
- `seaborn`
- `numpy`
- `pickle`

---

##  Cómo usar

1. Sube tus carpetas de imágenes a tu Google Drive.
2. Ajusta las rutas en el código si es necesario.
3. Ejecuta el script en Google Colab.
4. Observa las métricas y visualizaciones generadas.

---

## 📌 Autor

Este proyecto forma parte de un estudio sobre clasificación visual de semillas.  
**¡Recuerda que la vida es valiosa!** – *Memento Mori*
