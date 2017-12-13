## 使用`brewer.pal()`和`colorRampPalette()`
```
library(RColorBrewer)
display.brewer.all()                 ##显示所有颜色组合
cols <- brewer.pal(3, "BuGn")        ##从"BuGn"颜色set里选3个颜色
pal <- colorRampPalette(cols)        ##生成pal函数
image(volcano, col = pal(20))        
```
