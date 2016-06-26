## *Dispersal strategies of satellite males leave signatures in population distributions*
*Roger Shaw*
*22 Apr 2016*

Full model explanation published in Shaw 2016 (not yet available online, permalink added when possible).

### Purpose

In many animal systems, dominant males defend territories, while satellite males are pushed into lower-quality habitats.

Where exactly do these satellite males move to? Do they settle randomly in the landscape, or do they find the next most available spot?

I'm attempting to simulate potential dispersal behaviors of satellite males, to see what matches some empirical data best.

### Model

This is an individual-based model, coded in the NetLogo language.

In this model, the heterogeneous 30x30 landscape consists of patches that vary in their suitability score on a scale from 0 to 11, with a value of ’11’ representing an ideal suitable patch, and ‘0’ indicating a wholly unsuitable patch. Individuals lose health in every time step, at a linear proportion relative to the quality of the patch they are in, and losing all health results in death. An individual’s probability of successfully reproducing in a given patch is determined by a logistic function, where a patch with a suitability score of 8 gives each individual there a 50% probability of successful reproduction. A steepness value of 1.0 was chosen; this ensures that reproduction is often (but not always) successful in patches with a score of 9 and above, and are typically unsuccessful in patches with a score of 7 or below.During initialization, each individual is given a random ‘trait’ score, which affects the outcomes of intraspecific battles. Given a pre-determined carrying capacity for each patch, that number of individuals with the highest trait values are assigned as ‘dominant males’, while all others (with the lower trait values) are assigned as satellite males. Dominant males remain philopatric, while satellite males disperse according to given dispersal strategies, described below. Only dominant males are capable of reproducing, and if an individual successfully reproduces given the reproductive odds of its patch, it hatches a single individual offspring, with a trait value drawn from a Normal distribution centered on the parents’ trait value, and full health.
#### *Dispersal strategies*
In each run of the model, all satellite males followed one of four possible dispersal strategies: sensitivity to environment, sensitivity to crowds, sensitivity to both, or no sensitivity (random/passive dispersal). When sensitive to the environment, individuals assessed all patches within a given search radius, and dispersed to the patch with the greatest suitability score, other than its current patch. This search radius was drawn randomly from a poisson distribution at each time step for each individual, with a mean value of 3, which pilot study models showed to effectively link the entire landscape. In this dispersal strategy, individuals dispersed to the most suitable patch even if it was already crowded with individuals; therefore these individuals would be taking a chance that their trait values would be stronger in this new patch, compared to their original home.
When sensitive to crowds, individuals ignored all patches within their search radius that were already filled with individuals up to the carrying capacity. Among the remaining available patches, they dispersed to one chosen at random. This model assumes that individuals are blind to the suitability of a patch.
When sensitive to both environment and to crowds, individuals again ignored all patches in their search radius that were already full to the carrying capacity. Among the remaining available patches, they dispersed to the one with the best environment. This dispersal strategy is the closest to ideal habitat selection, though they remain limited by their search radius, and do not explicitly weigh individual benefits and costs.
When individuals were not sensitive to environment nor to crowds, they dispersed to a random patch within their search radius, mimicking passive movement. This strategy serves as a null model, to which the other strategies were compared to.