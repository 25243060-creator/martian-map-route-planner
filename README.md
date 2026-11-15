# MarsPath: A Layered Safe-Route Map for a Jezero Crater Marswalk

NASA Space Apps Challenge 2026, **Interplanetary Survival Guide: Martian Map**
Team **NOVANEC**: Nishanthini M (Team Leader), Sailaja M, Suji R, Tanisha Rayyan S

## What it is
MarsPath is an interactive, layered map of Jezero Crater that helps plan a safe human surface excursion. It combines three kinds of NASA and USGS data and plans a route from the habitat (Perseverance landing site) to science stops within an emergency return radius.

**Live map:** https://25243060-creator.github.io/martian-map-route-planner/jezero_map_final.html
**Map file:** `jezero_map_final.html` (open in a browser)

## Layers
- Optical image (CTX orthoimage)
- Geologic units (USGS)
- Slope, elevation and hillshade (derived from the HiRISE DTM)
- Caution zone (slope 15 to 25 degrees) and no-go zone (above 25 degrees)
- On-foot route, rover-supported route, 8 km return radius, science stops
- Crew safety panel

## Results
- Habitat to Western Delta (on foot): 7.4 km, about 2.5 hours at 3 km/h, maximum slope 15 degrees
- Western Delta to Western Inflow Channel (rover-supported): 10.2 km
- 6.7% of the mapped area is caution terrain and 0.6% is no-go terrain

## Data used
- Mars 2020 Terrain Relative Navigation HiRISE DTM Mosaic (USGS)
- Mars 2020 Terrain Relative Navigation CTX Orthorectified Image Mosaic (USGS)
- Geologic Map of Jezero Crater and the Nili Planum Region, USGS SIM 3464 (Sun and Stack, 2020)
- Curiosity RAD measurements at Gale Crater (reference value for radiation)

## How it works
1. Load the DTM and downsample it to a 20 m grid
2. Compute slope and build a cost map (slope above 15 degrees costs more, above 25 degrees is blocked)
3. Plan routes with the A* algorithm
4. Align the optical image and the geologic polygons to the DTM grid
5. Build the interactive Folium map with layer toggles and a safety panel

## Assumptions and limitations
- The slope limits (15 and 25 degrees), walking speed (3 km/h) and 8 km return radius are our assumptions
- The geologic map was made on a different CTX base, so alignment with the optical layer is approximate
- The Western Inflow Channel position is approximate
- The radiation value is a reference from Curiosity, not measured at Jezero
- No thermal or spectral layer yet

## Files
- `jezero_map_final.html`: final interactive map
- `marspath_notebook.ipynb`: Google Colab notebook
- `jezero_route_real.png`: route preview on the slope map
- `jezero_map.html`: earlier version of the map

## Tools
Python, Google Colab, rasterio, GeoPandas, scikit-image, Folium
