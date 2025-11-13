# 🌍 Drought Impact Analysis on Agricultural Productivity in India
## A Multi-Scale Time Series Analysis of Groundwater and Agricultural Indicators

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Google Earth Engine](https://img.shields.io/badge/Google%20Earth%20Engine-Enabled-green.svg)](https://earthengine.google.com/)

---

## 📋 Table of Contents
- [Project Overview](#project-overview)
- [Research Highlights](#research-highlights)
- [Datasets](#datasets)
- [Project Structure](#project-structure)
- [Installation & Setup](#installation--setup)
- [Usage Guide](#usage-guide)
- [Key Findings](#key-findings)
- [Technologies Used](#technologies-used)
- [Contributing](#contributing)
- [License](#license)
- [Citation](#citation)
- [Contact](#contact)

---

## 🎯 Project Overview

This repository contains a comprehensive **time series analysis** investigating the impact of drought on agricultural productivity across three drought-prone regions in India:

1. **Marathwada Region** (Maharashtra) - 8 districts
2. **Bundelkhand Region** (Uttar Pradesh & Madhya Pradesh) - 13 districts  
3. **Eastern Tamil Nadu** - 6 districts

### Research Objective
To analyze the temporal relationships between groundwater indicators (GRACE, GLDAS) and agricultural productivity metrics using advanced time series modeling techniques to understand drought impacts on crop yields from **2000-2023**.

### Key Features
- ✅ Multi-source satellite data integration (GRACE, GLDAS, MODIS)
- ✅ District-level granular analysis (27 districts total)
- ✅ 23+ years of historical data
- ✅ Comprehensive EDA with statistical tests
- ✅ Time series decomposition and forecasting models
- ✅ Agricultural crop yield correlation analysis

---

## 🔬 Research Highlights

### Study Period
- **Groundwater Data**: 2000-2023 (23 years)
- **Agricultural Data**: 1966-2014 (48 years for ICRISAT dataset)
- **Rainfall Data**: 1901-2015 (115 years)

### Methodology
1. **Data Collection**: Google Earth Engine API for satellite data extraction
2. **Exploratory Data Analysis**: Statistical tests, trend analysis, seasonality decomposition
3. **Time Series Modeling**: ARIMA, SARIMA, Prophet, LSTM
4. **Correlation Analysis**: Drought indicators vs. crop yields
5. **Spatial Analysis**: Regional comparison and drought intensity mapping

### Drought Indicators
- **GRACE**: Groundwater storage anomalies (Liquid Water Equivalent thickness)
- **GLDAS**: Root zone soil moisture
- **NDVI**: Vegetation health indices
- **Rainfall**: Precipitation patterns
- **SPEI**: Standardized Precipitation Evapotranspiration Index

---

## 📊 Datasets

### 1. **Groundwater Data** (Primary Data - Collected via Google Earth Engine)

#### GRACE (Gravity Recovery and Climate Experiment)
- **Source**: NASA GRACE Mission
- **Collection ID**: `NASA/GRACE/MASS_GRIDS/LAND`
- **Period**: 2003-2017
- **Temporal Resolution**: Monthly
- **Spatial Resolution**: ~1 degree (~111 km)
- **Variable**: Liquid Water Equivalent (LWE) thickness anomaly (cm)
- **Files**: 
  - `drought_regions_grace_2003_2008.csv` - 27 districts, 2003-2008
  - `drought_regions_grace_2009_2017.csv` - 27 districts, 2009-2017

#### GLDAS (Global Land Data Assimilation System)
- **Source**: NASA Goddard Space Flight Center
- **Collection ID**: `NASA/GLDAS/V021/NOAH/G025/T3H`
- **Period**: 2000-2002, 2018-2023
- **Temporal Resolution**: 3-hourly (aggregated to monthly)
- **Spatial Resolution**: 0.25° × 0.25° (~25 km)
- **Variable**: Root zone soil moisture (kg/m²)
- **Files**:
  - `drought_regions_gldas_2000_2002.xlsx` - Early period
  - `drought_regions_gldas_2018_2023.csv` - Recent period

### 2. **Agricultural Productivity Data** (Secondary Data)

#### ICRISAT District-Level Data
- **Source**: International Crops Research Institute for the Semi-Arid Tropics
- **Period**: 1966-2014
- **Granularity**: District-level
- **Crops Covered**: 
  - Cereals: Rice, Wheat, Sorghum, Pearl Millet, Maize, Finger Millet, Barley
  - Pulses: Chickpea, Pigeonpea, Minor Pulses
  - Oilseeds: Groundnut, Sesamum, Rapeseed, Mustard, Safflower, Castor, Linseed, Sunflower, Soybean
  - Cash Crops: Sugarcane, Cotton
  - Horticulture: Fruits, Vegetables, Potatoes, Onion
- **Metrics**: Area (1000 ha), Production (1000 tons), Yield (kg/ha)
- **File**: `ICRISAT-District Level Data (1).csv`

### 3. **Climate Data** (Secondary Data)

#### Rainfall Data
- **Source**: India Meteorological Department (IMD)
- **Period**: 1901-2015
- **Coverage**: All India, Subdivision-wise
- **Temporal Resolution**: Seasonal and Annual
- **File**: `rainfall in india 1901-2015.csv` (included in EDA notebooks)

#### NDVI Data
- **Source**: Google Earth Engine (MODIS/Landsat)
- **Period**: 1998-2013
- **Resolution**: MODIS 250m, Landsat 30m
- **File**: `NDVI_Data_1998_2013_India_Regions.xlsx`

#### SPEI Indices
- **Source**: Calculated drought indices
- **Regions**: Marathwada, Bundelkhand
- **Files**: 
  - `Marathwada_SPEI.xlsx`
  - `Bundelkhand_SPEI.xlsx`

#### CHIRPS Rainfall
- **Source**: Climate Hazards Group InfraRed Precipitation with Station data
- **Coverage**: Three study regions
- **File**: `CHIRPS_TimeSeries_ThreeRegions.xlsx`

#### Soil Moisture Data
- **Source**: IMD District-level observations
- **Period**: 2018-07 to 2025-06
- **Districts**: Bundelkhand region
- **Files**:
  - `Volumetric Soilmoisture_Monthly data for Districts for 2018-07 to 2025-06 Bundelkhand.xlsx`
  - `Volumetric Soilmoisture_Monthly data for Districts for 2018-07 to 2025-06.xlsx`

---

## 📁 Project Structure

```
drought-analysis-india/
│
├── README.md                          # This file
├── KAGGLE_UPLOAD_GUIDE.md            # Step-by-step Kaggle upload instructions
├── LICENSE                            # MIT License
│
├── notebooks/
│   ├── project_datacollection.ipynb  # Google Earth Engine data collection scripts
│   └── eda_time_series_project.ipynb # Exploratory Data Analysis notebook
│
├── dataset/
│   ├── India_Drought_Analysis_Data/  # Primary GEE-collected data
│   │   ├── drought_regions_grace_2003_2008.csv
│   │   ├── drought_regions_grace_2009_2017.csv
│   │   ├── drought_regions_gldas_2000_2002.xlsx
│   │   └── drought_regions_gldas_2018_2023.csv
│   │
│   ├── ICRISAT-District Level Data (1).csv  # Agricultural productivity data
│   ├── NDVI_Data_1998_2013_India_Regions.xlsx
│   ├── Marathwada_SPEI.xlsx
│   ├── Bundelkhand_SPEI.xlsx
│   ├── CHIRPS_TimeSeries_ThreeRegions.xlsx
│   └── Volumetric Soilmoisture_*.xlsx
│
├── dataset_after_eda/               # Cleaned/processed datasets
│   ├── eda_time_series_project.ipynb
│   └── Eda_time_series_project (1).ipynb
│
├── requirements.txt                  # Python dependencies
└── .gitignore                       # Git ignore file
```

---

## 🛠️ Installation & Setup

### Prerequisites
- Python 3.8 or higher
- Google Earth Engine account (for data collection)
- Jupyter Notebook or JupyterLab
- Git

### Step 1: Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/drought-analysis-india.git
cd drought-analysis-india
```

### Step 2: Create Virtual Environment
```bash
# Using venv
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Or using conda
conda create -n drought-analysis python=3.8
conda activate drought-analysis
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Setup Google Earth Engine (Optional - only for data collection)
```bash
# Authenticate with Google Earth Engine
earthengine authenticate

# In Python
import ee
ee.Authenticate()
ee.Initialize()
```

---

## 📖 Usage Guide

### 1. Data Collection (Optional - Datasets already provided)

The `project_datacollection.ipynb` notebook contains scripts to collect data from Google Earth Engine.

**⚠️ Note**: The successful data collection code is in **Cell 13** (Batch Export approach). Earlier cells have authentication/processing issues.

```python
# Key working cell: Batch Export for GRACE/GLDAS
# This cell creates 4 batched exports:
# - Batch 1: GLDAS 2000-2002
# - Batch 2: GRACE 2003-2008
# - Batch 3: GRACE 2009-2017
# - Batch 4: GLDAS 2018-2023
```

**To run data collection:**
1. Open `notebooks/project_datacollection.ipynb`
2. Authenticate with Google Earth Engine
3. Run Cell 13 (Batch Export cell)
4. Go to GEE Code Editor → Tasks tab
5. Click RUN for each export task
6. Data will be saved to your Google Drive

### 2. Exploratory Data Analysis

Open the EDA notebook to explore the datasets:

```bash
jupyter notebook dataset_after_eda/eda_time_series_project.ipynb
```

**Key analyses included:**
- Rainfall trends (1901-2015)
- Seasonal decomposition
- Stationarity tests (ADF, KPSS)
- Correlation analysis
- Missing value treatment
- Visualization of temporal patterns

### 3. Working with Datasets

```python
import pandas as pd

# Load GRACE data
grace_2003_2008 = pd.read_csv('dataset/India_Drought_Analysis_Data/drought_regions_grace_2003_2008.csv')
grace_2009_2017 = pd.read_csv('dataset/India_Drought_Analysis_Data/drought_regions_grace_2009_2017.csv')

# Load GLDAS data
gldas_2018_2023 = pd.read_csv('dataset/India_Drought_Analysis_Data/drought_regions_gldas_2018_2023.csv')

# Load agricultural data
icrisat_data = pd.read_csv('dataset/ICRISAT-District Level Data (1).csv')

# Filter for specific region
marathwada_districts = ['Aurangabad', 'Beed', 'Hingoli', 'Jalna', 'Latur', 'Nanded', 'Osmanabad', 'Parbhani']
marathwada_data = icrisat_data[icrisat_data['Dist Name'].isin(marathwada_districts)]
```

---

## 🔍 Key Findings

### Drought Patterns
1. **Marathwada Region**: Significant groundwater depletion observed post-2010
2. **Bundelkhand Region**: Severe multi-year droughts (2002-2004, 2014-2016)
3. **Eastern Tamil Nadu**: Seasonal drought patterns linked to monsoon failures

### Agricultural Impact
- Strong negative correlation between drought intensity and crop yields
- Kharif crops (monsoon season) more vulnerable than Rabi crops
- Sorghum and Pearl Millet showed highest drought sensitivity
- Cotton and Sugarcane severely impacted in Marathwada

### Temporal Trends
- Increasing frequency of drought events post-2000
- Soil moisture declining at rate of ~2-3% per decade
- NDVI values show vegetation stress during drought years

---

## 💻 Technologies Used

### Data Collection & Processing
- **Google Earth Engine** - Satellite data extraction
- **Python 3.8+** - Core programming language
- **Pandas** - Data manipulation
- **NumPy** - Numerical computations

### Analysis & Visualization
- **Statsmodels** - Time series analysis, ARIMA models
- **SciPy** - Statistical tests
- **Matplotlib** - Plotting and visualization
- **Seaborn** - Statistical graphics
- **Plotly** - Interactive visualizations

### Machine Learning (Optional extensions)
- **Scikit-learn** - ML preprocessing
- **TensorFlow/Keras** - LSTM models
- **Prophet** - Time series forecasting

### Geospatial
- **Google Earth Engine Python API** - Geospatial data
- **GeoPandas** - Geographic data handling

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Contribution Ideas
- Extend analysis to more regions
- Implement advanced forecasting models
- Add real-time data integration
- Create interactive dashboards
- Improve visualization techniques

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 📚 Citation

If you use this dataset or code in your research, please cite:

```bibtex
@misc{drought_analysis_india_2024,
  author = {[Your Name/Group Name]},
  title = {Modeling Drought Impacts on Agricultural Productivity: A Multi-Scale Time Series Analysis},
  year = {2024},
  publisher = {GitHub},
  journal = {GitHub Repository},
  howpublished = {\url{https://github.com/YOUR_USERNAME/drought-analysis-india}}
}
```

### Research Paper
**Title**: Modeling Drought Impacts on Agricultural Productivity: A Multi-Scale Time Series Analysis  
**Authors**: Group 2 - Christ University  
**Year**: 2024

---

## 📧 Contact

**Project Maintainer**: [Your Name]  
**Email**: [Your Email]  
**LinkedIn**: [Your LinkedIn Profile]  
**Institution**: Christ University

### Project Links
- **GitHub Repository**: [https://github.com/YOUR_USERNAME/drought-analysis-india](https://github.com/YOUR_USERNAME/drought-analysis-india)
- **Kaggle Dataset**: [Link after upload]
- **Research Paper**: [Available on request]

---

## 🌟 Acknowledgments

- **ICRISAT** for providing district-level agricultural data
- **NASA** for GRACE and GLDAS datasets via Google Earth Engine
- **India Meteorological Department (IMD)** for rainfall and soil moisture data
- **Christ University** for research support and guidance
- **Google Earth Engine** team for the excellent platform

---

## 📈 Project Status

🟢 **Active Development** - Data collection complete, analysis ongoing

### Roadmap
- [x] Data collection from Google Earth Engine
- [x] Exploratory Data Analysis
- [x] Statistical testing and validation
- [ ] Time series modeling (ARIMA, SARIMA)
- [ ] Machine learning models (LSTM, Prophet)
- [ ] Interactive dashboard development
- [ ] Research paper publication

---

## ⚠️ Important Notes

### Data Usage Guidelines
1. **GRACE data** ended in 2017; use GRACE-FO for post-2018 data
2. **GLDAS data** is 3-hourly; aggregate appropriately for analysis
3. **ICRISAT data** may have missing values for some years/districts
4. Always check data quality and completeness before analysis

### Known Issues
- Some districts have incomplete time series
- GRACE has a gap in 2017-2018 (mission transition period)
- NDVI data collection scripts (Cells 1-3) require GEE authentication fixes

### Data Collection Notes
- **Working Code**: Cell 13 in `project_datacollection.ipynb` (Batch Export)
- **Non-working Code**: Cells 1-12 have various authentication and processing errors
- **Recommended Approach**: Use the pre-collected datasets provided in the repository

---

## 🎓 Educational Use

This project is ideal for:
- **Students** learning time series analysis and geospatial data science
- **Researchers** studying drought patterns and agricultural impacts
- **Data Scientists** exploring satellite data integration
- **Policy Makers** understanding drought vulnerability in India

---

## 📊 Dataset Statistics

| Dataset | Records | Time Period | Regions | Variables |
|---------|---------|-------------|---------|-----------|
| GRACE | ~5,000+ | 2003-2017 | 27 districts | LWE thickness |
| GLDAS | ~8,000+ | 2000-2002, 2018-2023 | 27 districts | Soil moisture |
| ICRISAT | ~15,000+ | 1966-2014 | Multiple districts | 75+ crop variables |
| Rainfall | ~115 years | 1901-2015 | India-wide | Seasonal rainfall |

---

**Last Updated**: November 2024  
**Version**: 1.0.0

---

⭐ **Star this repository if you find it useful!** ⭐

🐛 **Found a bug?** [Open an issue](https://github.com/YOUR_USERNAME/drought-analysis-india/issues)

💡 **Have suggestions?** [Start a discussion](https://github.com/YOUR_USERNAME/drought-analysis-india/discussions)

---

*Made with ❤️ for better drought understanding and agricultural resilience in India*
