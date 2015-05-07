#QUANTILING
-----------------------------------------------
```
sample <- read.delim('D:\\Sample.csv',sep =',',header = T)
```

###SORTING OF THE TABLE

```
sample<-sample[order(sample$X,na.last = T,decreasing = T),]
```
###ROW NUMBER
```
sample$row <- 1:nrow(sample)
```
###CUMMULATIVE SUM
```
sample$cumsum<-cumsum(sample$X)
```
###TOTAL_SUM
```
a<-sum(sample$X)/4
b<-sum(sample$X)
```
###ASSIGNING VECTOR
```
d<-as.data.frame(seq(a,b,by=a))
d$row<-nrow(d):1
 
for(n in (nrow(d):1))
{
  sample[which(sample$cumsum<=d[n,1]),"Quartile"]<-d[n,2]
}

sample$Quartile<-as.character(sample$Quartile)
```
###QUALITY CHECK
```
t<-as.data.frame(table(sample$Quartile))
s<-as.data.frame(tapply(sample$X,sample$Quartile,sum))
```
