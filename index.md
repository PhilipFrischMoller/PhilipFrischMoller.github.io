---
title: A Deep Dive Into Vehicular Collisions in NYC 
---
.

<img src="{{site.url}}/imgs/meme.gif" style="display: block; margin: auto;" />

# Deadly Roads

Globally, 1.35 million people are killed on roadways every year which means that almost almost 3,700 people are killed every single day. The Association for Safe International Road Travel (ASIRT) reports that traffic related injuries are the leading cause of death among people aged 5 to 29. In addition to the devastation and loss of life, traffic accidents also cuase considerable financial losses to the individuals and families involved. Due to the lost productivity, time taken off by family members etc, the average country looses 3 percent of their GDP due to traffic related accidents. 

This online magazine will dive deeper into traffic accindents that cause death and injury, in NYC from 2013 to 2022. We aim to investigate hopsital coverage and figure out whether the distance to the hospitals play a role in the deadliness of the accidents, and model optimal new locations for hosptials in NYC.

<embed type="text/html" src="imgs/map_person_death.html" width="100%" height="600"/>

*Heat map showing deaths in NYC caused by vehicular Collisions between 2013 and 2022*

# A step back: Exploring the Data

We start by looking at vehicular collisions and how they evolve over time to see if there are any tendencies. Evidently, most collisions occur in the weekdays during rush our both mornings and evenings after work. There has been a significant decrease in collision rates in the last few years, although, there has been no significant change in the mortality rate. Interestingly, it seems that mortalities occur mostly in the weekends, where the collision rate is lowest. 

<img src="{{site.url}}/imgs/time series.png" style="display: block; margin: auto;" />

*Plot showing how collision and mortality rates evolve over time*

Taking a look at the contributing factors for the collisions, it is evident that driver distractions cause the highest number of accidents. Unsafe speeds, i.e., speeding, is one of the top contributing factors for death in traffic.  

<img src="{{site.url}}/imgs/causes_death.png" style="display: block; margin: auto;" />

*Top 10 contributing factors for collisions*

When a fatal collision occurs, the vast majority has only one fatality as shown in the pie chart below. This means that the other people involved got away with nonfatal injuries or the accident simply only involved a single person.

<img src="{{site.url}}/imgs/deathpie.png" style="display: block; margin: auto;" />

*Pie chart showing how many people die in a deadly traffic accident*

We shall now loook at where the most severe collision occur. As evident from the below plots, all boroughs are more or less equally represented in terms of collision severity, although Staten Island seems to host, on average, more severe collisions. When we differenitate between victim types, i.e. motorists, cyclists and pedestrians, we see that pedestrians are killed more in the inner city. Queens, Staten Island and the Bronx share high motorist fatalities. This all seems to indicate that the collions severity is somehow linked to the location of the collision. 

<img src="{{site.url}}/imgs/boroughsprob.png" style="display: block; margin: auto;" />

*Plots showing the probality of injury and death across boroughs, for all collisions (including collision that cause no injury or death)*

<img src="{{site.url}}/imgs/boroughs.png" style="display: block; margin: auto;" />

*Plots showing the probality of injury and death across boroughs, for different victim categorisations*


# NYC Hospitals: Distance to Nearest Hospital

It is natural to assume that the closer you are a to a hospital, the faster the ambulance will arrive, and thus the probability of surviving increases. Thus, the location where one is involved with a vehicular collision should, according the assumption, impact the survivability of the collision. This naturally assumes that 1. the person is injured enough by the collision that the time spent in an ambulance is critical, and 2. the road congestion and average speed matter less than the total distance to the collision. To analyze this futher, we can first plot the locations of each accute care hospital in NYC with a heat map of the collisions.

<embed type="text/html" src="imgs/map_hospital_collision.html" width="100%" height="600"/>

