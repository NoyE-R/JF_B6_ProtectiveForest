# JF_B6_ProtectiveForest

## Project

Team project attempting to model the evolution of the protective forests health in Switzerland.
Presentation of the project available on [Jedha Bootcamp](https://www.youtube.com/watch?v=Hbn9JkuRaWk&t=5136s&ab_channel=JedhaBootcamp) youtube channel.

**Team**
Main contribution:
- Dashboarding:[@MarjoryLamothe](https://github.com/MarjoryLamothe);
- Satellite data gathering and aggregation: [@Jesshuan](https://github.com/Jesshuan/Jedha-certification/tree/master/Blocn%C2%B06%20-%20Evolution%20and%20predictions%20for%20Swiss%20protection%20forests);
- Climatic data analysis: [@Ukratic](https://github.com/Ukratic/Protection-Forests);
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

![map](https://github.com/NoyE-R/JF_B6_ProtectiveForest/blob/main/items/map_BA_diff.png)

- For more details:
<img src="https://github.com/NoyE-R/JF_B6_ProtectiveForest/blob/main/items/qrcode.png" width="50%" height="50%">

**Approach**  
- We selected three targets to describe and predict in order to get different point of view defining the health of forests:
    - Basal Area: biomass production at time t;
    - Wood volume increment: growth of the forest plot between two forest surveys;
    - Regeneration cover rate: development ability of the forest in the future, *i.e.* stability of the forest.

- The main aim of the projet was to attempt to predict the three targets to identify forest plots with low health state. Three original sub-objectives were then developed:
    - Descriptive analysis of the targets to identify the relevant features (mainly field and climatic data);
    - Correlative analysis to get the match between satellite data and the relavant features in order to access at annual scale of those feature via satellite request; 
    - Predictive analysis of the targets with relevant features, climatic and satellite data.

Example of results of descriptive modeling which was quite conclusive for 2 of the 3 targets:
![Descriptive models](https://github.com/NoyE-R/JF_B6_ProtectiveForest/blob/main/items/desc_target.png)

## Repository architecture

### Folders:
*dataset*
- raw datasets from NFI with translated headers in French
- data_merge_meteo_SAT.xlsx: final working dataframe

*docs*
- additional resources for data understanding and analysis

*ML_descriptive*
- codes for descriptive modeling of Basal Area and Wood volume increment targets

*results*
- score_total.xlxs: scores from descriptive and predictive models
- Plot_ML_scores.ipynb: formating model results for dashboard in French

*satellite*
- codes for gathering and aggregating satellite data

### Files
- NFI_data_preparation.ipynb: preparation and merging the raw NFI datasets
- EDA_IFN_forestplot_map.ipynb: EDA of forest plot dataset and production of first visualizations

### Library
*data manipulation*:
- pandas, openpyxl, numpy, json, datetime

*graphics*:
- seaborn, plotly, matplotlib

*data analysis*:
- scikit-learn

*request*:
- earth engine

### Main Conclusions
- An increase of 3°C coupled with a general decrease of precipitaiton regime were observed for the studied forest since 40 years leading to a highest probability of drought events.
Meanwhile, a high amount of protective forests displays problematic decrease of the wood production and regeneration cover rate which increase our concerns about their ability to fulfill their protective role in the future.

- Analysis:
    - Descriptive analysis shows that Basal Area (BA) and Regeneration cover rate are mainly explained by field data whereas wood volume increment (WVI) is more difficult to describe.
    WVI is calculated from the volume difference between two surveys (*cca* 10 years-gap) and then annualy average. However, annual tree growth depends on climatic data, and more specially by the extreme climatic events, and initial plot and tree properties.
    In this case, averaging this kind of data induces biais in the analysis because of the assumption that tree and, then forest, grew up constantly between years within the studied period.
    A better incorporation of climatic data by extracting extreme climatic values could improve our analysis. Moreover, tree and forest growth modeling are the hot topic in academic research since decades, meaning the difficulty to analyse this target.
    - In addition, satellite data are not the main features contributing to all tested models. Here, we computed only five functions and an average value from a 25-m-raster which could not be sufficient to describe proprely the field features we need. However, some field and climatic features showed good correlations with satellite data.
    - Predictive analysis on BA display the best scores among the different tested targets. The contribution of field data is predominant where compared to climatic and satellite data.
    - To sum up, simple functions from satellite data and data extraction of climatic data are not enough to describe and built retrospectively the time series of the forest health which limit our predictions.
    In addition to a deeper analysis of satellite and climatic data, features derived from another remote-sensing technologies like LIDAR could improved our models.