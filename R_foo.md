# Learning R


R seems to be worthy of its own/separate doc.  

Install R and Rstudio shown in [workstation](./workstation_tips.md)

## Example App using Motor Trend Car Road Tests dataset

Start Rstudio  
Click on the small + in the upper-right hand corner  
Click "R Script   Ctrl + Shift + N"  
Enter the following:
```
library(datasets)
data("mtcars")
head(mtcars,5)
```

Then...  
In the console, install the ggplot2 library (this may take a little while to download/install)
```
install.packages("ggplot2", dep=T)
```

Enable ggpairs
```
install.packages('GGally')
```

### Create a scatterplot
```
ggplot(aes(x=disp,y=mpg,),data=mtcars)+geom_point()
```

### Add a title
```
ggplot(aes(x=disp,y=mpg,),data=mtcars)+geom_point()+ggtitle("displacement vs miles per gallon")
```
 
### Update Axis Name 
```
ggplot(aes(x=disp,y=mpg,),data=mtcars)+geom_point()+ggtitle("displacement vs miles per gallon") + labs(x = "Displacement", y = "Miles per Gallon")
```

### Create a boxplot of the the distribution of mpg for the individual Engine types vs Engine (0 = V-shaped, 1 = straight) NOTE: V-shape and straight are engine layout types "V6" vs "inline-6"
```
#make vs a factor
mtcars$vs <- as.factor(mtcars$vs)
# create boxplot of the distribution for v-shaped and straight Engine
ggplot(aes(x=vs, y=mpg), data = mtcars) + geom_boxplot()
```

### Add some color to boxes
```
ggplot(aes(x=vs, y=mpg, fill = vs), data = mtcars) + 
  geom_boxplot(alpha=0.3) +
  theme(legend.position="none")
```

### Now, create a histogram
```
ggplot(aes(x=wt),data=mtcars) + geom_histogram(binwidth=0.5)
```
