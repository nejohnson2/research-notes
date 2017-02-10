# Satellite Imagery and Python

# Overview

## The United States Geological Survey (USGS)

### Programs
- EROS: Earth Resources Observation and Science Center:
- LSR - Land Remote Sensing Program
- 

## Data
The [USGS Data page](https://eros.usgs.gov/satellite-imagery) is the primary source of information regarding Satellite imagery.  This includes numerous declassified satellite datasets and current satellite progrms.  I'm not sure if this is the most extensive list.

- *ASTER (Advanced Spaceborne Thermal Emission and Reflection Radiometer):**
- **AVHRR (Advanced Very High Resolution Radiometer):**
- **CDP (Comercial Data Purchase Imagery):**
- **Earth Observing-1 (EO-1) Advanced Land Imager (ALI) and Hyperion:** 10- to 30-meter multispectral and hyperspectral data from the Earth Observing-1 (EO-1) Extended Mission. (2000-2017)
- **[Sentinal 2](https://lta.cr.usgs.gov/sentinel_2)**:

## Data Portals
- EarthExplorer:
- LandsatLook
- **TerraLook**: The TerraLook collection consists of georegistered Advanced Spaceborne Thermal Emission and Reflection Radiometer (ASTER) images and Landsat Global Land Survey orthorectified images from five epochs (circa 1975, 1990, 2000, 2005, and 2010), selected from satellite images archived at EROS. TerraLook is intended to broaden the satellite data user community by providing both ASTER and Landsat Global Land Survey data as simulated natural color JPEG images.

# Landsat 1 and Landsat 8 
Provide 30 meter resolution (NIR and SWIR), 100 meters (thermal) and 15 meters (panchromatic).  The data can be downloaded from [https://earthexplorer.usgs.gov/](https://earthexplorer.usgs.gov/)

These [iPython Notebooks from PyDataNYC2014](https://github.com/HyperionAnalytics/PyDataNYC2014) have an excellent explaination of the different bands and how to process them. 

## Landsat Viewer
The [Landsat Viewer](https://landsatlook.usgs.gov/) page is a great place to preview Landsat imagery.  I havent played with this much but will report more once I have. 

# ASTER TERRA
The ASTER sensor is mounted on the TERRA satellite and provides high resolution (15m-90m) images in 14 bands including visible to near infrared bands (VNIR bands 1-3), six shortwave infrared bands (SWIR bands 4-9) and five thermal or long wave infrared bands (TIR bands 10-14).  ASTER images map surface temperature, emissivity and reflectance of the earths surface.  L1A is raw data and L1B is radiometrically and geometrically corrected.  Data are available from [http://reverb.echo.nasa.gov/reverb/](http://reverb.echo.nasa.gov/reverb/).
