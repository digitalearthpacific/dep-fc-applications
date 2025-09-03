# Fractional Cover Analysis and Applications

This repository explores the use of **fractional cover (FC)** products for land cover classification across Pacific Islands.  
The work combines exploratory analysis and a **Random Forest classifier** trained on multi-sensor satellite data.

---

##  Fractional Cover Analysis  

Notebook: **`fc_analysis.ipynb`**

- Analysis/ Visualisation of FC over Urban Area (Noumea, New-Caledonia). Uses K-means clustering to test if FC can help classify multiple classes areas.  
- Tests whether FC can distinguish Dry Forest (Forêt Sèche) in New Caledonia, save FC statistics for Dry Forest in Bourail and used these statistics to higlight dry forest in another area.  
- Explores the ability of FC to detect crops in Vanuatu.  

**Findings:**  
- Promising for **land cover classification** and **dry forest detection**.  
- Limited success in separating **cropland vs. grassland** in Vanuatu.

---

##  Fractional Cover Applications  

We extend the analysis by training a Random Forest classifier for land-cover classification with 7 classes:  

- Forest  
- Cropland  
- Grassland  
- Built-up  
- Bare soil  
- Water  
- Mangroves  

Notebooks:  
- **`data_preparation.ipynb`** : prepares training data  
- **`FC_RF_Classifier.ipynb`** : trains and tests the classifier

<img width="1930" height="1083" alt="image" src="https://github.com/user-attachments/assets/8d881632-ef01-49f3-872b-b58a532099e9" />

---

### Data Preparation  

Run **`data_preparation.ipynb`** for each labeled region (Cook Islands, Marshall Islands, Fiji, Palau).  
The output is a CSV file containing:  

- **Fractional cover (bs, pv, npv)** from Landsat-8  
- **Spectral bands (RGB, NIR, SWIR, emad, smad, bcmad)** from Sentinel-2 Geomedian  
- **Spectral indices**: NDVI, MNDWI, NDBI, EVI  
- **Seasonal fractional cover** (Jan–Apr, May–Aug, Sep–Dec)  
- **Elevation Model**  

Data are interpolated on labeled geopackage points, so each row = data + label.

---

### Random Forest Classifier  

Notebook: **`FC_RF_Classifier.ipynb`**  

- Loads training data from prepared CSVs.  
- Creates a **balanced dataset** by random sampling across regions.  
- Trains and tests a **Random Forest classifier** on the 7 land-cover classes.  

