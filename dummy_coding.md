Dummy Coding Categorical Data
========================================================
Stat 2*** 
---------------------------------------------------------
Using the Turkeys data set
### 


```r
turk <- read.csv(file = "C:\\Users\\Aaron\\Documents\\Datasets\\Turkeys.csv", 
    header = T)
head(turk)
```

```
##   Age Weight Origin
## 1  28   13.3      G
## 2  20    8.9      G
## 3  32   15.1      G
## 4  22   10.4      G
## 5  29   13.1      V
## 6  27   12.4      V
```

```r
attach(turk)
```


* There are **3** levels within Origin,   
therefore we must set **1** as a reference and the other **2** as dummy coded variables.  
* The variable we select as the reference is arbitrary.

To do this we will use the **ifelse** statement 


```r
Z1 <- ifelse(Origin == "V", 1, 0)  ## Notice that TWO equals signs must be used
Z2 <- ifelse(Origin == "W", 1, 0)
```

* The first number is what the level of Origin will be equal to *if* it's *true*, **1**.  
* The second number is our *Otherwise* statement, **0** .


Creating the interactions of Age with the dummy coded variables 
#### 

```r
Z1X <- Z1 * Age
Z2X <- Z2 * Age
```


A new data frame can now be made which includes the dummy coded variables.
### 


```r
turk2 <- data.frame(turk, Z1, Z2, Z1X, Z2X)
turk2
```

```
##    Age Weight Origin Z1 Z2 Z1X Z2X
## 1   28   13.3      G  0  0   0   0
## 2   20    8.9      G  0  0   0   0
## 3   32   15.1      G  0  0   0   0
## 4   22   10.4      G  0  0   0   0
## 5   29   13.1      V  1  0  29   0
## 6   27   12.4      V  1  0  27   0
## 7   28   13.2      V  1  0  28   0
## 8   26   11.8      V  1  0  26   0
## 9   21   11.5      W  0  1   0  21
## 10  27   14.2      W  0  1   0  27
## 11  29   15.4      W  0  1   0  29
## 12  23   13.1      W  0  1   0  23
## 13  25   13.8      W  0  1   0  25
```



