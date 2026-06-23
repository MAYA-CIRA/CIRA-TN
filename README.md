# 🌊 Coastal Inundation Risk Assessment for Tamil Nadu (CIRA-TN)

Welcome to the **Coastal Inundation Risk Assessment Tool** — a Python-based geospatial toolkit designed to assess and map coastal inundation risk along the **Tamil Nadu coastline**, integrating remote sensing data, ALTM elevation models, and green & gray coastal infrastructure. Built for researchers, planners, and policymakers to understand flood risk under sea-level rise scenarios. 🌍🌡️

> **Published in:** *Journal of Coastal Conservation (2025) 29:65*
> **DOI:** https://doi.org/10.1007/s11852-025-01169-z

---

## 🚀 Features

- 🗺️ **DEM Elevation Extraction** — Merges multiple ALTM DEM tiles and extracts 1m-interval elevation contours
- 📐 **Shoreline Buffer Generation** — Generates land-side buffer zones at 500m, 1000m, 1500m, and 2000m intervals
- ⚠️ **Inundation Risk Classification** — Classifies coastal zones into High, Moderate, and Low risk using elevation and distance from shoreline
- 🌿 **Green & Gray Infrastructure Integration** — Reclassifies risk zones incorporating sand dunes, mangroves, and engineered coastal structures
- 📦 **Multi-format Outputs** — Produces Shapefiles, GeoJSON, and merged GeoTIFF files

---

## 🧭 Project Structure

```
CIRA-TN/
├── notebooks/
│   ├── 01_Elevation_Extraction.ipynb       # ALTM DEM merge, contour extraction, polygon conversion
│   ├── 02_Buffer_Generator.ipynb           # Shoreline buffer zones (500–2000m)
│   ├── 03_CIRA_Without_Structures.ipynb    # Risk classification without coastal infrastructure
│   └── 04_CIRA_With_Structures.ipynb       # Risk reclassification with sand dunes & structures
├── ancillary_data/
│   └── (Input shapefiles, DEM tiles, infrastructure data)
├── outputs/
│   └── (Generated shapefiles, GeoJSON, risk maps)
├── .gitignore
├── requirements.txt
└── README.md
```

---

## 🔬 Methodology

The coastal inundation risk is classified into three categories — **High**, **Moderate**, and **Low** — based on two key parameters:

| Distance from Shoreline | Elevation 0–1 m | Elevation 1–2 m | Elevation > 2 m |
|------------------------|-----------------|-----------------|-----------------|
| 0 – 500 m              | 🔴 High          | 🟡 Moderate      | 🟢 Low           |
| 500 – 1000 m           | 🟡 Moderate      | 🟢 Low           | 🟢 Low           |
| 1000 – 1500 m          | 🟢 Low           | 🟢 Low           | 🟢 Low           |
| 1500 – 2000 m          | 🟢 Low           | 🟢 Low           | 🟢 Low           |

Risk zones are then **reclassified** considering the presence of:
- 🌿 **Green Infrastructure** — Mangroves (Sentinel-2, 10m), Sand Dunes (ALTM, 1m)
- 🏗️ **Gray Infrastructure** — Seawalls, Groins, Jetties, Fishing Harbors, Ports, Piers (NCCR Field Survey, 2021)

---

## 📊 Key Results

| Scenario | High Risk | Moderate Risk | Low Risk |
|---|---|---|---|
| **With Green & Gray Infrastructure** | 1.94% | 43.54% | 54.52% |
| **Without Green & Gray Infrastructure** | 4.14% | 41.34% | 54.52% |

> 🔑 The northern Tamil Nadu coast (Chennai, Thiruvallur, Kancheepuram, Nagapattinam) has significantly higher inundation risk than the southern coast.

---

## 🛠️ Installation & Usage

**1. Clone the repository:**
```bash
git clone https://github.com/Maya-Coast/CIRA-TN.git
cd CIRA-TN
```

**2. Install dependencies:**
```bash
pip install -r requirements.txt
```

**3. Run the notebooks in order:**
```bash
jupyter notebook notebooks/01_Elevation_Extraction.ipynb
jupyter notebook notebooks/02_Buffer_Generator.ipynb
jupyter notebook notebooks/03_CIRA_Without_Structures.ipynb
jupyter notebook notebooks/04_CIRA_With_Structures.ipynb
```

---

## 🧠 Requirements

```
numpy
pandas
geopandas
shapely
rasterio
fiona
pyproj
scipy
matplotlib
jupyter
```
Install all with:
```bash
pip install -r requirements.txt
```

---

## 🗂️ Data Used

| Parameter | Data Source | Resolution |
|---|---|---|
| Elevation | ALTM (Airborne LiDAR Terrain Mapping) | 1 m |
| Mangroves | Sentinel-2 | 10 m |
| Sand Dunes | ALTM | 1 m |
| Gray Structures | In-situ field survey (NCCR, 2021) | — |

---

## 📸 Study Area

The study covers the entire **Tamil Nadu coastline (~1,076 km)** along the Bay of Bengal, extending **2 km inland** from the shoreline, covering all 13 coastal districts from Thiruvallur in the north to Kanyakumari in the south.

---

## 📄 Citation

If you use this tool in your research, please cite:

```bibtex
@article{mayamanikandan2025cira,
  title     = {Evaluating coastal vulnerability: mapping inundation risk in Tamil Nadu with and without coastal protection},
  author    = {Mayamanikandan, T. and Usha, Tune and Dash, S.K. and Raju, S.K. and Mahendra, R.S. and Ramana Murthy, M.V.},
  journal   = {Journal of Coastal Conservation},
  volume    = {29},
  pages     = {65},
  year      = {2025},
  publisher = {Springer},
  doi       = {10.1007/s11852-025-01169-z}
}
```

---

## 🏛️ Affiliations

- **National Centre for Coastal Research (NCCR), MoES, Chennai, India**
- **Indian National Centre for Ocean Information Services (INCOIS), MoES, Hyderabad, India**

---

## 📬 Contact

For questions, feedback, feel free to open an issue or reach out:

📧 **T. Mayamanikandan** — tmayaceg@gmail.com

---

## 🙏 Acknowledgements

We sincerely thank **Dr. M. Ravichandran**, Secretary, Ministry of Earth Sciences, for his continuous support. We also gratefully acknowledge the **European Space Agency** for providing satellite data used in this study.

*NCCR Manuscript Contribution No. NCCR/MS/443*
