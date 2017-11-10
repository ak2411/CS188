# Markov Models
## What is it
* A chain-like, infinite-length Bayes' net
* information included:
  * __initial distribution__ - enumerated by the probability table given by _Pr(W0)_
  * __transition model__ - _Pr(Wi+1|Wi)_
    * implies that the value of of _Wi+1_ is conditionally dependent __only__ on the value of Wi
    * i.e. the weather at time _t = i+1_ is a __Markov/memoryless property__
* *Pr(W0, 1, ..., Wn) = Pr(Wo)/PRODUCT/limits_{i=0 to n-1} Pr(Wi+1|Wi)* reconstruction of the joint distribution via the chain rules
* Assumptions:
  * Markov property holds true
  * Transition is __time-homogeneous__
    * i.e. no matter what _i_ is, _Pr(Wi+1|Wi)_ is identical

## The Mini-Forward Algorithm
* The problem with obtaining the distribution of a given timestep using __inference by elimination__ is that with _j_ variables with domains _d_, the size of the joint distribution is _O(d^j)_
* Pr(Wi+1) = SUM(all Wi)Pr(wi, Wi+1)
* basically, to know the probability of i+1 happening, we need to get its value independent of i's value
* problem:
  * favors in transition models can affect the distribution

## Stationary distribution
*
