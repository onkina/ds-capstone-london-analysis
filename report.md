# Report

# A. Introduction/Business Problem

Over the past year, 627,000 people arrived in the UK (immigration) and 345,000 people left the UK (emigration). On a yearly basis, nearly 200,000 people move from elsewhere in the UK to live in London, while only 25,000 move the opposite way. So London is quickly increasing population density.
All of the immigrants face the challenge to find a new living place in an unknown city. How to make the right decision when selecting a neighborhood? Data analysis can help here.<BR><BR>
<B>Imagine that you receive an offer from Google London and you moving to London. What an exciting journey coming. But what do you know about London except that "London is the Capital of Great Britain?"</B><BR><BR>
Greater London is a ceremonial county of England that makes up the majority of the London region. This region forms the administrative boundaries of London and is organized into 33 local government districts  -  the 32 London boroughs and the City of London, which is located within the region but is separate from the county.<BR><BR>
The City of London is widely referred to simply as the City and is also colloquially known as the Square Mile, as it is 1.12 sq mi (716.80 acres; 2.90 km2) in area. Due to the City of London's small resident population (8706 people only), most open statistical reports lack the data for this area, so we are not able to include it in most indicators.<BR><BR>
As a result, it will be not ranked alongside other London local authorities, as the comparisons would be misleading.
In this post, I will describe how I resolved the task of London Boroughs analysis using public datasets, Foursquare API and python popular libraries. I will come up with a conclusion about what you should pay attention to when moving, based on your budget and infrastructure preferences.<br><br>
<b>This London Boroughs Analysis will be useful for everyone who faces the challenge to select where to settle in a new city.</b>

# B. Data section
    
<b>Assuming that the end-user is a person who is going to move to London, I will analyze boroughs by the next list of criteria:</b>
<li>infrastructure
<li>social equality, well-being, and safety rates
<li>rental price (1-Bdr)
<li>time to get to the City
<li>availability of a convenient transportation hub (direct tube line to the office)<br><br>  

<b>To make this analysis possible I explored the web and found the next data:</b>
<li><a href="http://www.trustforlondon.org.uk/data32">London boroughs on key poverty and inequality indicators</a>
<li><a href="https://raw.githubusercontent.com/naomiggg/the-best-borough-in-london/master/boroughs.json">List of Boroughs with their Locations and some other data</a>
<li><a href="https://wiki.openstreetmap.org/wiki/List_of_London_Underground_stations">List of London Underground stations</a>
<li><a href="https://data.london.gov.uk/dataset/average-private-rents-borough">Average Private Rents, Borough</a>
<li><a href="https://gist.github.com/cejast/2cb80a2346b2049ac5d0">London TopoJSON for every borough, including boundaries</a><br><br>

Additionally, we will grab venue data via the <b>Foursquare API</b> for infrastructure analysis.
All together these sources will help us to make a comparative analysis of Boroughs and make a recommendation what boroughs we should consider as a moving destination.

# C. Methodology

### <b>Data collection:</b>
<li>Get the data about boroughs demographical indicators from public government datasets (including Unemployment ratio, Poverty rate, etc)
<li>Get the data about boroughs locations for further visualisation on the map (including latitude,longitude that we need for Venues analysis)
<li>Get the data about rental prices
<li>Get the data about transport system (tube nodes only)
<li>Get the extended data (including Life Satisfaction Score, Happiness score, Immigrants ratio, etc)
    
### <b>Data analysis:</b>
<li>Find correlation between indicators     
<li>Analyse Boroughs by Social indicators
<li>Find what affects the rental price

### <b>Collect Venues Data</b>
<li>Use Foursquare API to extact data about venues in boroughs
<li>Cluster Neigborhoods by venues similarity
<li>Add Cluster labels for every Borough

### <b>Final data analysis</b>
<li>Visualise data that we found about the boroughs, make data understandable for independent research by end-user
<li>Make a conclusion about explored data

# D. Results / Discussion

After made analysis, we can examine each cluster and determine the discriminating venue categories that distinguish each cluster. Based on the defining categories, we can assign a name to each cluster.

<b>Just to recall what indicators we wanted to cover in such research:</b>
- housing affordability (aka average rent feature)
- infrastructure (10 Common venues by Foursquare)
- +Average Public Transport Accessibility score, 2014 (from london_details dataframe)
- +Crime rates per thousand population 2014/15 (from london_details dataframe)

<b>Some visualisation plots:</b>

<img src="https://github.com/onkina/ds-capstone-london-analysis/blob/master/poverty.png">Poverty by Boroughs</img>
<br>
<img src="https://github.com/onkina/ds-capstone-london-analysis/blob/master/poverty.png">Unemployment ratio by Boroughs</img>
<br>
<img src="https://github.com/onkina/ds-capstone-london-analysis/blob/master/correlation.png">Correlation between indicators</img>

## Demographic indicators Correlation matrix observations:

There is a strong positive correlation between:
- between Average rent and Income inequality
- between Low pay and Evictions
- between Counsil Tax Support cut and Evictions
- Out-of-work benefits and Poverty rate


Unsurprisingly, that there is a strong negative correlation between:
- Average rent and Evictions
- Average rent and Low Pay


## Cluster Observations / Conclusions

As far as we have an interactive map (check the notebook) with clustered boroughs data, we can characterize every cluster.
This information will be useful for people moving to London and considering where to settle.

<img src="https://github.com/onkina/ds-capstone-london-analysis/blob/master/Screen%20Shot%202020-04-25%20at%2016.34.38.png">

### Cluster 0 (red)

The downtown area, central transport node. Borough is full of Hotels, Gastronomical places, and Leisure Destinations such as Movie Theater, Art Gallery, or Lounge Bar.
Extra expensive rental cost (£ 2302), with a huge crime ratio of 129 points (because of pickpockets in the Tourist center).

### Cluster 1 (violet)

“Big center” + close to its areas with convenient transportation. Borough is full of Pubs, Coffee shops, Restaurants (Turkish, Italian, Indian, Japanese). Nice parks in every borough.
Mid+ rental cost (1604), with a mid+ crime ratio of 82 points.

### Cluster 2 (blue)

Green boroughs with nice Parks, Botanical Gardens, Gold Courses and Leisure places. A lot of pubs, cafe and other gastronomical places.
Mid rental cost (£ 1463), with a mid+ crime ratio of 70 points.


### Cluster 3 (green)

Suburbs. Comfortable for family living. Parks, Coffe Shops, Groceries, Supermarkets, and a variety of Cafe.
Affordable rent prices (1200). The safe sleeping area (crime ratio - 69) far from the city center.


### Cluster 4 (orange)

Outer suburbs with the cosmopolitan local community. Popular within Immigrants from India and Pakistan. A lot of Pubs, Coffee Shops, Groceries, Supermarkets, Gym points.
Affordable rent prices (£ 1360). Safe sleeping boroughs (crime ratio - 68) far from the city center.

## Discussion

The total number of measurements and population densities of the 32 London boroughs in total can vary. As there is such a complexity, very different approaches can be tried in clustering and classification studies. Moreover, it is obvious that not every classification method can yield the same high-quality results for this metropolis.

For example, in our analysis, we used just 2 demographical features from 82 covered by boroughs detailed report. So there is room for improvement of indicators coverage.

I used the Kmeans algorithm as part of this clustering study. I set the optimum k value to 5. However, only 32 district coordinates were used. For more detailed and accurate guidance, the data set can be expanded and the details of the neighborhood or street can also be drilled. One more option - examine tube station neighborhoods and make clustering around them for those users who prefer using public transport.

Also, some indicators from used reports may be outdated (some metrics are from 2014 or earlier). In future studies, these data can be replaced by more accurate fresh datasets.

# E. Conclusion

<i>Conclusion section where you conclude the report.</i>

In this educational project we successfully explored London Boroughs and made a suggestions list for potential end-user who interested in moving to London.

### Python Libraries used:
- pandas
- numpy
- seaborn
- sklearn
- matplotlib
- folium
- json
- requests

### Methodology used:
- data scrapping
- data wrangling
- data merging
- correlation analysis
- cluster analysis
- data visualisation

<b>For those who are going to work in City (like Google London) there are some recommendations:</b>

<li>- If you are willing to overpay for a proximity to the City center - consider <b>Lambeth borough</b>, the avg rent - £ 1740, high ptal rate, avg crime rate.

<li>- If you are on budget - consider <b>Lewisham borough</b>. Avg rent - £ 1318, mid+ plat rate - 4, mid crime rate.

<li>- If you are on budget,and also moving with family and you need a good social infrastructure with parks and shops - you should consider <b>Barking and Dagenham borough</b>. Avg rent - £ 1192, crime tate 83.
