# JF_B6_ProtectiveForest

## Project

Team project attempting to model the evolution of the protective forests health in Switzerland.
Presentation of the project available onon [Jedha Bootcamp](https://www.youtube.com/channel/UC_eP8EL0XZYwmTf1_m1U6-Q) youtube channel.

**Team**
Main contribution:
- Dashboarding: @MarjoryLamothe;
- Satellite data gathering and aggregation: @Jesshuan;
- Climatic data analysis: @Ukratic;
- Scientific expertise: myself;
- Modeling: all members.

**Dataset**
The used dataset includes three kind of data:
- National Forest Inventory ([NFI](https://lfi.ch/index-fr.php)) data : field measurements of the typographical and structural variables from 1983 to 2017;
- Historical climatic data ([WSL](https://www.wsl.ch/fr/index.html)): monthly temperature and precipitation records;
- Satellite data ([GEE](https://earthengine.google.com/) and [Indices](https://eo4geocourses.github.io/IGIK_Sentinel2-Data-and-Vegetation-Indices/#/)): satellite images of each forest plots from LANDSAT 5 and 7.

NB: requests to satellites were done by all members of the team using Docker image.

**Outputs**
Results take form through:
- Dashboard summing up workflow, EDA and modeling analysis, available to this [link](https://ukratic-protection-forests-dashboard-home-fsgk56.streamlit.app/);
- Interactive maps forest health.

map

**Analytical approach**
Three targets were selected in order to get different point of view defining the health of forests:
 - Basal Area: biomass production at time t;
 - Wood volume increment: growth of the forest plot between two forest surveys;
 - Regeneration cover rate: development ability of the forest in the future, *i.e.* stability of the forest.

Analysis were split in three main parts

## Repository architecture

### Folders:
*dataset*:
- raw datasets from NFI with translated headers in french
- data_merge_meteo_SAT.xlsx: final working dataframe

*docs*: additional resources for data understanding and analysis

*ML_descriptive*: codes for descriptive modeling of Basal Area and Wood volume increment targets

*results*:
- score_total.xlxs: scores from descriptive and predictive models
- Plot_ML_scores.ipynb: formating model results for dashboard in French

*satellite*: codes for gathering and aggregating satellite data

### Files
- NFI_data_preparation.ipynb: preparation and merging the raw NFI datasets
- EDA_IFN_forestplot_map.ipynb: EDA of forest plot dataset and production of first visualizations

### Library
*data manipulation*
pandas, openpyxl, numpy, json, datetime

*graphics*
seaborn, plotly, matplotlib

*data analysis*
scikit-learn

*request*
earth engine