# Overview of phylogenetic inference (2024-02-15)

No phylogenetic program can find the absolute optimum phylogenetic tree due to computational limitations (it is impossible to parse through the many trillions of possible trees to find the true absolute best) so we let programs run multiple times in a random search - each time finding pretty good trees - and pick the best from those. 

In general, maximum likelihood is the inference method most used right now. It is more statistically consistent and robust but costs more in computational power as compared to distance or parsimony methods. 

Phylogenetic inference is done as 2 simple steps: choose a criterion (distance, parsimony, likelihood) and then search the space of trees until you find an optimum. 

