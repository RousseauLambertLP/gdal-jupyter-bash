[En français](readme_cansips-datamart_fr.md)

![ECCC logo](../../img_eccc-logo.png)

[TOC](../../readme_en.md) > [MSC data](../readme_en.md) > [CanSIPS](readme_cansips_en.md) > CanSIPS data in GRIB2 on MSC Datamart

# Canadian Seasonal to Inter-annual Prediction System (CanSIPS) Data in GRIB2 Format

The Canadian Seasonal to Inter-annual Prediction System (CanSIPS) is a long-term prediction system whose objective is to forecast the evolution of global climate conditions. CanSIPS is a multi-model ensemble (MME) system using two atmosphere-ocean-land coupled models developed by the Canadian Centre for Climate Modelling and Analysis (CCCma) and the Canadian Meteorological Centre (CMC). It is a fully coupled atmosphere-ocean-ice-land prediction system relying on the operational data assimilation infrastructure for the initial state of the atmosphere, sea surface temperature and sea ice. For further technical information about CanSIPS please refer to the technical note.

## Principal components of CanSIPS
    
* __Assimilation mode__: CanCM4 uses a continuous assimilation cycle for the following 3D atmospheric variables: temperature, wind and humidity. The oceanic variables: sea surface temperature and the sea ice are also assimilated by the system. The assimilated data are provided by the global atmospheric analysis available every 6 hours and the daily sea surface temperature and sea ice analysis. Also a 3D ocean temperature analysis is integrated to CanCM4 trial field before launching the integration. GEM-NEMO uses atmospheric initial condition of the Global Ensemble Prediction System (GEPS) which are generated from the Ensemble Kalman Filter (EnKF) with observations that are background-checked and bias-corrected by the Global Deterministic Prediction System (GDPS). The ocean and sea ice initial conditions come from the CMC GIOPS analysis. To initialize the land surface fields, the CMC Surface Prediction System (SPS) is run offline forced by the near-surface atmospheric and precipitation fields of the CMC analysis.
* __Forecast mode__: The CanSIPS forecasts are based on a 10-member ensemble of forecasts produced with each of the two models for a total ensemble size of 20. Monthly to multi-seasonal forecasts extending to 12 months are issued on the first day of each month.
* __Hindcast mode__: CanSIPS climatology is based on a series of retrograde forecasts (e. g. historical forecasts) covering the period 1981 to 2010. This climatology is very useful for interpreting realistic forecasts because real-time forecast anomalies are generated instead of raw forecasts.

## How is the CanSIPS forecast configured ?

Ensemble size for the forecast is 20 members (10 GEM-NEMO members + 10 CanCM4 members). At the last day of the each month, a 12-month forecast is produced. There are no lagged initial conditions, all the 20 members start on the first of the month and are initialised with different initial conditions originating from separate assimilating coupled model runs. When the ensemble forecasts are finished we construct seasonal mean anomalies with respect to the 30-year hindcasts for each ensemble member. Subsequently we implement deterministic (ensemble mean) and probabilistic (different categories with respect to the ensemble size) approaches to forecast the upcoming seasons. 

## Data location 

MSC Datamart data can be [automatically retrieved with the Advanced Message Queuing Protocol (AMQP)](../../msc-datamart/amqp_en.md) as soon as they become available. An [overview and examples to access and use the Meteorological Service of Canada's open data](../../usage/readme_en.md) is also available.

The data is available using the HTTP protocol and resides in a directory that is plainly accessible to a web browser. Visiting that directory with an interactive browser will yield a raw listing of links, each link being a downloadable GRIB2 file.

The data can be accessed at the following URLs :

* [https://dd.weather.gc.ca/ensemble/cansips/grib2/forecast/raw/{YYYY}/{MM}/](https://dd.weather.gc.ca/ensemble/cansips/grib2/forecast/raw)
* [https://dd.weather.gc.ca/ensemble/cansips/grib2/hindcast/raw/{YYYY}/{MM}/](https://dd.weather.gc.ca/ensemble/cansips/grib2/hindcast/raw)

where :

* __forecast__ : Constant string indicating that the file contains the data from the forecast part of CanSIPS, in opposition to the hindcats part.
* __hindcast__ : Constant string indicating that the file contains the data from the hindcast part of CanSIPS, in opposition to the forecast part.
* __MM__ : Month of the forecast start [01, 02, 03, ..., 12]
* __YYYY__ : Year of the forecast start [2012, 2013, ...]

A 2-month history is kept in this directory.

## Technical specification of the grid

Tables list the values of various parameters of the CanSIPS lat-lon grid, according to the resolution.

### Data at 2.5x2.5 degrees resolution

| Parameter | Value |
| ------ | ------ |
| ni | 145 |
| nj | 73 | 
| resolution | 2.5° |
| coordinates of the first grid point | 90° S  0° E | 

### Data at 1.0x1.0 degree resolution

| Parameter | Value |
| ------ | ------ |
| ni | 360 |
| nj | 180 | 
| resolution | 1.0° |
| coordinates of the first grid point | 89.5° S  0.5° E | 

## File name nomenclature 

NOTE : ALL HOURS ARE IN UTC.

The files have the following nomenclature:

* Filename for the forecast : cansips_forecast_raw_projection_VAR_YYYY-MM_allmembers.grib2
* Filename for the hindcast : cansips_hindcast_raw_projection_VAR_YYYY-MM_allmembers.grib2
* Filename for probabilities: cansips_forecast_prob-product_projection_VAR_PPP_YYYY-MM.grib2

where :

* __cansips__ : Constant string indicating that the data is from the CanSIPS system.
* __forecast__ : Constant string indicating that the file contains the data from the forecast part of CanSIPS, in opposition to the hindcats part.
* __hindcast__ : Constant string indicating that the file contains the data from the hindcast part of CanSIPS, in opposition to the forecast part.
* __raw__ : Constant string indicating that the file contains raw data without bias correction
* __projection__ : Constant string indicating the projection [latlon] and resolution [2.5x2.5, 1.0x1.0]
* __VAR__ : Variable type included in this file. To consult a complete list, refer to the variables section
* __MM__ : Month of the forecast start [01, 02, 03, ..., 12]
* __YYYY__ : Year of the forecast start [2012, 2013, ...]
* __allmembers__ : Constant string indicating that all members [01, 02, 03, ..., 20] are grouped into the file.
* __grib2__ : Constant string indicating the GRIB2 format is used.
* __product__: product description (ex: near-normal, above-normal, below-normal)
* __PPP__: forecast product time length ex: P3M is for a product with forecast a period of 3 months. 

Examples : 

* cansips_forecast_raw_latlon2.5x2.5_HGT_ISBL_0500_2012-10_allmembers.grib2
* cansips_forecast_raw_latlon1.0x1.0_PRATE_SFC_0_2019-08_allmembers.grib2
* cansips_forecast_prob-below-normal_latlon2.5x2.5_TMP_TGL_2m_P3M_2018-12.grib2

## Internal Structure of the Files

The internal structure of the forecast and hindcast files is the following : 

Each file contains 240 temporal records (12 months times 20 ensemble members) and starts with the first ensemble member. Ensemble members are placed in an incremental order within the CanSIPS files.

Each forecast or the hindcast file starts with a lead time of zero months. This means that if for example a CanSIPS file has a 2016-02 date-tag (e.g. cansips_forecast_raw_latlon-1x1_PRATE_SFC_0_2016-02_allmembers.grib2),data will start from the month 02 of the year of 2016 and will be finished (for the first member) in the month 01 of the year of 2017. This means that the forecast was initialised on the last day of the January 2016 and that the results are starting to appear in the month of February 2016 (zero lead time).

Following the temporal record of the month 01 of the year 2017, a second CanSIPS ensemble member appears from the month 02 of the year 2016 following the same logic as described earlier.

## Levels

The data are available at surface and for certain isobaric levels.

## List of variables

The list of the CanSIPS available variables is the following:

* Water temperature (WTMP_SFC_0)
* Precipitation rate (PRATE_SFC_0)
* Temperature at 2m (TMP_TGL_2m)
* Temperature at 850 hPa (TMP_ISBL_850)
* Mean Sea Level Pressure (PRMSL_MSL_0)	
* Geopotential Height at 500 hPa (HGT_ISBL_500)
* U Wind Component at 200 hPa (UGRD_ISBL_200)
* U Wind Component at 850 hPa (UGRD_ISBL_850)
* V Wind Component at 200 hPa (VGRD_ISBL_200)
* V Wind Component at 850 hPa (VGRD_ISBL_200)

The list of the CanSIPS variables for probability above,near or below normals products is the following:

* Temperature at 2m (TMP_TGL_2m)
* Precipitation rate (PRATE_SFC_0)

## Tips for Computing Anomaly Forecasts

It is recommended to use anomaly forecasts instead of the raw forecasts. Anomaly forecasts can be obtained by subtracting from the forecast a climatology based on the hindcasts. The recipe is as follows for a given variable:

For a specific forecast month (e.g. 2016-02) an ensemble mean file needs to be created and we can call it ensm_for_02_2016 for the purpose of this example. This file now contains only 12 temporal records since the mean of 20 ensemble members is performed. The temporal record of this file starts in the month 02 of the year 2016 and stretches until the month 01 of the year 2017.

Subsequently, the same procedure is repeted for the hindcast files but separately for each of the hindcasts that start in 1981 and stretch until the year of 2010. Each year will have an ensemble mean file for the month 02, ensm_hin_02_YYYY, but for the particular hindcast year (YYYY stands for a particular hindcast year). By making the mean of all of the 30 ensm_hin_02_YYYY files, the climatology of the ensemble mean hindcast for the month of February is obtained, which can be called ensm_hinclim_02 in this example.

The subtraction of ensm_hinclim_02 and ensm_for_02_2016 allows for anomaly forecast production for the month 02 of the year 2016. Since this anomaly forecast now contains 12 temporal records, starting from the month of February 2016, we can say that the anomaly forecast for the month of February has zero lead time, for the month of March 2016 a one month lead time and finally for the month of January 2017 (last of the 12 record) an eleven month lead time.

Similar approach applies for the seasonal forecasts only with the seasonal means (e.g. DJF, JFM, FMA, or any other running season) being calculated before the anomaly forecast is computed.

## Support

If you have any questions about these data, please contact us at: [ec.dps-client.ec@canada.ca](mailto:ec.dps-client.ec@canada.ca)

## Announcements from the dd_info mailing list 

Announcements related to this dataset are available in the [dd_info list](https://lists.ec.gc.ca/cgi-bin/mailman/listinfo/dd_info).
