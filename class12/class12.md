# Class 12 Extra Credit
Harshita Jha (PID: A17350910)

## Population Scale Analysis

One sample is obviously not enough to know what is happening in a
population. You are interested in assessing genetic differences on a
population scale.

So, you processed about ~230 samples and did the normalization on a
genome level. Now, you want to find whether there is any association of
the 4 asthma-associated SNPs (rs8067378…) on ORMDL3 expression.

> Q. How many samples do we have?

``` r
expr <- read.table("rs8067378_ENSG00000172057.6.txt")
head(expr)
```

       sample geno      exp
    1 HG00367  A/G 28.96038
    2 NA20768  A/G 20.24449
    3 HG00361  A/A 31.32628
    4 HG00135  A/A 34.11169
    5 NA18870  G/G 18.25141
    6 NA11993  A/A 32.89721

``` r
nrow(expr)
```

    [1] 462

> Q13. Read this file into R and determine the sample size for each
> genotype and their corresponding median expression levels for each of
> these genotypes.

``` r
table(expr$geno)
```


    A/A A/G G/G 
    108 233 121 

``` r
box_plot <- boxplot(exp ~geno, data=expr)
```

![](class12_files/figure-commonmark/unnamed-chunk-4-1.png)

``` r
box_plot$stats[3,]
```

    [1] 31.24847 25.06486 20.07363

- The sample size for A/A is 108, A/G is 233 and G/G is 121. The medians
  are 31.24847, 25.06486 and 20.07363 respectively.

> Q14. Generate a boxplot with a box per genotype, what could you infer
> from the relative expression value between A/A and G/G displayed in
> this plot? Does the SNP effect the expression of ORMDL3?

``` r
library(ggplot2)
```

``` r
ggplot(expr) + aes(x=geno, y=exp, fill=geno) + geom_boxplot(notch=T)
```

![](class12_files/figure-commonmark/unnamed-chunk-7-1.png)

- From this plot, we can see that as the number of G alleles increases,
  the expression decreases so it can be inferred that ORMDL3 expression
  is highest in A/A, medium in A/G and lowest in G/G.

- This pattern wherein G allele increase is associated with decrease in
  expression suggests that the SNP does affect ORMDL3 expression in an
  allele-dependent way.
