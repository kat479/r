#Intro to Data
```
source("http://www.openintro.org/stat/data/cdc.R")
```
###Number of Cases and Variables
```
dim(cdc)
```
###Type of Variable
```
str(cdc)
attributes(cdc$genhlth)
table(cdc$weight)
table(cdc$smoke10)
```
###Numerical summary for Gender
```
summary(cdc$gender)
```
###Relative frequency distribution of Genhlth
```
plot(table(cdc$genhlth)/nrow(cdc),type='h')
t<-table(cdc$genhlth)/nrow(cdc)
```
###mosaicplot
```
mosaicplot(table(cdc$gender,cdc$smoke100))
```
###number of people who are aged less than 23 and smoked 100 
```
nrow(cdc[which(cdc$age<=23 & cdc$smoke100 ==1),])
```
###boxplot
```
boxplot(cdc$height~cdc$gender)
```
###Calculation of BMI
```
cdc$bmi <- (cdc$weight / cdc$height^2) * 703
boxplot(cdc$bmi ~ cdc$genhlth)
```
###Mean across general health category
```
mean<-as.data.frame(tapply(cdc$bmi,cdc$genhlth,mean))
median<-as.data.frame(tapply(cdc$bmi,cdc$genhlth,median))
```
###Histograms
```
hist(cdc$age)
hist(cdc$bmi)
hist(cdc$bmi,breaks=50)
```
#Scatter plot between Weight and Desired Weight
```
plot(cdc$weight,cdc$wtdesire)
```
