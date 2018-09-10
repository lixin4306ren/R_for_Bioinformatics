# 使用`qplot()`快速作图
```
library(ggplot2)
qplot(displ, hwy, data = mpg, color = drv)
qplot(displ, hwy, data = mpg, geom = c("point", "smooth"))          ##同时画点和线
qplot(hwy, data = mpg, facets = drv ~ ., binwidth = 2)              ##多个panel
qplot(displ, hwy, data = mpg, facets = . ~ drv) + geom_smooth()
qplot(log(eno), data = maacs, geom = "density", color = mopos)
```
# 使用ggpubr，grid，cowplot，gridExtra排列组合图片成publish-ready figures
```
bp + font("x.text", size = 8)   ##改变x轴字体大小
bp + rremove("x.text")          ##去掉x轴文字
ggarrange(bxp, dp, bp + rremove("x.text"),   ##排列panel
          labels = c("A", "B", "C"),
          ncol = 2, nrow = 2)
annotate_figure()               ##上下左右添加注释
ggarrange(bxp, dp, labels = c("A", "B"),common.legend = TRUE, legend = "bottom")  ##use common legend
```
