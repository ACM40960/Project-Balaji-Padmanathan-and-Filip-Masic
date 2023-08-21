[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/foXtNvtG)

# Identification and Ranking of Optimal Locations for New Electric Vehicle (EV) Charging Stations in Dublin

[![Version](https://img.shields.io/badge/version-1.0-orange.svg)]()
[![Python Version](https://img.shields.io/badge/python-v3.9.15+-blue.svg)]()
[![Jupyter Notebook](https://img.shields.io/badge/jupyter-notebook-orange)]()
[![Last Commit](https://img.shields.io/github/last-commit/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic.svg)](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/commits)
[![Documentation](https://img.shields.io/badge/documentation-yes-brightgreen)]()
[![Contributions](https://img.shields.io/badge/contributions-welcome-brightgreen)]()

#### NOTE: 
Due to the comprehensive nature of our Jupyter notebook, the file's size is substantial, making it impractical for direct viewing. To conveniently access its contents without the need for downloading, we kindly suggest utilizing the provided nbviewer link below:

<a href="https://nbviewer.org/github/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/blob/main/01_Consolidated_Code.ipynb" target="_blank">View Notebook on nbviewer</a>

## Table of Contents
- [Project Overview](#project-overview)
- [Dependencies and Installation](#dependencies-and-installation)
- [Getting Started](#getting-started)
- [Data Collection and Exploration](#data-collection-and-exploration)
- [Identification of Optimal Hotspots](#identification-of-optimal-hotspots)
- [Ranking the Optimal Hotspots](#ranking-the-optimal-hotspots)
- [Conclusion](#conclusion)
- [Future Work](#future-work)
- [License](#license)
- [Contact](#contact)

## Project Overview

- The Global Climate Crisis has intensified the urgency to transition to sustainable and eco friendly transportation solutions
- Electric vehicles (EVs) are widely recognized as a promising alternative to traditional fossil fuel powered vehicles, offering reduced greenhouse gas emissions and lower environmental impact
- However, the widespread adoption of EVs requires a robust charging infrastructure that ensures convenient and reliable access to charging stations for EV owners
- Dublin, being a significant urban center with a growing number of EV users, faces the pressing need to increase the network of charging stations to support the transition towards clean and green mobility
-  Our aim is to **Identify and Rank the Optimal Locations** within a 20 Km radius of Dublin where new EV Charging Stations could be placed
- This initiative would contribute to making clean mobility accessible to a larger population and encourage widespread EV adoption
- This would also tie in perfectly with Dublin Region’s plan to deploy 1650 new EV Charging Stations by 2025 - \
    <a href="https://www.dlrcoco.ie/news/general news press releases/dublin region local authorities deploy 1650 ev charge points 2025" target="_blank">Dublin Region local authorities plan to deploy 1650 EV Charge Points by 2025</a>

## Dependencies and Installation

To run this project and utilize its functionalities, you will need to have the following Python libraries installed on your system. You can install them using the provided command:

#### Libraries

- [osmnx](https://osmnx.readthedocs.io/): Python library to work with OpenStreetMap data
- [folium](https://python-visualization.github.io/folium/): Python library for creating interactive maps
- [shapely](https://shapely.readthedocs.io/en/stable/): Python library for manipulation and analysis of geometric objects
- [geopy](https://geopy.readthedocs.io/en/stable/): Python library for geocoding and distance calculations
- [pyproj](https://pyproj4.github.io/pyproj/stable/): Python interface to coordinate transformation operations
- [geopandas](https://geopandas.org/en/stable/): Python library for working with geospatial data
- [pandas](https://pandas.pydata.org/): Python library for data manipulation and analysis
- [numpy](https://numpy.org/): Python library for numerical computations
- [matplotlib](https://matplotlib.org/): Python library for creating static, animated, and interactive visualizations
- [seaborn](https://seaborn.pydata.org/): Python library for statistical data visualization
- [plotly](https://plotly.com/): Python library for interactive visualizations
- [scikit-learn](https://scikit-learn.org/stable/): Python library for machine learning and data mining
- [requests](https://docs.python-requests.org/en/latest/): Python library for making HTTP requests

#### Commands

```bash
pip install osmnx
pip install folium
pip install shapely
pip install geopy
pip install pyproj
pip install geopandas
pip install pandas
pip install numpy
pip install matplotlib
pip install seaborn
pip install plotly
pip install scikit-learn
pip install requests
```
## Getting Started

The below step-by-step guide will help you navigate through the repository and execute the analysis effectively

1) Clone the repository to your local machine
2) Open the Jupyter notebook 01_Consolidated_Code.ipynb
3) Run the provided pip install commands to install the required libraries listed above
4) The Files folder contains all the necessary input files essential for the analysis
5) Note that the notebook includes read_csv commands that load data from specific file paths on the author's machine
6) To adapt the analysis to your machine, update these commands to reference the correct file paths from the Files folder
7) Sequentially execute the notebook cells to perform the analysis steps
8) Review the analysis outcomes and visualizations generated within the notebook

## Data Collection and Exploration

### <i> 01) Hotspot Discovery</i>

- Leveraged OpenStreetMap (OSM) API to get all the hotspots within a 20 Km radius from the centre of Dublin
- OSM data has a feature called ‘amenity’ which accurately tags each coordinate to a particular category
- Based on looking at the list of available ‘amenity’ , we finalized on the following tags as they satisfy our criteria of a hotspot: \
  ['fuel', 'parking', 'events_venue', 'college', 'hospital', 'university', 'food_court', 'exhibition_centre', 'townhall', 'stadium', 'conference_centre']
- There were a total of 6,599 hotspots available in the chosen radius

![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/deaebe9a-41ca-44f9-b3c9-6682655a7b61)

### <i> 02) Feature Gathering</i>

**i) Existing Electric Vehicle Charging Station Locations in Dublin (Coordinate level)**

- Leveraged OpenChargeMap (OCM) API to get all the existing EV stations within a 25 Km radius from the centre of Dublin
- There were a total of 333 EV Charging Points in the chosen radius

![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/bb62bd90-2161-497d-b6ce-19c151ad7eac)

**ii) Public Service Spots in Dublin (Coordinate level)**

- Leveraged OpenStreetMap (OSM) API to get all the public service spots within a 25 Km radius from the centre of Dublin
- Based on looking at the list of available ‘amenity’ , we finalized on the following tags as they satisfy our criteria of a public spot: \
['school', 'pharmacy', 'place_of_worship', 'bank', 'doctors', 'kindergarten', 'social_facility', 'post_office', 'clinic', 'childcare', 'library', 'police', 'veterinary', nursing_home', post_depot', 'fire_station', 'courthouse']
- There were a total of 3,186 public service spots available in the chosen radius 

![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/5befb1b3-360c-424b-b600-a74996c9b978)

**iii) Places of Recreation in Dublin (Coordinate level)**

- Leveraged OpenStreetMap (OSM) API to get all the places of recreation within a 25 Km radius from the centre of Dublin
- Based on looking at the list of available ‘amenity’ , we finalized on the following tags as they satisfy our criteria of a public spot: \
['restaurant', 'cafe', 'pub', 'bar', 'theatre', 'arts_centre', 'cinema', 'nightclub']
- There were a total of 3,128 places of recreation available in the chosen radius

![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/3b28cb59-6713-43dd-aa0c-a0e944b1b7b2)

**iv) Pobal's HP Deprivation Index for Dublin (District level)**

- Pobal's Deprivation Index is a widely used and comprehensive tool in Ireland designed to measure and assess the levels of deprivation within different geographical areas
- It is constructed from a set of key indicators that cover various dimensions of deprivation, such as income, employment, education, health, housing, and access to essential services
- Since there was no API available, the data was taken from this link - \
  <a href="http://trutzhaase.eu/deprivation index/the 2016 pobal hp deprivation index for small areas/" target="_blank">Pobal HP Index</a>

![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/b31d67ca-260c-4f08-8238-63928ce84049)

**v) Total Population of Dublin (District level)**

- The data is from the 2016 census and is available at a district level and it refers to the number of residents living within a particular district
- The population data was taken from the same dataset which contained the Deprivation Index - \
  <a href="http://trutzhaase.eu/deprivation index/the 2016 pobal hp deprivation index for small areas/" target="_blank">Pobal HP Index</a>
    
![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/dbded8a1-9e7b-4070-a462-7bc5ab69a515)

**vi) Household Median Gross Income of Dublin (District level)**

- The household median gross income is also from the 2016 census and represents the midpoint of income distribution within a particular district
- The data was taken from CSO and had to be preprocessed in order for us to directly use for our analysis - \
  <a href="https://data.cso.ie/table/IIA01" target="_blank">Median Gross Income</a>
    
![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/7539de99-5fb0-43df-a7eb-517383a0187f)

## Identification of Optimal Hotspots

### <i> 01) Creation of Hotspot Clusters using DBSCAN</i>

- When we looked at the final list of hotspots, it was clear that there were a lot of hotspots that were very close to each other
- Thus, it would have been pointless for us to consider all of them as separate hotspots when we could easily cluster them into groups thereby reducing redundancy and optimizing the selection process
- Thus, in order to perform this clustering, we decided to use DBSCAN (Density Based Spatial Clustering of Applications with Noise)

![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/fca06f72-900e-4808-a432-6e939f4ee4d1)

- There were a total of 1,658 Clusters formed using our chosen parameters in DBSCAN

![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/e9c9b7cf-a700-41d9-948f-c351ebed9513)

- As you can see in the below gif, after performing DBSCAN, hotspots that are very close become part of the same cluster (Cluster 59)

![DBSCAN](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/9433d476-5d90-435f-8648-03a0b6dbb4b8)

### <i> 02) Designating the Optimal Hotspot per Cluster</i>

- Once the clustering was done, we observed that most clusters predominantly contained only 1 or 2 hotspots, while some clusters had a lot of hotspots within them

![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/0072e1d6-a9c4-49ef-95af-018eb96b6448)

- Thus, in order to remove such redundant hotspots, we decided to keep it simple and adopted a strategy of choosing just one hotspot from each cluster, which became the Optimal Hotspot for that cluster
- Thus we ended up with a total of 1,658 Optimal Hotspots from the 1,658 clusters

![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/3274f3bd-2187-4b5f-95c2-667de8aa9ca5)

- The collection of these 1,658 Optimal Hotspots became our final sample space on which we used our Scoring Function and performed the ranking

![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/86abb2b7-46df-4dd7-b410-3f5927c9d228)

## Ranking the Optimal Hotspots

### <i> 01) Sphere of Influence</i>

- In our analysis, in order to comprehensively rank the importance of Optimal hotspots identified in the previous section, we created a Sphere of Influence around each hotspot
- The Sphere of Influence represents a defined geographical area surrounding the central hotspot, enabling a detailed consideration of its impact and subsequently its ranking
- This approach enabled us to narrow our focus to the immediate vicinity of each hotspot, facilitating an objective ranking based on their contextual surroundings
  ![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/f6c3d7fa-826c-40f8-8d7f-59aa1a0f6b9e)
- Radius of each hotspot's sphere is determined based on the population density, which reflect the hotspot's significance. By incorporating this, hotspots in densely populated areas will have a smaller sphere while loosely populated areas will have a bigger sphere
- We created a mapping function which enabled us to smoothly transform the normalized population density (using min-max normalization) values into meaningful radius values \
  ![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/b1abb785-2505-4e4f-9651-0c51af4e7931)
- The resulting radius for each hotspot in the Sphere of Influence represents its range of impact and helped us perform the next step - Ranking of these Optimal Hotspots \
\
  ![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/769f914b-cf1f-4ca1-a5a6-b82f7340cfc5)

### <i> 02) Final Ranking</i>

- Using the radius of the Sphere of Influence around each hotspot, we created the following metrics to be used for the creation of a Scoring Function
    - Number of existing EV stations lying within the Sphere
    - Number of Public Spots lying within the Sphere
    - Number of Recreational Spots lying within the Sphere
- We then leveraged these features along with the HP Deprivation Index and Median Gross Income to create a Scoring Function that helped us to rank each of the 1,658 Optimal Hotspots
- After getting these 5 features, firstly, we normalized each feature using min-max normalization
- Post that we created a Scoring Function that approximately highlights the importance of each hotspot w.r.t its surroundings

![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/a7c4c9db-6d25-47b8-974d-96eede813026)

- Based on the score generated by this function, we ranked each hotspot, with those obtaining higher scores receiving higher rankings
- The below image shows the top 100 locations for new EV Charging Points based on our analysis -

![image](https://github.com/ACM40960/Project-Balaji-Padmanathan-and-Filip-Masic/assets/133981001/6e3ab9f1-bf55-4a12-8430-ed8bb5c80558)

- The rankings for all 1,658 Optimal Hotspots is available in the jupyter notebook for further exploration

## Conclusion 

- Amidst a growing urgency to address the global climate crisis, Electric Vehicles emerge as a promising and environmentally friendly alternative to traditional fossil fuel powered vehicles
- Optimizing EV Charging Station Placement is pivotal for expediting Electric Vehicle adoption and fostering a sustainable transportation shift
- OpenStreetMaps and OpenChargeMaps give us the opportunity to explore and expand sustainable urban mobility solutions, leveraging the power of open data and collaborative mapping to drive positive change in our cities
- The use of Spatial data along with Clustering algorithms and Optimization showcased the potential of data driven decision making for urban infrastructure planning
- We hope that our findings offer a solid foundation when planning for new EV Charging Stations in Dublin

## Future Work

- More time needs to be spent on coming up with a suitable objective function based on comprehensive field research, domain expertise, and alignment with policy requirements
- Our analysis did not encompass factors such as new EV station setup costs, land acquisition expenses, private/public access. Access to such data would significantly broaden the depth and applicability of our analysis
- Information regarding the existing level of EV usage throughout Dublin was unavailable for our analysis. Integrating this data would greatly enhance our ability to identify optimal new charging station locations
- The establishment of new EV stations would inevitably impact the current power grid, necessitating a cautious integration aligned with the existing load structures. This aspect offers potential for further comprehensive analysis and consideration

## License

This project is licensed under the [MIT License](LICENSE).

## Contact

🤵🏻 **Balaji Padmanathan**
- Student ID: 22202290
- Email - balajirvp6@gmail.com
- LinkedIn: [Balaji Padmanathan](https://www.linkedin.com/in/balaji-p-65845298/)

🤵🏻 **Filip Masic**
- Student ID: 22208050
- Email - filipmasic.ie@gmail.com

Feel free to connect with us! We'd love to hear your thoughts and feedback on this project.

