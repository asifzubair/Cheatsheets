# RECOMB Genetics 2016 #

## Building catalog linking genes to the medical phenome ##
### Nancy Cox ###

- [PrediXcan](https://github.com/hakyim/PrediXcan): new approach to data integration
- [BioVU](https://victr.vanderbilt.edu/pub/biovu)
- [PheWAS](https://github.com/PheWAS/PheWAS) - package not related

## locLMM for heritability partitioning ##
### Lisa Gai ###

Accounting for linkage disequilibrium when estimating the contribution of a genomic region.
- heritability partitioning can give insights into:
  - genetic architectue
  - etc.
- LD leads to inflated heritability estimates. traditional methods ignore this

## Local joint testing improves power and identifies missing heritability in association studies ##
### Brielin Brown ###

- hidden versus missing heritability
- h^2_gwas vs. h^2_chip vs. h^2_fam
- joint testing: instead of marginal tests, use joint test to examine a pair of SNPS 
  - two degree chi-squared test
- linking masking
- literture on joint testing
  - wood et al. hum mol gen 2011
  - yang et al. nat gen 2012
  - lee et al 2011
- [paper](http://biorxiv.org/content/biorxiv/early/2016/02/18/040089.full.pdf)
- [jester](https://github.com/brielin/Jester)
- [impute2](https://mathgen.stats.ox.ac.uk/impute/impute_v2.html)
- local joint testing of all pairs of variants within __200KB of the TSS__
- Q: what about trans factors - if working within a close window of TSS

## Inferring local genealogical tree topologies from haplotypes with presence of recombination ##
### Sajad Mirzaei ###

- [RENT](http://www.computer.org/csdl/trans/tb/2011/01/ttb2011010182-abs.html), Wu, 2011
- [RENTPlus](https://github.com/SajadMirzaei/RentPlus)
- [UPGMA](https://en.wikipedia.org/wiki/UPGMA)

## Enhanced methods for gene expression imputation from genetic variation data ##
### Nicholas Mancuso ###

- impute gene expression and then use gene associations for disease
- `SNP -> GE -> Disease` 
- various regularized methods like [BLUP](https://en.wikipedia.org/wiki/Best_linear_unbiased_prediction) etc
- ensemble learning of cis-regulated expression
- [gEUVADIS](http://www.geuvadis.org/web/geuvadis;jsessionid=6C3CEC4B93669043F5EF2E9F01641051)
- 