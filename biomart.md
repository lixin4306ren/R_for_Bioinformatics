## `SRAdb`
R中下载SRA数据  

```
library(SRAdb)
#sqlfile <- getSRAdbFile()
sqlfile <- 'SRAmetadb.sqlite'
sra_con <- dbConnect(SQLite(),sqlfile)
rs = listSRAfile( c("SRX275878"), sra_con, fileType = 'sra' )
getSRAfile(rs$run, sra_con, fileType = 'sra' )
```

## `biomartr`
`biomartr`是`biomaRt`的拓展版，有很多相似的函数，`biomartr`的特点是基于物种为中心。   
`getMarts()`  获取可用mart数据库
`getReleases(db = "ensembl")`  获取可用的版本，包含archive  
`getDatasets(mart = "ENSEMBL_MART_ENSEMBL")`  获取某个mart里所有的datasets  
`getAttributes(mart = "ENSEMBL_MART_ENSEMBL", dataset = "mmulatta_gene_ensembl")`  列出某dataset所有可用的Attributes  
`getFilters()`  列出基因可用的和可供filter的信息  
`organismBM(organism = "Macaca mulatta")`  列出某物种所有数据库

## `biomaRt`
`listMarts()`  列出可用的数据库，基因信息为`ENSEMBL_MART_ENSEMBL`  
`listEnsemblArchives()`  列出所有archive版本  
`useMart()`  使用具体的数据库  
```
mart<-useMart("ENSEMBL_MART_ENSEMBL",dataset="ggallus_gene_ensembl",host="Jul2016.archive.ensembl.org")
```
`listDatasets()`  列出指定数据库所含的datasets  
```
listDatasets(mart)
```
`listAttributes()`和`listFilters()`  列出基因可用的和可供filter的信息  
`attributePages()`  对于大型数据库，attribute很多，`attributePages()`可以列出主要分类页  
```
listAttributes(mart)
listAttributes(mart, page="feature_page")
```

`getBM()`  获取基因信息  
```
geneinfo=getBM(filters="ensembl_gene_id",attributes=c('ensembl_gene_id','external_gene_name','description'),values=gene_id,mart=mart)
```

## `AnnotationHub`
整合NCBI，UCSC，Ensembl数据库的信息，好处是可以直接得到GRange格式的对象
```
ah <- AnnotationHub()
query(ah,c("Homo sapiens"))->hs
mcols(hs) -> hs.info

cpgi_query <- query(hs, c("CpG Islands", "UCSC", "hg19"))
### refseq
gene_query <- query(hs, c("hg19","refseq"))
d <- display(gene_query)
hs[['AH5040']]->refseq
### CGI
cpgi_query <- query(ah, c("CpG Islands", "UCSC", "hg19"))
cpgi <- ah[[names(cpgi_query)]]
```

## `Homo.sapiens`
基因信息，已经不同数据库之间的信息（如ID）转化，`Homo.sapiens`是`org.Hs.eg.db`和`TxDb.Hsapiens.UCSC.hg19.knownGene`的整合。

```
Homo.sapiens
cls <- columns(Homo.sapiens)
cls
cls <- cls[c(1,19,45)]
kts <- keytypes(Homo.sapiens)
kt <- kts[2]
kts
ks <- head(keys(Homo.sapiens, keytype=kts[2]))
ks
res <- select(Homo.sapiens, keys=ks, columns=cls, keytype=kt)
head(res)
```
