# ggdist_boxplot_scatter_graph
![boxplot_scatter](https://user-images.githubusercontent.com/40909985/204297083-9ce6abd1-b94e-44ca-8f56-1d33146bc53f.jpg)


library(ggdist)
library(tidyverse)
library(tidyquant)
data(mpg)
mpg %>% 
  filter(cyl %in% c(4,6,8)) %>% 
  ggplot(aes(x=factor(cyl), y=hwy, fill=factor(cyl)))+
  ggdist::stat_halfeye(
    adjust=0.5,
    justification= -.2,
    .width = 0,
    width=0.4,
    point_colour=NA
  )+
  ggdist::stat_dots(
    side="left",
    justification = 1.1,
    binwidth = .25
  )+
  scale_fill_tq()+
  theme_tq()+
  labs(title="Raincloud Plot",
       subtitle = "showing the bi-modal distribution of 6 cylinder vehicle",
       x="engine size",
       y="highway fuel economy",
       fill= "cylinders")+
  #coord_flip()+
  geom_boxplot(
    width=.12,
    outlier.color = NA,
    alpha=0.5
  )


