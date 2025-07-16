# STAC Timelapse Testing

This project demonstrates how to create monthly timelapse composites from Sentinel-2 satellite imagery using the STAC (SpatioTemporal Asset Catalog) ecosystem. The workflow leverages cloud-based geospatial data, parallel processing, and interactive visualization.

## Main Libraries

- **PySTAC & STAC**:  
  STAC (SpatioTemporal Asset Catalog) is a specification for organizing and describing geospatial assets (such as satellite imagery) in a standardized, searchable way. PySTAC and pystac-client are Python libraries for searching, accessing, and working with STAC-compliant catalogs, such as Microsoft's Planetary Computer.

- **stackstac**:  
  A library for efficiently stacking and loading large amounts of geospatial raster data from STAC catalogs into xarray and Dask arrays.

- **Dask**:  
  Dask enables parallel and distributed computation in Python. It is used here to process large satellite datasets efficiently, either locally or on the cloud.

## Workflow Overview

1. **Cluster Setup**:  
   Initializes a Dask cluster for parallel processing.

2. **Area Selection**:  
   Uses ipyleaflet and geopandas to select a region of interest, optionally loading points from a KML file.

3. **Data Search & Loading**:  
   Queries the Planetary Computer STAC API for Sentinel-2 imagery over the selected area and time range, then loads the data with stackstac.

4. **Cloud Masking & Compositing**:  
   Applies cloud masking using the Sentinel-2 Scene Classification Layer (SCL), then creates monthly composites by aggregating clear pixels.

5. **Visualization & Export**:  
   Generates animated GIFs of the monthly composites and optionally exports each monthly composite as a GeoTIFF.

## Requirements

- Python 3.8+
- pystac-client
- planetary-computer
- stackstac
- dask
- xarray
- ipyleaflet
- geopandas
- fiona
- pandas
- matplotlib
- geogif
- rioxarray

Install dependencies with:

```bash
pip install pystac-client planetary-computer stackstac dask[distributed] xarray ipyleaflet geopandas fiona pandas matplotlib geogif rioxarray
```

## Usage

Open `timelapse_notebook.ipynb` in Jupyter and follow the instructions in each cell to select an area, process imagery, and export results.
