# Report

# A. Introduction/Business Problem

Over the past year, 627,000 people arrived in the UK (immigration) and 345,000 people left the UK (emigration). On a yearly basis, nearly 200,000 people move from elsewhere in the UK to live in London, while only 25,000 move the opposite way. So London is quickly increasing population density.
All of the immigrants face the challenge to find a new living place in an unknown city. How to make the right decision when selecting a neighborhood? Data analysis can help here.<BR><BR>
<B>Imagine that you receive an offer from Google London and you moving to London. What an exciting journey coming. But what do you know about London except that "London is the Capital of Great Britain?"</B><BR><BR>
Greater London is a ceremonial county of England that makes up the majority of the London region. This region forms the administrative boundaries of London and is organized into 33 local government districts  -  the 32 London boroughs and the City of London, which is located within the region but is separate from the county.<BR><BR>
The City of London is widely referred to simply as the City and is also colloquially known as the Square Mile, as it is 1.12 sq mi (716.80 acres; 2.90 km2) in area. Due to the City of London's small resident population (8706 people only), most open statistical reports lack the data for this area, so we are not able to include it in most indicators.<BR><BR>
As a result, it will be not ranked alongside other London local authorities, as the comparisons would be misleading.
In this post, I will describe how I resolved the task of London Boroughs analysis using public datasets, Foursquare API and python popular libraries. I will come up with a conclusion about what you should pay attention to when moving, based on your budget and infrastructure preferences.

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
