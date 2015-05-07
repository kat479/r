-----------------------------------------------
sample <- read.delim('D:\\Roshni sacks adhoc\\Prescriber Info Sample.csv',sep =',',header = T)

#SORTING OF THE TABLE
#Quantiling
```
sample<-sample[order(sample$TRX,na.last = T,decreasing = T),]
```
###ROW NUMBER
```
sample$row <- 1:nrow(sample)
```
###CUMMULATIVE SUM
```
sample$cumsum<-cumsum(sample$TRX)
```
###TOTAL_SUM
```
a<-sum(sample$TRX)/4
b<-sum(sample$TRX)
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
s<-as.data.frame(tapply(sample$TRX,sample$Quartile,sum))
```
