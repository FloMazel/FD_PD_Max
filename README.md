# greedyFD

The "GreedyFD" function use a Traits matrix (Traits * species) and try to maximize the convex hull of k species. You can penalize the algorithm using the parameter "penal" (=T or F) and set manually the PenalK and PenalY parameters. I advice to use a wide range of paramaters and take the maximun value of the convex hull. For example, I currently use 1000 pairs of parameters drawn from a truncated normal distribution (mean=1, sd=.5) and retained the parameter pairs that yielded the maximal FD.  The "deter" parameter can be let to "TRUE" (it takes the species that maximize the convex hull at each step instead of having the possibility to take a sub-optimal solution).


