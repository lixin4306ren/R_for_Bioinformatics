## 使用`rio`package进行文件读写，转换
```
library("rio")                                                ##根据后缀自动识别一系列文件格式，支持的文件类型见[链接](https://cran.r-project.org/web/packages/rio/vignettes/rio.html)
x <- import("mtcars.csv")
export(mtcars, "mtcars.rds")
export(mtcars, "mtcars.dta")
export(list(mtcars = mtcars, iris = iris), "multi.xlsx")      ##支持多个object写入一个excel文件，不同的sheet
convert("mtcars.dta", "mtcars.sav")                           ##直接进行文件格式转换，无需读取
```
