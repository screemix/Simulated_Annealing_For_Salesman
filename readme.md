# Implementaion of simulated annealing for travelling salesman problem optimization

Code is written as a solution for Statistical Techniques for Data Science Assignment #3, Innopolis University, S21.

## Algorithm description 

1. Sample initial $x_0$, set time step t = 0;
2. Set initial temperature T. To avoid problems with numerical overflow when calculating the exponent, set the temperature comparable with the initial value of the system’s energy;
3. Generate $x′$ from $g(x′|x_t)$. For continuous problems, the common solution is to use the normal distribution. For salesman problem, to generate new x' from distribution of paths: 1) pick two cities in the path → 2) exchange their positions in the path → 3) return the new proposed path;
4. Calculate acceptance ratio $α = \frac{p∗(x')}{p∗(x_t)}$, where p*(x) = $e^{\frac{-distance(path)}{T}}$ and where $path$ is the ordered list of cities to visit, $distance$ is the function that computes path distance;
5. Generate $u ∼ U(0,1)$. If $u ≤ α$, accept the new state $x_{t+1} = x′$, otherwise propagate the old state;
6. Reduce temperature T. Temperature annealing does not have to occur on every iteration. The temperature can be decreased every N iteration as well. There is no strict rule about this;
7. Increment t;
8. Repeat 2-8 until cooled down. The solution can be sampled before the system is cooled down, but we don't know whether this was the optimal solution.

## Data 
For algorithm testing, there were chosen 30 most populated Russian cities. Information about cities was extracted from Wikipedia - [source](https://github.com/hflabs/city).

## Code 
In the attached notebook, you can find simple data preprocessing, helper functions, algorithm implementation, experiments, and code for animation.

## Results 

![](https://i.imgur.com/ZI1PUNB.gif)

The best path distance achieved through experimentation was 17-20k km. 

Parameters, $\alpha$ and $N$ that regulate annealing speed are the main subjects for tuning. 

Visualization of convergence for different annealing speeds:

![](https://i.imgur.com/gLTknMF.jpg)
