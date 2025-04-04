# S2S-AI QGIS Plugin

The **S2S-AI** plugin allows you to segment elements directly in QGIS using **MobileSAM**, a lightweight version of Meta AI’s Segment Anything Model (SAM). It works with Python environment and lets you generate vector masks from high-resolution geospatial imagery, suitable for applications in cultural heritage, remote sensing, and more.

---

## 🔧 Installation Guide

### 1. Environment Setup

This step ensures that required libraries are installed and avoids conflicts with system Python installations.

- Download and install [Anaconda](https://www.anaconda.com/download/success).
- Open the **Anaconda Prompt** and create a new environment:

```bash
conda create --name sam_qgis_env python=3.10
conda activate sam_qgis_env
```

- Install PyTorch according to your CUDA version:  
  → [https://pytorch.org/get-started/locally](https://pytorch.org/get-started/locally)  
  Check your CUDA version with `nvidia-smi`.

- Install required libraries:

```bash
pip install opencv-python numpy flask pycocotools timm
pip install git+https://github.com/ChaoningZhang/MobileSAM.git
```

---

### 2. Plugin Installation in QGIS

- Download the plugin ZIP: `S2S-AI-MobileSAM.zip`
- Download the MobileSAM weights:  
  [`mobile_sam.pt`](https://github.com/ChaoningZhang/MobileSAM/blob/master/weights/mobile_sam.pt)  

#### Install in QGIS:

- Open QGIS → `Plugins` → `Manage and Install Plugins…`
- From the left bar, select **Install from ZIP** → browse for `S2S-AI-MobileSAM.zip`
- Click **Install Plugin**
- If a warning appears, press **Yes**

---

## 🚀 How to Use the Plugin

Once installed, you will see 3 new buttons in the QGIS top bar:

![Menu Qgis](assets/toolbar.png)


### First-Time Setup:

1. Click **Configuration**
2. Set the following:
   - **Pt File** → select `mobile_sam.pt`
   - **Conda Environment Path**  
     - On Linux/Mac: `which python`  
     - On Windows: `where python` (choose the line with `sam_qgis_env`)

3. Click the **Start** button  
   → If it turns into **Stop** (green), the Plugin has started successfully

### Segmentation

- Click the **Segment** button
- Choose:
  - Density (higher = more detailed, slower)
  - Output layer: new or existing
  - Transparency of output masks

→ The plugin will segment everything visible on the screen. Hide other layers to avoid re-segmentation.

### Important

- When done, click the **Start/Stop** button before closing QGIS.

---

## 📝 Considerations

- You only need to configure the environment path and model file once.

---

## 📸 Screenshots

![Sc1](assets/Picture1.png)

![Sc2](assets/Picture2.png)

---

## 📂 License

MIT


---

## 📚 Citation

If you use this plugin or dataset, please cite:

Lucho, S., Treuillet, S., Desquesnes, X., Leconge, R., & Brunetaud, X. (2024).  
**Weakly Supervised SVM-Enhanced SAM Pipeline for Stone-by-Stone Segmentation of the Masonry of the Loire Valley Castles**.  
*Journal of Imaging, 10(6), 148.* https://doi.org/10.3390/jimaging10060148

```bibtex
@article{lucho_weakly_2024,
  title = {Weakly {Supervised} {SVM}-{Enhanced} {SAM} {Pipeline} for {Stone}-by-{Stone} {Segmentation} of the {Masonry} of the {Loire} {Valley} {Castles}},
  volume = {10},
  copyright = {https://creativecommons.org/licenses/by/4.0/},
  issn = {2313-433X},
  url = {https://www.mdpi.com/2313-433X/10/6/148},
  doi = {10.3390/jimaging10060148},
  language = {en},
  number = {6},
  urldate = {2025-03-08},
  journal = {Journal of Imaging},
  author = {Lucho, Stuardo and Treuillet, Sylvie and Desquesnes, Xavier and Leconge, Remy and Brunetaud, Xavier},
  month = jun,
  year = {2024},
  pages = {148}
}
```

---

## 🙏 Acknowledgement

This project is based on and benefits from [MobileSAM](https://github.com/ChaoningZhang/MobileSAM).
