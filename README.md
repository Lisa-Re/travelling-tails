# 🐕 Travelling Tails: Dog-Friendly Travel in Germany. A Geographic Accessibility Analysis

> **Project Status:** 🚧 In Development (Work in Progress)

---
## 1. Project Overview

This project explores dog-friendly travel across Germany using OpenStreetMap (OSM) data. It examines accommodation locations and the availability of nearby facilities relevant to travelers with dogs, including veterinary clinics, parks, and pet shops.

The project uses Python and Pandas for data cleaning and preparation, spatial analysis to investigate accessibility, and Tableau to visualize patterns and compare destinations across Germany.


### Data Availability

The raw and processed datasets are stored locally and are not included in this repository. The repository contains an example notebook demonstrating the initial data cleaning and preparation workflow. Running the notebook requires the corresponding source files to be available in the expected local directories.


## 2. Project Goal

Which German cities offer the best accessibility to dog-relevant facilities for travelers?

Traveling with a dog involves more than finding accommodation that allows pets. Access to parks, beaches, veterinary practices, pet shops, and general dog amenities can significantly influence the convenience and quality of a stay.

This project analyzes the geographic accessibility of dog-relevant facilities from accommodation locations across Germany. Using geographic data, it compares cities and districts to identify destinations where travelers can reach essential facilities more easily.

The aim is to develop a data-driven ranking of German destinations based on proximity to relevant services and the availability of nearby alternatives.

### Key Questions
- Which German cities and districts offer the best access to dog-relevant facilities?
- How far must travelers walk or travel from their accommodation to reach a veterinary practice, park, beach, or pet shop?
- Which destinations offer the greatest choice of facilities within a reasonable distance?
- How does accessibility vary between cities and districts?
- Which areas show potential gaps in the availability of nearby facilities?

---

## 3. Data

The project uses geographic data from [OpenStreetMap (OSM)](https://www.openstreetmap.org/), a collaborative, open geographic database. Data is collected using [Overpass Turbo](https://overpass-turbo.eu/) and processed with Python.

### Data Categories

| Category | Description | Key Features & OSM Tags |
| :--- | :--- | :--- |
| **Accommodation** | Hotels, apartments, guest houses, campsites, and lodgings | `tourism=hotel`, `tourism=apartment`, `tourism=guest_house`, `tourism=camp_site` |
| **Veterinary Services** | Veterinary practices and animal hospitals | `amenity=veterinary` |
| **Parks, Beaches & Green Spaces** | Parks, gardens, beaches, and outdoor spaces | `leisure=park`, `natural=beach`, `leisure=garden`, boundary polygons |
| **Pet Shops** | Specialty pet supplies and retailers | `shop=pet` |
| **General Dog Amenities** | Dog infrastructure and convenience facilities | `amenity=waste_disposer` + `waste=dog_waste`, `amenity=dog_toilet`, `leisure=dog_park` |
| **Geographic Reference** | Administrative boundaries for German cities and districts | BKG VG250 / Official German administrative boundaries |

### Data Preparation
Python and Pandas will be used to:
- Clean and standardize the datasets.
- Identify and handle duplicate records.
- Validate geographic coordinates.
- Inspect missing values and relevant dog-related tags.
- Integrate the datasets for spatial analysis.
- Assign facilities and accommodation to cities or districts.

### Data Limitations
OpenStreetMap is community-maintained, so completeness and tagging practices can vary between regions.

The absence of a dog-related tag does not necessarily mean that a facility is unsuitable for dogs. Furthermore, geographic proximity does not guarantee pedestrian accessibility or indicate whether dogs are permitted. The analysis will therefore assess accessibility based on recorded locations rather than claim to measure dog-friendliness in its entirety.

---

## 4. Method

The project combines data preparation, spatial analysis, exploratory data analysis, and interactive visualization.

### Step 1: Data Collection
Collect accommodation and dog-relevant facility data across Germany using OpenStreetMap and Overpass Turbo.

### Step 2: Data Cleaning and Integration
Prepare the datasets with Python and Pandas, validate coordinates, remove duplicate records, and integrate the data with geographic reference information.

### Step 3: Spatial Accessibility Analysis
Calculate the geographic proximity of accommodation to relevant facilities (projected using metric systems like UTM Zone 32N / `EPSG:25832` for accurate meter-level calculations).

The analysis will focus on three dimensions:
- **Proximity:** 
  - Distance from each accommodation to the nearest veterinary practice.
  - Distance to the nearest park, beach, or green space.
  - Distance to the nearest pet shop.
- **Local Availability:** 
  - Number of facilities within selected distance thresholds of each accommodation.
  - Number of nearby alternatives for each facility category.
- **Comparative Accessibility:** 
  - Median distance to relevant facilities across cities and districts.
  - Share of accommodation locations within defined distances of selected facilities.
  - Differences in accessibility between destinations.

Where possible, park and beach boundaries will be used instead of representative center points to improve distance estimates. Distances calculated from coordinates represent straight-line proximity, not actual walking or driving distances.

### Step 4: City and District Ranking
Aggregate accommodation-level accessibility metrics to compare German cities and districts. The ranking will prioritize proximity and the availability of nearby alternatives rather than the total number of facilities alone. The final scoring method, distance thresholds, and weighting of indicators will be documented to ensure transparent comparisons.

### Step 5: Visualization with Tableau
Use Tableau to build an interactive dashboard that communicates the results. Planned visualizations include:
- **Geographic overview:** A map showing the distribution of accommodation and dog-relevant facilities.
- **Accessibility ranking:** A comparison of cities and districts based on selected accessibility indicators.
- **Distance analysis:** Charts showing typical distances from accommodation to different facility categories.
- **Nearby availability:** Comparisons of the number of facilities accessible within selected distance thresholds.
- **Destination comparison:** An interactive view allowing users to compare locations and identify accessibility strengths and weaknesses.

---

## 📁 Repository Structure

```text
travelling-tails/
├── data/
│   ├── raw/                 # Raw OSM data files
│   └── processed/           # Cleaned datasets
├── notebooks/
│   └── 01_data_cleaning.ipynb
├── src/                     # Reusable Python code
├── .gitignore
├── README.md
└── requirements.txt
```

**Note:** Raw and processed datasets are stored locally and excluded from GitHub. The repository includes an example notebook demonstrating the initial data cleaning and preparation workflow. Running the notebook requires the corresponding source files in the expected local directories.

```
------

```
## 🛠️ Tools and Technologies

- **Python:** Data processing and spatial analysis
- **Pandas:** Data cleaning and manipulation
- **GeoPandas & Shapely:** Geospatial data processing & spatial indexing
- **Jupyter Notebook:** Exploratory analysis and documentation
- **OpenStreetMap / Overpass Turbo:** Geographic data collection
- **Tableau:** Interactive dashboards and data visualization
- **SQL:** Data storage and querying (if incorporated into the final workflow)

---

## 📄 Data Attribution & License

- **Project Code:** Licensed under the [MIT License](LICENSE).
- **Data Source:** Map data and facility information are sourced from [OpenStreetMap](https://www.openstreetmap.org/) contributors and extracted via [Overpass Turbo](https://overpass-turbo.eu/).
- **Data License:** OpenStreetMap data is available under the [Open Database License (ODbL)](https://www.openstreetmap.org/copyright). 
- **Map Visuals Attribution:** All maps and Tableau dashboards generated from this data include explicit attribution to `© OpenStreetMap contributors`.

---

## 🚀 Getting Started (Local Setup)

```bash
# Clone the repository
git clone https://github.com/Lisa-Re/travelling_tails.git
cd travelling_tails

# Create a virtual environment
python3 -m venv venv

# Activate the virtual environment (macOS/Linux)
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

**Note:** The raw and processed datasets are not included in this repository. To run the notebook, the required data files must be obtained separately and placed in the expected local directories.
