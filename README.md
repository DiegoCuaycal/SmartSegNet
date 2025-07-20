# 🌱 SmartSegNet: Segmentación Semántica de Malezas UAV con Deep Learning

<p align="center">
  <img src="SmartSegNet.png" alt="SmartSegNet Logo" width="300"/>
</p>


## 📘 Descripción del Proyecto

Este proyecto implementa un modelo de segmentación semántica optimizado para la detección automática de malezas en cultivos de papa, usando imágenes aéreas tomadas con drones (UAVs).  
El objetivo fue superar las métricas obtenidas en el trabajo de **Jorge Pazos** ([Repositorio UTN](https://repositorio.utn.edu.ec/handle/123456789/16794)), quien utilizó una arquitectura **Residual U-Net**.

> 📌 **SmartSegNet** propone una arquitectura moderna basada en EfficientNetV2-S + ASPP + Decoder convolucional, logrando mejoras en mIoU, Dice Score y eficiencia computacional.

---

## ⚔️ Comparativa de Resultados


| **Aspecto Evaluado**              | **Proyecto de Jorge Pazos**                | **Nuestro Proyecto Desarrollado (SmartSegNet)**             | **¿Mejora?**                  |
|-----------------------------------|-------------------------------------------|-------------------------------------------------------------|-------------------------------|
| **Total de parámetros**           | 134,901,524                               | 32,961,810                                                  | ✅ Sí (-75.56%)               |
| **Tamaño del checkpoint (.pth)**  | 514.61 MB                                 | 222.70 MB                                                   | ✅ Sí (-56.74%)               |
| **Tamaño del archivo para inferencia** | 171.54 MB                            | ~87.6 MB (estimado)                                         | ✅ Sí (-49%)                  |
| **Resolución de entrada**         | 128 × 128                                 | 256 × 256 píxeles                                           | ✅ Sí (mayor resolución)      |
| **Épocas de entrenamiento**       | N/D                                       | 320                                                         | ✅ Sí                         |  |
| **Mean IoU**                      | 0.8053                                    | **0.82**                                                  | ✅ Sí (+0.0147)               |
| **Train Loss final**              | N/D                                       | 0.0734                                                      | ✅ Sí                         |
| **Val Loss final**                | N/D                                       | 0.0919                                                      | ✅ Sí                         |
| **Arquitectura utilizada**        | Residual U-Net (TensorFlow)               | EfficientNetV2-S + ASPP + ConvTranspose2d (PyTorch)         | ✅ Mejorada e interpretada    |
| **Preparado para drones / UAVs**  | No especificado                          | ✅ Sí (modelo liviano y portable)                           | ✅ Sí                         |


---

## 🧠 Arquitectura del Modelo

- ✅ **Backbone:** EfficientNetV2-S
- ✅ **ASPP:** Atrous Spatial Pyramid Pooling (multi-escala)
- ✅ **Decoder:** Convoluciones `ConvTranspose2d`
- ✅ **Resolución:** 256×256 píxeles
- ✅ **Función de pérdida:** Focal Loss + Dice Loss (combinada)
- ✅ **Optimización:** Adam + ReduceLROnPlateau
- ✅ **Entrenamiento con precisión mixta:** Sí (`torch.cuda.amp`)

---

## 💻 Recursos Técnicos Utilizados

- **Entorno:** Google Colab Pro
- **Framework:** PyTorch 2.x
- **Sistema Operativo:** Linux (Ubuntu 20.04)
- **Acelerador:** GPU NVIDIA Tesla T4 (16 GB VRAM)
- **RAM disponible:** ~13 GB
- **CUDA version:** 11.x
- **Entrenamiento mixto:** activado con `torch.cuda.amp` para eficiencia

---

## 📁 Dataset

📦 Dataset agrícola de malezas en cultivos de papa  
Autor: Jorge Pazos  
📥 Repositorio original:  
[https://github.com/JorgePazos-git/Dataset-of-weeds-in-potato-crops-in-the-province-of-Carchi-and-Imbabura-in-.git](https://github.com/JorgePazos-git/Dataset-of-weeds-in-potato-crops-in-the-province-of-Carchi-and-Imbabura-in-.git)

📌 Clases:
- `0`: fondo
- `1`: lengua de vaca
- `2`: diente de león
- `3`: kikuyo
- `4`: otras malezas
- `5`: patata

---
## 🧪 Evaluación

El modelo fue evaluado utilizando las métricas **mIoU** (*mean Intersection over Union*) y **Dice Score**, que son ampliamente utilizadas en tareas de segmentación semántica para medir la superposición entre la predicción y la máscara real.

- 🔷 **mIoU**: Evalúa el promedio de la intersección entre la predicción y la verdad de terreno dividido por su unión, por clase.
- 🔷 **Dice Score**: Mide la similitud entre las dos máscaras, favoreciendo coincidencias exactas.

## ▶️ Reproducir la evaluación

Para ejecutar la evaluación con el modelo entrenado:

```bash
python evaluate.py --weights checkpoint_focal_dice.pth
```
---
## 📦 Descargar el Modelo Entrenado

👉 Puedes descargar el modelo `.pth` entrenado con mejor mIoU desde la release oficial:

🔗 [Releases > v1.0.0](https://github.com/DiegoCuaycal/SmartSegNet/releases/tag/v1.0.0)

---

