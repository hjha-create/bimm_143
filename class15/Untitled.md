# class15


``` r
b <- read.table("mm-second.x.zebrafish.tsv", sep="\t", header=FALSE)
colnames(b) <- c("qseqid","sseqid","pident","length","mismatch","gapopen",
                 "qstart","qend","sstart","send","evalue","bitscore")

hist(b$bitscore, breaks=30)
```

![](Untitled_files/figure-commonmark/unnamed-chunk-1-1.png)

``` r
plot(b$pident, b$bitscore, pch=16, cex=0.3)
```

![](Untitled_files/figure-commonmark/unnamed-chunk-1-2.png)

``` r
plot(b$pident * (b$qend - b$qstart), b$bitscore, pch=16, cex=0.3)
```

![](Untitled_files/figure-commonmark/unnamed-chunk-1-3.png)

``` r
library(ggplot2)
ggplot(b, aes(pident, bitscore)) + geom_point(alpha=0.1) 
```

![](Untitled_files/figure-commonmark/unnamed-chunk-2-1.png)

``` r
ggplot(b, aes((b$pident * (b$qend - b$qstart)), bitscore)) + geom_point(alpha=0.1) + geom_smooth()
```

    Warning: Use of `b$pident` is discouraged.
    ℹ Use `pident` instead.

    Warning: Use of `b$qend` is discouraged.
    ℹ Use `qend` instead.

    Warning: Use of `b$qstart` is discouraged.
    ℹ Use `qstart` instead.

    Warning: Use of `b$pident` is discouraged.
    ℹ Use `pident` instead.

    Warning: Use of `b$qend` is discouraged.
    ℹ Use `qend` instead.

    Warning: Use of `b$qstart` is discouraged.
    ℹ Use `qstart` instead.

    `geom_smooth()` using method = 'gam' and formula = 'y ~ s(x, bs = "cs")'

![](Untitled_files/figure-commonmark/unnamed-chunk-3-1.png)
