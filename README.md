# Covid-in-Americas-Largest-Cities
## Background
The pandemic has been affecting the world socially and economically nonstop. With over 124 million infections and 2.7 million deaths, the virus has had a catastrophic impact. The United States alone has 2.6 million cases with over 100,000 cases itself. To make matters worse, there are now 22 distinguishing mutations, 6 of which have the new gene that cause the virus to have enhanced transmission.

[Covid-Statistics](https://www.medicalnewstoday.com/articles/live-updates-coronavirus-covid-19#1)

[More statistics](https://www.nature.com/articles/d41586-020-00502-w)

Taking a closer look at the United States,  cases have been rapidly increasing for larger cities. The higher population density has been associated with many more infections with around 38.7 daily cases per 100k.

At the begininning of the pandemic the US national government under the leadership of Donald Trump took a hands off policy issueing guideline over had rules, leaving state and local governments to decide restrictions. Because of this along with the vast diversity of races, income, population, climate, etc. the pandemic has had different affects across much of the country. The virus is also attracted to dense populations, because of this we decided to analyze the most populous US cities to discover if certain factors affected outcome, and group cities as a launch point for further analysis.

## Business Question
Does the wealth of citizens affect covid outcomes in major American cities?
## Step by Step
#### Compiling Data
Using the Politifact list of 50 largest US cities we searched in google and to find what county we felt best represented that city. This mostly came down to a judgement call using the map and population of counties to determine what county best represents each city. We only chose a single county for each city with the exception of New York City because each borough is its own county meaning the five counties are fully within the city limits.
Using this list of counties we extracted the line of COVID data from the JHU Center for Systems Science and Engineering (CSSE) entry from March 24th, 2021. This was combined with median household income data taken from opportunity Atlas, and population data from Data Commons.
#### Regression
I began by organizing the data that I needed to perform my multiple linear regression. I used the politifact list of 50 largest U.S. cities to find the population of each of the cities while elminating the few that overlap counties. Using the list of counties, I used the Opportunity Atlas database to find the Household Incomes that corresponded with each part. Using the compiled COVID data from before, I organized the data into columns using average and Vlookup functions. I completed several analyses using different dependent variables, but I used the same two factors of Household Income and Population for each analysis. I did 3 multiple linear regressions with Covid Cases as the Y, Incident rate, and fatality rate. I utilized the Data analysis toolpak for the regression.
#### Cluster Analysis
After removing unessacary column I standardized the factors for use in the cluster analysis using Exels, average, stdev, and standarize functions. Initially I used COVID Cases, Deaths, Median household income, and population. At some point I decided to pivot and replace Cases and Deaths with incident and death rate, because these rates control for population, which is a seperate factor. Then I choose the first four cities as placeholder anchors and extracted their info using vlookup. Then I used min and sumxmy2 functions to find the associated anchor and min distance. Then using the sum of these min distances and solver with restraints I found the four anchors that minimized the total min distances. 
## Analysis
#### Regression
After running 3 different multiple linear regressions on Population, household income, covid cases, incident rate, and fatality rate I had some intriguing results. 

For the first analysis with Covid cases as the Y, there was a strong positive correlation between population and covid cases with an R^2 value of 0.9345. The value was significant as well since the P value was around 2.1E-28. On the other hand, Household income seemed to have no correlation with an insignificant p-value along with an R^2 value of 0.0025 showing almost no correlation. 
**Covid cases = 129763 + 0.10968 (population)-3.66152(Household Income)** 
When we control for the Household Income, a one-unit difference in Population is associated with a 0.10968 unit difference in Covid Cases.
![image](https://user-images.githubusercontent.com/78445017/112768723-62a50300-8feb-11eb-8220-c3dadc6cfc09.png)


For the second analysis with Incident rate as the Y, there was not much correlation between the Population and incident rate as the R^2 value was 0.0567 and insignicant P value of above 0.05. However, the Household Income versus Incident Rate was significant with a P-value of 0.02, showing a slight negative correlation. The R^2 value was 0.085 showing that the data did not follow the prediicted line that closely. 
**Incident Rate = 17013.6 + 0.00038(population)-0.20476(Household Income)**
When we control for the Household Income, a one unit difference in population is associated with a 0.00038 unit difference in Incident Rate. 
![image](https://user-images.githubusercontent.com/78445017/112768708-499c5200-8feb-11eb-857d-dc5bb48b2b48.png)


For the third analysis with the Fatality Rate as the Y, the population had a slight positive correlation with a R^2 value 0f 0.1208 and a significant P value of 0.0076. The household income was insignicant as the P-value of >0.05 but the R^2 was 0.0491 with low correlation regardless.
**Fatality Rate = 3.13714 + 1.2E-07(population)-4E-05(Household Income)**
When we control for the Household Income, a one unit difference in population is associated with a 1.2E-07 difference in fatality rate percentage. 
![image](https://user-images.githubusercontent.com/78445017/112768697-3a1d0900-8feb-11eb-997e-747bc00cb9a4.png)

Data points such as New York, Philadelphia, Chigcago, and Los Angeles stood out since their fatality, incident, and case numbers were much higher than average. This could be the explanation for why some of the best-fit lines were pulled slightly up. Overall, it seemed that Population had a much stronger effect on the dependent variable than Household income did. 
#### Cluster
I ran a four cluster analysis on the standardized factors of incident rate, fatality rate, population, and median household income. The first cluster is anchored on Sacramento with a very low incident rate, average fatality and population, with a slightly high median income. New Orleans is the second anchor with low incident and population, a very high fatality rate, and very low median income. Chicago is next with above average in all metrics with especially high population. Lastly Louisville has slightly high incidence, and slightly low across all other meterics. Noteworthy that the Chicago and New Orleans clusters each have five cities or less. While Sacramento and especially Louisville contain the vast majority of the cities. 

The Chicago cluster contains the large cities which all tended to fair worse which is in line with the regression. The New Orleans cluster contains cities that have really struggled with covid and have low incomes, which is also in line with the regression.
More interestingly the Sacramento and Louisville clusters could be seen as the "good" clusters, but cities like Philadelphia with a massive fatality rate show how that that is not necessarily true. This is likely because these clusters were too general and maybe increasing the number of clusters significantly could yield more specific clusters.

Lastly standardizing and inspecting the data reveals that New York and Detroit fared the worst and by inspection many cities in warmer climates had higher incidents rates including El Paso, Miami, and Los Angeles. 

![image](https://user-images.githubusercontent.com/78045592/112733033-f1465100-8f13-11eb-9575-e576cf7f59f2.png)

## Conclusions
The multiple linear regression providing an effective way to understand the relationship between variables in the city by city analysis. Overall it seems as though Population has a much stronger effect than household as seen with the covid cases analysis. Although for the other studies, the population was not significant, the Covid Case study was the only one that revealed a strong positive correlation for population with a high R^2 value. Household Income was only significant for the Incident rate analysis which revealed there to be a slight negative correlation between the Household Income and Incident Rate. There was a stronger negative correlation for the Incident Rate versus the Fatality Rate. As an overall conclusion, there cannot be any significant claims to be made about the effect of Household Income on Covid Cases. To improve the containment of the disease, governments could push for re-instating masking laws and to spread more awareness regarding the virus. As vaccinations are distributed further, the mortality rates will decreases, and hopefully with more awarenesss, the cases can see a decrease over time. It is not very feasible to spend more money on policies for the virus since the country is already very much in debt, but non-profit organizations and informational programs can help to convey the message and limit cases as seen in the past. [Article explaining](https://www.brookings.edu/blog/up-front/2020/03/25/where-is-the-u-s-government-getting-all-the-money-its-spending-in-the-coronavirus-crisis/)

The Cluster analysis provides a nice jumping off point for further city by city analysis. Detriot and New York should be investigated to see why things went so bad. Factors such as the a large spike in cases over a short period of time overwhelming the health care system should be looked at. The inspection of what cities had stricter policies and if they were effective is important, and comparing your city to similar ones is important for seeing what could be done better. For example New Orleans and Baltimore were very closly related so if I were making policy decisions in Baltimore I would look closely at what New Orleans has done and the outcomes, positive or negative, of those decisions. 

## Data
[JHU CSSE CSV March 24, 2021](https://github.com/CSSEGISandData/COVID-19/blob/master/csse_covid_19_data/csse_covid_19_daily_reports_us/03-24-2021.csv)

[Data Commons](https://datacommons.org/place/geoId/06037)

[Politifact 50 Largest US Cities](https://www.politifact.com/largestcities/)

[Opportunity Atlas](https://www.opportunityatlas.org/)

[Cluster Analysis](https://github.com/cmclane1/Covid-in-Americas-Largest-Cities/blob/main/Covid_Cities_Cluster.xlsx)

[Multiple Linear Regression]([Top 50 U.S. cities.xlsx](https://github.com/cmclane1/Covid-in-Americas-Largest-Cities/files/6218149/Top.50.U.S.cities.xlsx)
