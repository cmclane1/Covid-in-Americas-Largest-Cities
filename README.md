# Covid-in-Americas-Largest-Cities
## Background
## Business Question
Does the wealth of citizens affect covid outcomes in major American cities?
## Step by Step
#### Compiling Data
Using the Politifact list of 50 largest US cities we searched in google and to find what county we felt best represented that city. This mostly came down to a judgement call using the map and population of counties to determine what county best represents each city. We only chose a single county for each city with the exception of New York City because each borough is its own county meaning the five counties are fully within the city limits.
Using this list of counties we extracted the line of COVID data from the JHU Center for Systems Science and Engineering (CSSE) entry from March 24th, 2021. This was combined with median household income data taken from opportunity Atlas, and population data from Data Commons.
#### Regression
#### Cluster Analysis
After removing unessacary column I standardized the factors for use in the cluster analysis using Exels, average, stdev, and standarize functions. Initially I used COVID Cases, Deaths, Median household income, and population. At some point I decided to pivot and replace Cases and Deaths with incident and death rate, because these rates control for population, which is a seperate factor. Then I choose the first four cities as placeholder anchors and extracted their info using vlookup. Then I used min and sumxmy2 functions to find the associated anchor and min distance. Then using the sum of these min distances and solver with restraints I found the four anchors that minimized the total min distances. 
## Analysis
#### Regression
#### Cluster

## Conclusions
## Data
[JHU CSSE CSV March 24, 2021](https://github.com/CSSEGISandData/COVID-19/blob/master/csse_covid_19_data/csse_covid_19_daily_reports_us/03-24-2021.csv)

[Data Commons](https://datacommons.org/place/geoId/06037)

[Politifact 50 Largest US Cities](https://www.politifact.com/largestcities/)

[Opportunity Atlas](https://www.opportunityatlas.org/)

[Cluster Analysis](https://github.com/cmclane1/Covid-in-Americas-Largest-Cities/blob/main/Covid_Cities_Cluster.xlsx)
