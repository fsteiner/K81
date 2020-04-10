**The object of this paper is to provide some intuition about the concept or *basic replication number (Ro)* which has gained a lot of attention in the context of the COVID-19 pandemic, and to cast some light on its impact of the dynamics of the propagation, using toy epidemiologic models. These models should not be taken as a basis for any real-world forecast.**  
*In all this document we consider the total population constant.*
## Basic models of epidemic transmission
### M0
Let us start with a basic model M0: each contaminated individual transmits the disease to r new individuals per day.
If X is the *cumulated* proportion of contaminated individuals at a certain time t expressed in days, the proportion of new cases at each period is:
> M0: X(t+1)-X(t) = r x X(t)

The resulting evolution is **exponential**:
> M0: X(t) = X(0) x (1+r)<sup>t</sup>

Or 
> M0: X(t) = X(0) x e<sup>kt</sup>

with
> k = log(1+r) 

In this simple scenario, both cumulated and new cases grow at the same exponential rate. M0 is a very simple model, valid only when a very small part of the population is contaminated.

### M1
If we take into account that people already contaminated cannot catch the disease a second time, the proportion of the population that can be contaminated on day t is in fact [1-X(t)]. Incorporating this in our second model leads to:
> M1: X(t+1) - X(t) = r x X(t) x [1-X(t)]

The resulting evolution is **a S-curve** following the *sigmoid* (also called *logistic*) function:
> M1: X(t) = 1/(1 + e<sup>-rt</sup>) 

When X(t) is small, at the beginning of the disease, the evolution is practically exponential. The number of new cases keeps growing until the proportion of the infected population reaches 50%, then new cases start decreasing. Eventually, the whole of the population gets contaminated.

### M2
M1 is and improvement over M0 as it takes into account the fact that the epidemic is limited by the size of the population, but it assumes that every patient is contagious forever. If we make the assumption that the contagious period is fixed to C, days for all patienss and if we define Ro by **the number of individuals *directly* contaminated by each carrier of the virus *among a population with no immunity***, we have directly:
> Ro = r x C

In this model, the proportion X<sub>inf</sub>(t) of the population that can transmit the disease at any time t is:
> X<sub>inf</sub>(t) = X(t) - X(t-C)

As people who contracted the disease more than C days ago are not contagious anymore. The equation for the propagation of the epidemic becomes:
> M2 : X(t+1) - X(t) = r x X<sub>inf</sub>(t) x (1-X(t))

or
> M2 : X(t+1) - X(t) = r x [X(t) - X(t-C)] x (1-X(t))

For the same daily transmission rate r, M2 therefore shows a slower growth than M1.

<img src="https://github.com/fsteiner/K81/blob/master/Comparison.png" width="800">  

Indeed, if Ro is below 1, by definition every carrier propagates the infection to less than 1 new case over his/her contagious period, meaning that the number of new daily cases will go decreasing from the start, contrary to M0 or M1.  
If Ro is above 1, every infected individual generates more than one new case over the contagious period until:
> Ro x  (1-X(t)) < 1

or
> X(t) > X<sub>immunity</sub> = 1 - 1/Ro

The idea that for Ro > 1 new cases keep increasing every day until a proportion of the population is reached and decrease thereafter is known as *herd immunity*. There is no warranty that without countermeasures the peak will be compatible with the capacity of existing national health systems. For instance, with a Ro of 3 the peak of new cases would be circa 6.5% of the population - if 2% of these new cases require intensive care for 5 days, 130 x 5 = 650 ICU beds per 100,000 inhabitants would be required. As a reference, most European countries' ratio of ICU beds is around 10 per 100,000 with the exception of Germany among major countries at around 30 per 100,000 (source: [Wikipedia](https://en.wikipedia.org/wiki/List_of_countries_by_hospital_beds)). Managing the peak through the Ro (*flattening the curve*) is therefore critical.

<img src="https://github.com/fsteiner/K81/blob/master/Flattening_the_curve.png" width="600">  

It should be noted that following M2 (and contrary to M1 and M0), a part of the population is preserved from the infection. The reach of the epidemic depends mostly on Ro, as seen on the chart below.

<img src="https://github.com/fsteiner/K81/blob/master/Influence_of_Ro.png" width="400">  

For Ro below 1, only a small fraction of the population gets infected.
Above Ro=2, most of the population gets infected: 80% for Ro=2, 90% for Ro=2.5, 95% for R=3 and 99% for R=4.

Managing the Ro therefore allows to control:
- The pace of the disease
- The final proportion of the population contracting it
- The magnitude of the peak of new cases, a crucial parameter in regard to the capacity of national health systems.
