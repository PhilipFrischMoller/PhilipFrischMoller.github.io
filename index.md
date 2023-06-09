---
title: A Deep Dive Into Vehicular Collisions in NYC 
---

The below visualistations stem from the linked [iPython notebook](https://github.com/PhilipFrischMoller/PhilipFrischMoller.github.io/blob/main/code/Explainer_v1.ipynb) and is based on the plan detailed in this [video](https://youtu.be/pFTp2CmEs8E).

<img src="{{site.url}}/imgs/meme.gif" style="display: block; margin: auto;" />

# Deadly Roads

Globally, 1.35 million people are killed on roadways every year which means that almost 3,700 people are killed every single day. The Association for Safe International Road Travel (ASIRT) reports that traffic related injuries are the leading cause of death among people aged 5 to 29. In addition to the devastation and loss of life, traffic accidents also cause considerable financial losses to the individuals and families involved. Due to the lost productivity, time taken off by family members etc, the average country looses 3 percent of their GDP due to traffic related accidents. 

In NYC alone, 2,247 people have lost their lives on the streets due to traffic accidents from 2013 to 2022. 485,445 have similarily been injured. 

<embed type="text/html" src="imgs/killedpie.html" width="100%" height="600"/>

<embed type="text/html" src="imgs/injuredpie.html" width="100%" height="600"/>

*Pie charts visualising the representation of different victim types in NYC from 2013 to 2022*

This online magazine will dive deeper into traffic accidents that cause death and injury, in NYC from 2013 to 2022. We aim to investigate hospital coverage and figure out whether the distance to the hospitals play a role in the deadliness of the accidents, and model optimal new locations for hospitals in NYC.

<embed type="text/html" src="imgs/map_person_death.html" width="100%" height="600"/>

*Heat map showing deaths in NYC caused by vehicular Collisions between 2013 and 2022*


<embed type="text/html" src="imgs/yearheatmap.html" width="100%" height="950"/>

*Interactive plot showing amount of collisions per postal code per year*


# A step back: Exploring the Data

We start by looking at vehicular collisions and how they evolve over time to see if there are any tendencies. Evidently, most collisions occur in the weekdays during rush hour both mornings and evenings after work. There has been a significant decrease in collision rates in the last few years, although, there has been no significant change in the mortality rate. Interestingly, it seems that mortalities occur mostly in the weekends, where the collision rate is lowest. 

What is perhaps counter intuitive is that most of the collisions occur during the summertime. One would have otherwise assumed it would have been during the winter as the weather would be statistically worse for driving. 


<img src="{{site.url}}/imgs/time series.png" style="display: block; margin: auto;" />

*Plot showing how collision and mortality rates evolve over time*

Taking a look at the contributing factors for the collisions, it is evident that driver distractions cause the highest number of accidents. Unsafe speeds, i.e., speeding, is one of the top contributing factors for death in traffic. There is less traffic during most weekends and as such vehicles drive substantially faster on average. Furthermore, Fridays and weekends tend to also lend themselves more to the consumption of alcohol which is also in the top 10 contributing factors for traffic fatalities. This also neatly explains the peak in fatalities up and around midnight. 


<img src="{{site.url}}/imgs/causes_death.png" style="display: block; margin: auto;" />

*Top 10 contributing factors for collisions*


We shall now look at where the most severe collision occurs. As evident from the below plots, all boroughs are equally represented in terms of collision severity, although Staten Island seems to host, on average, more severe collisions. When we differentiate between victim types, i.e., motorists, cyclists and pedestrians, we see that pedestrians are killed more in the inner city. Queens, Staten Island and the Bronx share high motorist fatalities. This all seems to indicate that the collisions severity is somehow linked to the location of the collision. 

<img src="{{site.url}}/imgs/boroughsprob.png" style="display: block; margin: auto;" />

*Plots showing the probability of injury and death across boroughs, for all collisions (including collision that cause no injury or death)*

<img src="{{site.url}}/imgs/boroughs.png" style="display: block; margin: auto;" />

*Plots showing the probability of injury and death across boroughs, for different victim categorisations*

# NYC Hospitals: Distance to Nearest Hospital

It is natural to assume that the closer you are a to a hospital, the faster the ambulance will arrive, and thus the probability of surviving increases. Thus, the location where one is involved with a vehicular collision should, according to the assumption, impact the survivability of the collision. This naturally assumes that 1. the person is injured enough by the collision that the time spent in an ambulance is critical, and 2. the road congestion and average speed matter less than the total distance to the collision. To analyse this further, we can first plot the locations of each acute care hospital in NYC with a heat map of the collisions.

<embed type="text/html" src="imgs/map_hospital_collision.html" width="100%" height="600"/>

*Heat map showing collision locations relative to NYC hospitals*

We can compute the distance to the nearest hospital for all collisions and compute the distributions split on fatal, nonfatal, fatal motorist collisions see below interactive plot. Evidently, there is a slight difference in the mean distance to nearest hospital, with fatal motorist collision having the largest mean distance. We also see that most collisions occur within 5 km to the nearest hospital. 

<embed type="text/html" src="imgs/interactiveplot.html" width="100%" height="620"/> 

*Histograms showing distance to nearest hospital distributions*

18.5% of collisions that result in death or injury fall outside of the 5 km radius to nearest hospital.

We compute the relative severity (how many out of the total collisions are collisions that result in fatalities) for collisions that occur within and outside of the 5 km radius to nearest hospital we see that collision occurring within the 5 km radius have a fatality rate of 0.59% whilst collisions occurring outside the radius have a fatality rate of 0.65%. If we only consider motorist deaths, the difference becomes even larger. Collisions within the 5 km radius have a motorist fatality rate of 0.20% whilst outside the radius, the fatality rate increase to 0.32%. We can compare to the average fatality rate of 0.60% and the average motorist fatality rate of 0.22%. Overall, we see that collisions occurring more than 5 km away form the nearest hospital have a higher fatality rate, especially when one considers motorist deaths. 

These tendencies can naturally be explained by the speed limit increasing as you go further from the city centre, where most of the hospitals are located. There are also more highways outside of the city centre. Also, these do not necessarily mean that the increased fatality rates are due to long ambulance drives. What it does say is that there are significant number of fatal collisions that are not covered by the 5 km radius of the nearest hospital.

<embed type="text/html" src="imgs/persons_killed_hospitals.html" width="100%" height="600"/>

*Heat map showing fatal collisions outside of the 5 km radius to nearest hospital*

5 km might not seem far, but according to [TomTom](https://www.tomtom.com/traffic-index/new-york-traffic/), the time it takes to travel 10 km is on average 24 min for 2022. That is 12 mins for 5 km distance. This does not consider that Ambulances travel faster on average than normal cars. However, it would still take time to call the emergency services and for the ambulance to get going. Likewise, the distance given here is the straight-line distance, which is significantly shorter than if one actually drove on the roads.

## Hospital Stress: Added Strain due to Distant Collisions

We can compute how many collisions occur closest to a given hospital as seen in the below bar charts. We are of course assuming that patients are transported to the nearest hospital upon colliding in traffic. 

<img src="{{site.url}}/imgs/hospitalstress.png" style="display: block; margin: auto;" />

*Bar chart showing relative strain from collision occurring > 5 km away from nearest hospital*

Notably we see that Queens Hospital centre is the hospital that is closest to most collisions occurring more than 5 km away from the nearest hospital. In fact, around 50% of the fatal collisions the hospital receives stem from collisions occurring more than 5 km away. Kings County Hospital and Coney Island Hospital also have large proportions of distant collision patients.  

# Solution: New Hospitals?

## Optimal locations for New Hospitals

Using Kmeans clustering, we can find optimal placements for future hospitals based solely on collision coverage. We can then compute the mean shortest distance to a hospital given the addition of new hospitals. The incremental impact of additional hospitals shows that after 3 new hospitals, we can decrease the average shortest distance by 0.5 km. This small decrease is likely limited by the spread-out nature of the collisions that are more than 5 km away from the nearest hospital.

<img src="{{site.url}}/imgs/mean.png" style="display: block; margin: auto;" />

*Average shortest distance to hospital given the addition of new hospitals. The teal line represents the current mean distance without any additional hospitals*

Using Kmeans inertia gradients, optimality is reached when NYC builds 3 additional hospitals denoted as 'New Hospital 1', 'New Hospital 2' and 'New Hospital 3' in the below shown map. Optimality is based on the coverage of collisions occurring over 5 km away from the nearest hospital.

<embed type="text/html" src="imgs/map_new_hospitals.html" width="100%" height="600"/>

*Plot showing how the 3 new hospitals cover collisions not covered by a 5km radius from the current hospitals*

The mean distance to nearest hospital has decreased to 2.97 km. There are now only 9.8% of collisions that fall outside of the 5 km radius. The addition of the 3 new hospitals has actually made it such that the mortality rate outside of the 5 km is more or less equal to inside the 5 km radius (0.66% and 0.60% respectively.)

<embed type="text/html" src="imgs/interactiveplot_newhos.html" width="100%" height="620"/> 

*Histograms showing distance to nearest hospital distributions with the additional hospitals*

<img src="{{site.url}}/imgs/hospitalstress_newhos.png" style="display: block; margin: auto;" />

*Bar chart showing relative strain from collision occurring > 5 km away from nearest hospital with the additional three hospitals included*

'New Hospital 2' has evidently taken a lot of what collisions that were previously assigned to Queens. 'New Hospital 1' also leads on number of collisions resulting in fatalities. This is probably a good choice for a new additional hospital. The addition of these new hospitals has also distributed the collisions that occur further than 5 km away more uniformly across the hospitals.  

## Rellocation of Existing Hospitals

What if we instead of building 3 new hospitals, we simply moved the existing hospitals to create a better covering of the collisions. This would naturally be an insanely expensive undertaking but will serve as a good visualisation of optimal hospital locations based solely on vehicular collisions which in turn says a lot about the occurrence rate densities. 

<embed type="text/html" src="imgs/persons_killed_hospitals.html" width="100%" height="600"/>

*Heat map showing fatal collisions alongside a 5 km radius from each newly relocated hospital*

We note that after the relocation of all 11 hospitals, we are left with a mean shortest distance to hospital of 2.85, which is shorter than the addition of 5 extra hospitals. Further more, we can see that the collisions are asigned alot more uniformly between the hospitals or cluster centers. However, when we look at fatality rates the picture is not as good. We see a relative fatality rate of 0.77% outside of the 5 km radius and 0.59% within the 5 km radius. For motorists its 0.40% and 0.21% respectively. This naturally means that the hospital coverage covers less of the fatal accidents than the original setup. This is likely due to the worse coverage within the city center where most pedestrian accidents occur and as we have seen, pedestrians are far more likely to die in an accident.

<img src="{{site.url}}/imgs/hospitalstress_v2.png" style="display: block; margin: auto;" />

*Bar chart showing relative strain from collision occurring > 5 km away from nearest hospital after the relocation of all current hospitals*

<embed type="text/html" src="imgs/interactiveplot_newhos_v2.html" width="100%" height="620"/> 

*Interactive bar chart showing the distance to hospital distribution split on different collision severities*

We can finally, based on the above interactive bar chart, that the relocation yields almost identical distance to nearest hospital distributions across the different severity types which is indeed optimal and could mean that the we capture most of the variance in the data set. 

# Concluding words

This has been an interactive deep dive into NYC vehicular collisions and how one would, in the ideal world where cost is of negliable concern, place hospitals to better cover the vehicular collisions. We also investigated the inherent tendencies in the collisions and how this can also lead to a better understanding of some social mechanisms that exist in society. We have also seen how the current hospital locations actually, in some metrics, outperforms the optimised locations. For the best coverage of vehicular accidents it is recommended to build more hospitals.

