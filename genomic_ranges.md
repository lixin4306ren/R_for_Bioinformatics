## GRange更改chr名称风格
`seqlevelsStyle(gene) <- "UCSC"`更改chr风格

## 只保留主要染色体，去除random等chr
gene <- keepStandardChromosomes(gene，pruning.mode = "coarse")

