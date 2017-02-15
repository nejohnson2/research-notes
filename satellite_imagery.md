# Satellite Data

## The United States Geological Survey (USGS)

Global Land Survey (GLS)

### Programs
- EROS: Earth Resources Observation and Science Center:
- LSR - Land Remote Sensing Program
- 

## Data Sources
The [USGS Data page](https://eros.usgs.gov/satellite-imagery) is the primary source of information regarding Satellite imagery.  This includes numerous declassified satellite datasets and current satellite progrms.  I'm not sure if this is the most extensive list.

- **AVHRR (Advanced Very High Resolution Radiometer):** 1-km multispectral data from the NOAA satellite series.
- **Earth Observing-1 (EO-1) Advanced Land Imager (ALI) and Hyperion:** 10- to 30-meter multispectral and hyperspectral data from the Earth Observing-1 (EO-1) Extended Mission. (2000-2017)
- **[Sentinal 2](https://lta.cr.usgs.gov/sentinel_2)**: The Sentinel-2 MultiSpectral Instrument (MSI) acquires 13 spectral bands ranging from Visible and Near-Infrared (VNIR) to Shortwave Infrared (SWIR) wavelengths along a 290-km orbital swath.

Sensors:
- [**ASTER (Advanced Spaceborne Thermal Emission and Reflection Radiometer)](https://lpdaac.usgs.gov/dataset_discovery/aster):** High-resolution (15- to 90-meter) multispectral data from the Terra satellite (2000 to present).
- **[Landsat ETM+ (Enhanced Thematic Mapper Plus)](https://lta.cr.usgs.gov/LETMP)**: 15- to 30-meter multispectral data from Landsat 7. (1999 to present)
- **[MODIS (Moderate Resolution Imaging Spectroradiometer)](https://lpdaac.usgs.gov/dataset_discovery/modis)**: Moderate-resolution (250- to 1000-meter) multispectral data from the **Terra** Satellite (2000 to present) and **Aqua** Satellite (2002 to present).
- **[Landsat 8 OLI (Operational Land Imager) and TIRS (Thermal Infrared Sensor)](https://lta.cr.usgs.gov/L8):**The Operational Land Imager (OLI) and Thermal Infrared Sensor (TIRS) are instruments onboard the Landsat 8 satellite, which was launched in February of 2013. The satellite collects images of the Earth with a 16-day repeat cycle, referenced to the Worldwide Reference System-2. The satellite’s acquisitions are in an 8-day offset to Landsat 7 (see http://landsat.usgs.gov/acquisition). The approximate scene size is 170 km north-south by 183 km east-west (106 mi by 114 mi).

## Data Portals
- **[EarthExplorer](https://earthexplorer.usgs.gov/)**: A complete search and order / download tool for all of the data in our Archive.
- **[LandsatLook](https://landsatlook.usgs.gov/)**: A tool that allows rapid online viewing and access to the USGS Landsat image archives.
- **[Glovis](http://glovis.usgs.gov/)**: A quick and easy browse-based search and order / download tool of all available satellite and aerial data in our Archive.

## Derrived Datasets
A complete list of datasets derrived from satellite imagery can be found [here](https://eros.usgs.gov/land-cover).

- [AVHRR Normalized Difference Vegetation Index (NDVI) Composites](https://lta.cr.usgs.gov/NDVI)

## Landsat 1 and Landsat 8 
Provide 30 meter resolution (NIR and SWIR), 100 meters (thermal) and 15 meters (panchromatic).  

These [iPython Notebooks from PyDataNYC2014](https://github.com/HyperionAnalytics/PyDataNYC2014) have an excellent explaination of the different bands and how to process them. 

## ASTER TERRA
The **ASTER sensor** is mounted on the **TERRA satellite** and provides high resolution (15m-90m) images in 14 bands including visible to near infrared bands (VNIR bands 1-3), six shortwave infrared bands (SWIR bands 4-9) and five thermal or long wave infrared bands (TIR bands 10-14).  ASTER images map surface temperature, emissivity and reflectance of the earths surface.  L1A is raw data and L1B is radiometrically and geometrically corrected.  Data are available from [http://reverb.echo.nasa.gov/reverb/](http://reverb.echo.nasa.gov/reverb/).

# NASA

Several datasets for CO2 are available from the [NASA Jet Propulsion Lab](https://co2.jpl.nasa.gov/).  The datasets are downloaded in bulk; the 'lite' version is 54GB and the full version is 1TB.  The sites offer python scripts if you customize your download selection.

# MISC
- [Global Land Cover Facility](http://glcf.umd.edu/data/): collection of satellite data.
- [Digital Globe](https://www.digitalglobe.com/): this seems to be a private company who built super high resolution sensors for various satellites.  There was the **Quickbird** satellite ran from the early 2000s to 2010ish.  That program became **Worldview-1**, **Worldview-2** and **Worldview-3**.  The resolution for visible and multispectral imagery are incredible - less than a meter!  **Quickbird** data can be accessed from [http://glcf.umd.edu/data/quickbird/](http://glcf.umd.edu/data/quickbird/)
- [Earth Observation Data](https://earthdata.nasa.gov/earth-observation-data): I havent spent much time looking over this page but it seems there is a lot of data available.
- [NASA Earth Science Data](http://eospso.gsfc.nasa.gov/content/nasa-earth-science-data): lots of links.  havent explored
[The National Map](https://viewer.nationalmap.gov/viewer/) seems to be a country-wide geospatial dataset that includes 1 foot resolution imagery, topographic contours, borders and much more.
