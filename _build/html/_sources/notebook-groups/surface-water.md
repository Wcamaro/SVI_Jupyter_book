# Surface Water

Surface water plays a vital role in the Earth's hydrological cycle, encompassing various components such as soil moisture, lakes, and rivers. This subsection focuses on the analysis of different aspects of surface water dynamics, including soil moisture anomalies and the characteristics of lake water bodies.

## [Soil Moisture Anomaly Analysis](../notebooks/soil-moisture-anomalies/soil-moisture-anomalies.ipynb)

In this tutorial we will download C3S Satellite Soil Moisture data from the [Copernicus Climate Data Store (CDS)](https://doi.org/10.24381/cds.d7782f18), read data stacks in python using [xarray](https://xarray.pydata.org/) and perform simple analyses of soil moisture anomalies over selected study areas.

The tutorial consists of the following main steps:

1. A short description of the data sets
2. Download satellite soil moisture images from CDS using the CDS API
3. Application 1: Open downloaded data and visualize the soil moisture variable
4. Application 2: Extract a time series for a single location and compute the soil moisture anomaly
5. Application 3: Vectorized anomaly computation and data extraction for a study area

## [Tutorial: Visualising Lake Water Level (LWL) Timeseries](../notebooks/lake-water-level/lake-water-level.ipynb)

In this tutorial we will access lake products from the Climate Data Store (CDS) and analyse the timeseries of the lake water level on a selected lake. The tutorial comprises two main steps:

1. Dowload and decompress data
2. Visualise the location of the lake in a map
3. Visualise and save water level timeseries
4. Visualise and save the yearly water level anomalies

## [Lake Surface Water Temperature Analysis](../notebooks/lake-surface-water-temperature/lake-surface-water-temperature.ipynb)

In this tutorial we will access lake surface water temperature data from the Climate Data Store (CDS) and plot

- the timeseries at the lake centre for a given day of the year and
- the LSWT, uncertainty and quality level for all the pixels on the given lake on a selected day.

The tutorial comprises two main steps:

1. Dowload and decompress data for every year on record on the selected day of the year
2. Visualise and save the lake surface water temperature **timeseries** (displaying quality levels and uncertainty) **at the lake centre**, but other locations can be given through their lat/lon coordinates
3. Visualise the location of the lake centre (or of the preferred location) on the lake mask
4. Plot the **LSWT, uncertainty and quality level for all the available pixels** on the selected lake **on a given date**
