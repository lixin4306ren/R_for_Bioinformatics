## 更改levels的名字和顺序
```
plyr::revalue(nor_merge_f_seurat@ident,c("7"="H1_C7","5"="nor2_C5","1"="nor2_C1","2"="nor4_C2","3"="nor6_C3","0"="nor4_C0","4"="nor6_C4","6"="nor6_C6")) -> nor_merge_f_seurat@ident
forcats::fct_relevel(nor_merge_f_seurat@ident,"H1_C7","nor2_C5","nor2_C1","nor4_C2","nor6_C3","nor4_C0","nor6_C4","nor6_C6") -> nor_merge_f_seurat@ident

```
