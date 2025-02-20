# Optimizing-EV-Charging-Infrastructure
1. Project Motivation -
Inadequate infrastructure for charging electric vehicles (EVs) still remains
a significant obstacle to their broad use as their acceptance rises. Range anxiety and the scarcity
of charging outlets make many prospective EV purchasers hesitant. Lack of charging availability
was listed as the top problem by 44% of respondents who were not interested in buying an EV in
a 2022 survey (WSJ). By employing unsupervised machine learning approaches, this initiative
seeks to strategically determine the best places for additional EV charging stations. To increase
accessibility, convenience, and promote future EV use, we analyse vehicle range, EV ownership
distribution, and the current charging network.

Business Relevance - Expanding charging infrastructure has significant economic and
environmental benefits. Businesses can attract more customers by hosting charging stations,
while utility companies can optimize electricity distribution and grid stability. Government and
city planners can use data-driven insights to allocate resources efficiently, ensuring equitable
access to charging points. According to the International Energy Agency (IEA), a strong network
of charging stations is extremely important to supply future EV demand and cutting carbon
emissions.This project promotes sustainability initiatives and speeds up the shift to cleaner
transportation by increasing the availability of EV charging stations.

Related Work - Previous studies have explored data-driven approaches for optimizing charging
infrastructure. Wang et al. (2024) integrated transportation and charging network data to
minimize travel time and improve efficiency (arXiv). Similarly, Tiu et al. (2023) developed
demand estimation models for optimal station placement (arXiv). This project builds upon these
works by applying clustering techniques (DBSCAN, K-Means) and geospatial analysis to
identify high-demand areas lacking sufficient charging facilities. Additionally, anomaly detection
methods will be used to highlight underserved regions, ensuring a more comprehensive approach
to infrastructure expansion.

3. Problem Statement
With the continuous onboarding of electric vehicles, demand for charging infrastructure surfaces
aggressively. However, in many places, the growth in the number of charging stations is not up
to the increment of EV ownership, hence giving rise to huge areas commonly known as charging
deserts, where access to public chargers by drivers is limited or not available. This has been a
great hurdle to the adoption of EVs, especially in areas where home charging is not feasible.
This is done by finding the optimal charging station locations with the help of spatial distribution
based on electric vehicle owners, vehicle type, electric range, and current charging station
placements. Clustering EV population data and then overlaying that with the existing charging
station locations can help detect areas where EV density is high and charging options are
minimal. Moreover, anomaly detection techniques can also provide hotspots of unexpected EV
adoption without infrastructure that will drive data-driven investment decisions by city planners
and private charging networks.

Beyond location analysis, the project will study the usage patterns of EV by association rule
mining, finding behaviors such as the relationship between short-range EVs and urban charging
needs, or how certain vehicle brands rely on the fast-charging network. These will serve to assist
not only in infrastructural expansions but also inform policies, such as incentives for public or
workplace charging installations.
This project will provide an integrated data-driven solution to support sustainable EV growth,
ensuring better accessibility for drivers of different geographic and socio-economic regions, by
leveraging unsupervised learning techniques such as clustering, anomaly detection, and
association rule mining.

5. Dataset
1. Alternative Fuel Stations Locator Dataset

Size & Features: 93,056 entries with 75 features, comprising 61 categorical, 13 numeric,
and 1 integer feature.
Source: Data was obtained from the US Department of Energy website (Link -
https://afdc.energy.gov/stations#/analyze)
Key Features:
a. Fuel Type Code – Specifies if the station offers electric, hydrogen, or other
alternative fuels.
b. Station Name & Location (City, State, ZIP, Latitude/Longitude) – Allows spatial
mapping of current infrastructure.
c. Status Code – Specifies if the station is presently active or inactive.

Data Handling Strategy:
a. Fields like "Updated At" and "Date Last Confirmed" are unnecessary for
infrastructure planning and will be removed.
b. No exact duplicates were found, we will standardize categorical values (e.g., Fuel
Type Code) for consistency.
c. Filter by state/region to focus on high-demand areas and reduce processing load.
2. Electric Vehicle Population Dataset

Size & Features: 223,995 records with 17 features, comprising 10 categorical, 5
numerical, and 2 integer features.

Source: Data was obtained from the US Government’s Open Data (Link -
https://catalog.data.gov/dataset/electric-vehicle-population-data)

Key Features:
a. Vehicle Make & Model – Determines the most prevalent EV brands (Tesla,
Nissan, Chevrolet, etc.).
b. Electric Vehicle Type – Splits between Battery Electric Vehicles (BEVs) and
Plug-in Hybrid Electric Vehicles (PHEVs) to evaluate different charging
requirements.
c. Model Year – Facilitates monitoring EV adoption patterns over time.
d. Geographic Distribution (City, State, ZIP) – Identifies high-density locations of
EV ownership.
e. Electric Range – Specifies the distance a vehicle can travel on a single charge,
which affects charging station location.
Data Handling Strategy:
a. Columns such as "VIN (1-10)" and "Vehicle Location", which serve as unique
identifiers rather than contributing to location-based infrastructure planning, will
be removed.
b. Standardize EV Make & Model for accurate grouping.
c. Apply clustering (DBSCAN, K-Means) to identify optimal charging station
locations based on EV density.

4. Proposed Methodologies
This project aims to identify optimal locations for new EV charging stations by analyzing
electric vehicle (EV) adoption patterns and existing charging infrastructure. We will employ
unsupervised learning techniques such as clustering, anomaly detection, and association
rule mining, along with geospatial analysis to generate actionable insights.

Preprocessing and Feature reduction: We will use PCA to reduce dimensions and also
apply other preprocessing techniques like scaling etc.

Clustering - We will apply clustering to identify different customer segments and also
identify geographic regions with high EV adoption density .We will explore using either
K- Means clustering or DBSCAN clustering. We are inclined towards DBSCAN as it can
detect natural clusters without assigning a fixed number of groups and also the clusters
will depend heavily on the density of EV registrations in each cluster.

Geospatial Analysis- After clustering , we will use Geospatial analysis to map the
current charging locations onto the EV clusters. This will help in identifying areas with
high EV density but low charging density.

Anomaly Detection using isolation forest and other techniques: This technique will be
used to flag anomalies where there is high EV presence but insufficient infrastructure.

Association rule mining : We will use techniques like apriori algorithm or FP- growth to
identify frequent patterns in EV type, charging needs and geography. The objective
behind this is to identify user behaviour and charging patterns to optimizing station
placement.
Additional techniques : We will explore alternative techniques like Graph Neural
Networks or Shortest path analysis if the primary techniques don’t provide satisfactory
outputs.
5. Appendix
References:
1.https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html
2.https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.IsolationForest.html

Data Source:
Due to size limitations, we couldnt upload data. Use the below links to access

1.https://afdc.energy.gov/stations#/analyze
2.https://catalog.data.gov/dataset/electric-vehicle-population-data
