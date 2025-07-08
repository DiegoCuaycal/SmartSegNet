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

| Métrica                  | Jorge Pazos (U-Net) | 🔥 Nuestro Modelo (SmartSegNet) |
|--------------------------|---------------------|-----------------------------|
| Arquitectura             | Residual U-Net      | EfficientNetV2-S + ASPP + ConvTranspose2d |
| Resolución de entrada    | 128 × 128           | 256 × 256 píxeles          |
| Épocas de entrenamiento  | N/D                 | **320**                    |
| Mejor mIoU               | 0.8053              | **0.8188**                 |
| Dice Coefficient         | 0.8763              | **0.8721**                 |
| Train Loss final         | N/D                 | **0.0734**                 |
| Val Loss final           | N/D                 | **0.0919**                 |
| Parámetros totales       | N/D                 | **32,961,810**             |
| Checkpoint final         | N/D                 | **222.70 MB**              |

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

## 📦 Descargar el Modelo Entrenado

👉 Puedes descargar el modelo `.pth` entrenado con mejor mIoU desde la release oficial:

🔗 [Releases > v1.0.0](https://github.com/DiegoCuaycal/SmartSegNet/releases/tag/v1.0.0)

---

