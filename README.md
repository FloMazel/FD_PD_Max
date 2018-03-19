# FD_PD_Max
# -----------

The set of functions presented here are related to the following preprint: 
Mazel, F., Pennell, M., Cadotte, M., Diaz, S., Dalla Riva, G., Grenyer, R., ... & Pearse, W. (2018). Is phylogenetic diversity a surrogate for functional diversity across clades and space?. bioRxiv, 243923.

https://www.biorxiv.org/content/early/2018/01/09/243923

Basically it consists of a function that maximize PD ("GreedyMMD") and one function that maximizes PD ("GreedyFD")

# GreedyMMD

This function maximizes PD for k species given a phylogenetic tree. 
The algorithm is from Bordewich et al. (2008)

Bordewich, M., Rodrigo, A., Semple, C. & Collins, T. Selecting Taxa to Save or Sequence: Desirable Criteria and a Greedy Solution. Syst. Biol. 57, 825–834 (2008).


# GreedyFD

This function maximizes FD (Convex Hull) for k species given a set of traits. 
The algorithm is from Mazel et al. (2018)

Briefly, the "GreedyFD" function use a Traits matrix (Traits * species) and try to maximize the convex hull of k species. You can penalize the algorithm using the parameter "penal" (=T or F) and set manually the PenalK and PenalY parameters. I advice to use a wide range of paramaters and take the maximun value of the convex hull. For example, I currently use 1000 pairs of parameters drawn from a truncated normal distribution (mean=1, sd=.5) and retained the parameter pairs that yielded the maximal FD.  The "deter" parameter can be let to "TRUE" (it takes the species that maximize the convex hull at each step instead of having the possibility to take a sub-optimal solution).

The algorithm is as follow (see Mazel et al 2018 for mroe details and justificaitons)

Step 1. Select the two species with the highest trait distance

Step 2. Compute the centroid of these two selected species

Step 3. Compute distances between species not in the set and this ‘set centroid’. 

Step 4. Penalize these distance by adding the following factor f (Eq. 1)

        f = K x eL x minD					  (eq. 1)
        
        with K and L being penalizing factors and minD the distance between a given candidate species and the nearest species             already in the selected set. 
        
Step 5. Select the species that maximized the penalized distance

Step 6. Go back to step one with this new set of species until the desired number of species is reached. 

