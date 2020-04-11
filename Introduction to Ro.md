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
M1 is and improvement over M0 as it takes into account the fact that the epidemic is limited by the size of the population, but it assumes that every patient is contagious forever. If we make the assumption that the contagious period is fixed to C days for all patienss and if we define Ro by the number of individuals *directly* contaminated by each carrier of the virus *among a population with no immunity*, we have directly:
> Ro = r x C

In this model, the proportion X<sub>inf</sub>(t) of the population that can transmit the disease at any time t is:
> X<sub>inf</sub>(t) = X(t) - X(t-C)

As people who contracted the disease more than C days ago are not contagious anymore. The equation for the propagation of the epidemic becomes:
> M2 : X(t+1) - X(t) = r x X<sub>inf</sub>(t) x (1-X(t))

or
> M2 : X(t+1) - X(t) = r x [X(t) - X(t-C)] x (1-X(t))

### Dynamics of the propagation

The dynamics of the propagation are directly dependent on the value of Ro

<img src="https://github.com/fsteiner/K81/blob/master/Comparison_R.png" width="800">  

In particular if Ro is below 1, every carrier propagates the infection to less than 1 new case over his/her contagious period, implying that the number of new daily cases will go decreasing from the start and that no epidemic will result. 
If Ro is above 1, every infected individual generates more than one new case over the contagious period until:
> Ro x  (1-X(t)) < 1

or
> X(t) > X<sub>immunity</sub> = 1 - 1/Ro

The idea that for Ro > 1 new cases keep increasing every day until a proportion of the population is reached and decrease thereafter is known as *herd immunity*. 

###  Implications for national health systems
There is no warranty that without countermeasures the peak will be compatible with the capacity of existing national health systems. Let us assume based on [1] that 5% of new cases require intensive care and let us make the additional assumption that the average stay in ICU is 10 days (probably an optimistic number in the case of COVID-19).  

<img src="https://github.com/fsteiner/K81/blob/master/Flattening_the_curve.png" width="800">  

Keeping the assumption of a contagion period of 10 days, **with Ro=3 the required ICU capacity at peak is circa 1,600 beds** per 100,000 inhabitants **2 months** after reaching 1 confirmed case per million of inhabitants (cumulated).
**With Ro=1.2 this number becomes circa only 70 beds** per 100,000 inhabitants after **11 months**. 
As a reference, **average European countries count 11.5 ICU beds per 100,000 inhabitants**, Germany having the highest ratio at 29.2 per 100,000 (source: [Wikipedia](https://en.wikipedia.org/wiki/List_of_countries_by_hospital_beds)).

<img src="https://github.com/fsteiner/K81/blob/master/Peaks.png" width="800">  

Managing the peak through the Ro (*flattening the curve*) is therefore critical.

The proportion of the population preserved from the infection also depends widely on Ro, as seen on the chart below.

<img src="https://github.com/fsteiner/K81/blob/master/Influence_of_Ro.png" width="400">  

For Ro below 1, only a small fraction of the population gets infected.
Above Ro=2, most of the population gets infected: 80% for Ro=2, 90% for Ro=2.5, 95% for R=3 and 99% for R=4.

**In conclusion, managing Ro  allows to control:**
- **The pace of the disease**
- **The magnitude of the peak of new cases, a crucial parameter in regard to the capacity of national health systems**
- **The reach of the epidemic**


### References
[1] Wei-jie Guan, Ph.D., Zheng-yi Ni, M.D., Yu Hu, M.D., Wen-hua Liang, Ph.D., Chun-quan Ou, Ph.D., Jian-xing He, M.D., Lei Liu, M.D., Hong Shan, M.D., Chun-liang Lei, M.D., David S.C. Hui, M.D., Bin Du, M.D., Lan-juan Li, M.D., et al., for the China Medical Treatment Expert Group for Covid-19, Clinical Characteristics of Coronavirus Disease 2019 in China, New England Journal of Medicine, //doi.org/10.1056/NEJMoa2002032
