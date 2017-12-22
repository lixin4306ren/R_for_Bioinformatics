## 使用`biomartr`下载数据
`getMarts()`  获取可用mart数据库
`getReleases(db = "ensembl")`  获取可用的版本，包含archive  



## biomaRt
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

