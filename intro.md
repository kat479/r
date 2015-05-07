#Intro to R
source("http://www.openintro.org/stat/data/present.R")

present$girls

#Scatterplot of Boys and Girls

plot(x=present$boys, y=present$girls)
plot(x=present$boys,y=present$girls,type = 'l')

#Histogram of girls across years

plot(x=present$year,y=present$girls,type = 'h')
plot(x=present$year,present$boys+present$girls,type ='l')

#Maximum births in US
present[which.max(present$boys+present$girls),]

#Proportion of Boys over time
plot(present$year,present$boys/(present$boys+present$girls),type='l')

#Number of Years where the proportion of boys is greater than girls
nrow(present[which(present$boys>present$girls),])

#which year has maximum absolute difference between boys and girls
present[which.max(present$boys-present$girls),]

#plot of boy girl ratio
plot(present$year, present$boys/present$girls,type = 'h')
