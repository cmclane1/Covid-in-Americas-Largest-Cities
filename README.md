# Covid-in-Americas-Largest-Cities
## Background
Background info on pandemic like what it is (Nand)

At the begininning of the pandemic the US national government under the leadership of Donald Trump took a hands off policy issueing guideline over had rules, leaving state and local governments to decide restrictions. Because of this along with the vast diversity of races, income, population, climate, etc. the pandemic has had different affects across much of the country. The virus is also attracted to dense populations, because of this we decided to analyze the most populous US cities to discover if certain factors affected outcome, and group cities as a launch point for further analysis.

## Business Question
Does the wealth of citizens affect covid outcomes in major American cities?
## Step by Step
#### Compiling Data
Using the Politifact list of 50 largest US cities we searched in google and to find what county we felt best represented that city. This mostly came down to a judgement call using the map and population of counties to determine what county best represents each city. We only chose a single county for each city with the exception of New York City because each borough is its own county meaning the five counties are fully within the city limits.
Using this list of counties we extracted the line of COVID data from the JHU Center for Systems Science and Engineering (CSSE) entry from March 24th, 2021. This was combined with median household income data taken from opportunity Atlas, and population data from Data Commons.
#### Regression
(Nand)
#### Cluster Analysis
After removing unessacary column I standardized the factors for use in the cluster analysis using Exels, average, stdev, and standarize functions. Initially I used COVID Cases, Deaths, Median household income, and population. At some point I decided to pivot and replace Cases and Deaths with incident and death rate, because these rates control for population, which is a seperate factor. Then I choose the first four cities as placeholder anchors and extracted their info using vlookup. Then I used min and sumxmy2 functions to find the associated anchor and min distance. Then using the sum of these min distances and solver with restraints I found the four anchors that minimized the total min distances. 
## Analysis
#### Regression
(Nand)
#### Cluster
After running a four cluster analysis on the standardized factors of incident rate, fatality rate, population, and median household income. The first cluster is anchored on Sacramento with a very low incident rate, average fatality and population, with a slightly high median income. New Orleans is the second anchor with low incident and population, a very high fatality rate, and very low median income. Chicago is next with above average in all metrics with especially high population. Lastly Louisville has slightly high incidence, and slightly low across all other meterics. Noteworthy that the Chicago and New Orleans clusters each have five cities or less. While Sacramento and especially Louisville contain the vast majority of the cities. 

The Chicago cluster contains the large cities which all tended to fair worse which is in line with the regression. The New Orleans cluster contains cities that have really struggled with covid and have low incomes, which is also in line with the regression.
More interestingly the Sacramento and Louisville clusters could be seen as the "good" clusters, but cities like Philadelphia with a massive fatality rate show how that that is not necessarily true. This is likely because these clusters were too general and maybe increasing the number of clusters significantly could yield more specific clusters.

Lastly standardizing and inspecting the data reveals that New York and Detroit fared the worst and by inspection many cities in warmer climates had higher incidents rates including El Paso, Miami, and Los Angeles. 

![image](https://user-images.githubusercontent.com/78045592/112733033-f1465100-8f13-11eb-9575-e576cf7f59f2.png)

## Conclusions
(Nand put regression conclusions here)

The Cluster analysis provides a nice jumping off point for further city by city analysis. Detriot and New York should be investigated to see why things went so bad. Factors such as the a large spike in cases over a short period of time overwhelming the health care system should be looked at. The inspection of what cities had stricter policies and if they were effective is important, and comparing your city to similar ones is important for seeing what could be done better. For example New Orleans and Baltimore were very closly related so if I were making policy decisions in Baltimore I would look closely at what New Orleans has done and the outcomes, positive or negative, of those decisions. 

## Data
[JHU CSSE CSV March 24, 2021](https://github.com/CSSEGISandData/COVID-19/blob/master/csse_covid_19_data/csse_covid_19_daily_reports_us/03-24-2021.csv)

[Data Commons](https://datacommons.org/place/geoId/06037)

[Politifact 50 Largest US Cities](https://www.politifact.com/largestcities/)

[Opportunity Atlas](https://www.opportunityatlas.org/)

[Cluster Analysis](https://github.com/cmclane1/Covid-in-Americas-Largest-Cities/blob/main/Covid_Cities_Cluster.xlsx)
