
# Distribution Selection

We've covered some important distributions thus far: binomial, uniform, poisson, geometric, exponential, and of course, the normal distribution! Now it's time to put those all together and practice selecting the appropriate distribution for various scenarios.  
  
Here's a brief recap:  

**Binomial Distribution**  
Given the probability of success (such as flipping a coin; Heads vs Tails) what is the probability of 2 successes on 5 trials?  
  
**Uniform Distribution**  
Everything has equal probability of occuring.  
  
**Poisson Distribution**  
Useful for calculating the probability of a discrete number of events occuring during a given time period. (Generally used when this number is small; as the average grows large the normal distribution becomes a good approximation.)  
  
**Geometric Distribution**  
Related the binomial distribution and bernoulli trials. Rather then asking the probability of X success in Y trials, asks for the probability that the first success is on the nth trial.  
  
**Exponential Distribution**  
Has a memoryless property where the probability of success in the next block of time is the same whether or not another success just happened, or a substantial period of time has already passed. *If the total expected number of events is poisson distributed, the time between events is exponentially distributed.*  
  
**Normal Distribution**  
The classic [symmetrical] bell shaped curve. Also known as the Gaussian distribution. Often the assumed distribution for unknown variables (including error).  

# Car Sales
A car sales person sells an average of 2 cars per week. What's the probability that he/she sells 4 in a given week?


```python
import scipy.stats as st
```


```python
st.poisson.pmf(4, 2)
```




    0.09022352215774178



# Car Sales 2
What's the probability that the car salesperson sells 0 cars in a given week?


```python
st.poisson.pmf(0,2)
```




    0.1353352832366127



# Car Sales 3
Whats' the probability that the car salesperson sells 0 cars in 2 consecutive weeks?


```python
st.poisson.pmf(0,2)**2
```




    0.018315638888734182



or


```python
st.poisson.pmf(0,4)
```




    0.01831563888873418



# Car Sales 4!
The sales associate is worried about not getting paid for a period of time. What's the probability that 2 weeks (or more) pass between selling one car and the next?


```python
import scipy.stats as st
```


```python
1 - st.expon.cdf(2, scale=0.5)
```




    0.01831563888873422



# SAT Scores
Below is a sample of SAT scores (yes SAT scores are now out of 2400 not 1600):
Assuming the sample is representative, what would be the estimated percentile rank be of someone who scored a 2000?


```python
import numpy as np
```


```python
 scores = [1710, 1460,2060,1010,1690,1080,1940,1050,1020,1280,
 1240,1570,1690,910,1570,1440,1530,1700,1750,1320,
 2050,1430,1340,960,1480,890,1620,1280,1750, 1490]
```


```python
import scipy.stats as st
z = (2000-np.mean(scores))/np.std(scores)
st.norm.cdf(z)
```




    0.9578688788330638



# Coin Flips
Assuming that you're using a fair coin, what's the probability of flipping 8 heads on 10 flips?


```python
st.binom.pmf(8,10,0.5)
```




    0.04394531249999999



# Coin Flips 2
What's the probability that you have to flip a coin 5 times in order to get the first head?


```python
st.geom.pmf(5, 0.5)
```




    0.03125



# Trains
Assuming the train system is on a perfect schedule where trains show up exactly every 10 minutes (ignoring reality).
What is the probability that a rider who randomly shows up has to wait at least 3 minutes for a train?


```python
#Uniform Distribution;
.7
```




    0.7


