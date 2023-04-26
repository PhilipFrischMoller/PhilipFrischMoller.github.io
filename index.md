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

It is natural to assume that the closer you are a to a hospital, the faster the ambulance will arrive, and thus the probability of surviving increases. Thus, the location where one is involved with a vehicular collision should, according to the assumption, impact the survivability of the collision. This naturally assumes that 1. the person is injured enough by the collision that the time spent in an ambulance is critical, and 2. the road congestion and average speed matter less than the total distance to the collision. To analyse this further, we can first plot the locations of each acute care hospital in NYC with a heat map of the collisions.

<embed type="text/html" src="imgs/map_hospital_collision.html" width="100%" height="600"/>

*Heat map showing collision locations relative to NYC hospitals*

We can compute the distance to the nearest hospital for all collisions and compute the distributions split on fatal, nonfatal, fatal motorist collisions see below interactive plot. Evidently, there is a slight difference in the mean distance to nearest hospital, with fatal motorist collision having the largest mean distance. We also see that most collisions occur within 5 km to the nearest hospital. 

<embed type="text/html" src="imgs/interactiveplot.html" width="100%" height="600"/> 

*Histograms showing distance to nearest hospital distributions*

We compute the relative severity (how many out of the total collisison are collision that result in fatalities) for collisions that occur within and outside of the 5 km radius to nearest hospital we see that collision occuring within the 5 km radius have a fatality rate of 0.59% whilst collisions occuring outside the radius have a fatality rate of 0.65%. If we only consider motorist deaths, the difference becomes even larger. Collisions within the 5 km radius have a motorist fatality rate of 0.20% whilst outside the radius, the fatality rate increaes to 0.32%. We can compare to the average fatality rate of 0.60% and the average motorist fatality rate of 0.22%. Overall, we see that collisions occuring more than 5 km away form the nearest hospital have a higher fatality rate, especially when one considers motorist deaths. 

These tendencies can naturally be explained by the speed limit increasing as you go further from the city center, where most of the hosptials are located. There are also more highways outside of the city center. Also, these do not necessarily mean that the increased fatality rates are due to long ambulance drives. What it does say is that there are signifcant number of fatal collisions that are not covered by the 5 km radius of the nearest hospital.

<embed type="text/html" src="imgs/persons_killed_hospitals.html" width="100%" height="600"/>

*Heat map showing fatal collsisions outside of the 5 km radius to nearest hospital*

5 km might not seem far, but according to [TomTom](https://www.tomtom.com/traffic-index/new-york-traffic/), the time it takes to travel 10 km is on average 24 min for 2022. That is 12 mins for 5 km distance. This does not take into account that Ambulances travel faster on average than normal cars. However, it would still take time to call the emergency services and for the ambulance to get going. Likewise, the distance given here is the straight line distance, which is significantly shorter than if one actually drove on the roads.

## Hospital Stress: Added Strain due to Distant Collisions

We can compute how many collisions occur closest to a given hospital as seen in the below bar charts. We are of course assuming that patients are transported to the nearest hospital upon colliding in traffic. 

<img src="{{site.url}}/imgs/hospitalstress.png" style="display: block; margin: auto;" />

*Bar chart showing relative strain from collision occuring > 5 km away from nearest hospital*

Notably we see that Queens Hospital center is the hospital that is closest to most collisions occuring more than 5 km away from the nearest hospital. In fact, around 50% of the fatal collisions the hospital recieves stem from collisions occuring more than 5 km away. Kings County Hospital and Coney Island Hospital also have large proportions of distant collision patients.  

# New Hospitals: Optimal locations for New Hospitals

Using Kmeans clustering, we can find optimal placements for future hospitals based solely on collision coverage. Optimally, one would get 3 more hosptials denoted as 'New Hospital 1', 'New Hospital 2' and 'New Hospital 3' in the below shown map.

<embed type="text/html" src="imgs/map_new_hospitals.html" width="100%" height="600"/>

*Plot showing how the 3 new hospitals cover collisions not covered by a 5km radius from the current hospitals*

Plotting the distance to nearest hospital distributions, it is evident that the average distance has not decreased substantially, but rather some of the more distant collisions are now closer to a hospital. 

<embed type="text/html" src="imgs/interactiveplot_newhos.html" width="100%" height="620"/> 

*Histograms showing distance to nearest hospital distributions for the additional hospitals*

<img src="{{site.url}}/imgs/hospitalstress_newhos.png" style="display: block; margin: auto;" />

*Bar chart showing relative strain from collision occuring > 5 km away from nearest hospital with the additional three hospitals included*

'New Hospital 2' has evidently taken alot of what collisions that were previously assigned to Queens. 'New Hospital 2' also leads on number of collisions resulting in fatalities. 'New Hospital 1', 'New Hospital 3' seem like huge investments that cover the least amount of total collisions. However, the addition of these new hospitals has also distributed the collisions that occur furhter than 5 km away more uniformly across the hospitals.  

What if we instead of building 3 new hospitals, we simply moved the existing hospitals to create a better covering of the collisions. This would naturally be an insanely expensive undertaking, but will serve as a good visualisation of optimal hospital locations based solely on vehicular collisions. 




