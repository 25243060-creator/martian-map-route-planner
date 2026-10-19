# MarsPath: Safe Route and Science Planner

Layered Martian map for the 2026 NASA Space Apps Challenge,
"Interplanetary Survival Guide: Martian Map".

**Author:** Nishanthini M

## What it does
- Calculates a slope hazard map of Jezero Crater from a HiRISE DTM
- Builds a hazard cost map (slope > 15 deg = risky, > 25 deg = no-go)
- Finds the safest walking route with A* (scikit-image)
- Routes through real science targets from the Mars Trek Jezero tour
- Shows a 5 km emergency return radius
- Exports an interactive layered map (jezero_map.html)

## Result
- Route: Landing Site (habitat) -> Western Delta Deposit -> Western Inflow Channel
- Total 14.8 km, about 4.9 hours at 3 km/h
- Leg 1: 5.9 km, max slope 14.7 deg
- Leg 2: 8.9 km, max slope 15.0 deg
- Data downsampled to 20 m/pixel

## Data
- Mars Trek (trek.nasa.gov/mars): "MRO HiRISE, Jezero DEM, Controlled"
- Science targets: Mars Trek "Jezero Crater Features and Landforms" tour
- The DEM file is about 1.8 GB and is not included. Download it from Mars Trek.

## How to run
1. Download the DEM from Mars Trek and upload it to Google Drive as `jezero_dem.tif`
2. Open the notebook in Google Colab
3. Run `!pip install rasterio folium`, then run the cells in order

## Tech
Python, NumPy, Rasterio, scikit-image, Matplotlib, Folium

## Limitations
- Slope thresholds (15 and 25 deg) and walking speed (3 km/h) are assumptions
- Planning-level estimate: 20 m/pixel smooths out local steep spots
- Northern Delta and Outflow Channel are outside the DEM study area, so they are excluded
- Map uses image coordinates, not real lat/long

## Future work
Weather (MEDA/REMS), radiation and dust layers, a larger DEM area, 3D view
