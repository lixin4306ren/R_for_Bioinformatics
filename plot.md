# 使用`qplot()`快速作图
```
library(ggplot2)
qplot(displ, hwy, data = mpg, color = drv)
qplot(displ, hwy, data = mpg, geom = c("point", "smooth")) ##同时画点和线
qplot(hwy, data = mpg, facets = drv ~ ., binwidth = 2)     ##多个panel
qplot(displ, hwy, data = mpg, facets = . ~ drv) + geom_smooth()
qplot(log(eno), data = maacs, geom = "density", color = mopos)
```
