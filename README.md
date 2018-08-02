# kenward_cattle

```
library(agridat)
data("kenward.cattle")
names(kenward.cattle)

library(dplyr)
allid<-unique(kenward.cattle$animal)
plot(c(0,133),c(100,400),"n")
for(ii in 1:length(allid)){
  anid<-allid[ii]
  subsetdf<-kenward.cattle%>%filter(animal==anid)
  lines(subsetdf$day,subsetdf$weight,col=subsetdf$trt[1])
}
legend("bottomright",legend=subsetdf$trt[1],lty=1,col=subsetdf$trt[1])

meandf<-kenward.cattle%>%group_by(trt,day)%>%summarise(mw=mean(weight))

plot((meandf%>%filter(trt=="A"))$mw,type="l")
lines((meandf%>%filter(trt=="B"))$mw,type="l",col="red")
```
