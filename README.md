# Introduction-R

Teaching page (Drafted July 2022). 

TIP: Learn, Unlearn & Relearn.

# Operations in R

```R

height <- 1.81
weight <- 75
age    <- 26
job    <- "Researcher"

########################
# Generating Sequences
########################

rep(c(1:4),3)
rep(c(1:4), times = 3)
rep(c(1:4), each = 3)

seq(from = 1, to = 4, by = 1)
seq(4,19,3)

########################
# Generating Matrices
########################

y <- matrix(1:9, nrow=3, ncol=3)
y <- matrix(1:9, nrow=3, ncol=3, byrow=TRUE)

> y[1,2]
> y[1,]
> y[2,]

# Creating matrices in R
z <- rep(0,times=3*4)
dim(z) <- c(3,4)
z

z <- matrix( 0 , nrow = 3, ncol = 3 )
A <- matrix( 0, nrow = 3, ncol = 3 )
B <- matrix( 0, nrow = 3, ncol = 3 )

A[1,1] <- -2
A[1,2] <- 3
A[1,3] <- 1
A[2,1] <- 0
A[2,2] <- 0.5
A[2,3] <- 4
A[3,1] <- -3
A[3,2] <- 5
A[3,3] <- 3.5

B[1,1] <- -8
B[1,2] <- 4
B[1,3] <- 1
B[2,1] <- 2
B[2,2] <- 0.5
B[2,3] <- -4
B[3,1] <- 6
B[3,2] <- 2
B[3,3] <- 3

A %*% B
A * B

diag(5)
diag(A)
diag(B)
diag(A %*% B)
diag(A * B)

########################
# Generating Vectors 
########################

x <- c(10.4, 5.6, 3.1, 6.4, 21.7)
v <- 2*x + 1/x

min(x)
max(x)
range(x)
length(x) 

sum(x) 
prod(x)
mean(x)
var(x) 
sum((x-mean(x))^2)/(length(x)-1)

############################
# Descriptive Data Analysis
############################

Data_example <- rnorm( n = 100, mean = 10, sd = 5 )
summary( Data_example )
density( Data_example )
stem( Data_example )
hist( Data_example )
boxplot( Data_example )

```

# Looping in R

```R

# While Loop
i <- 1
while(i <= 7)
{
  print(i)
  i <- i + 1
}

# Repeat Loop
i <- 1
repeat
{
  print(i)
  i <- i + 1
  if(i > 10)	
  {
    break
  }
}

# For Loop
for(i in 1:n) { < do operations in for loop > }

for(i in (1:4)) print(i)
for(i in (1:4)^2) print(i)
for(i in (1:4)^2) cat(i," ")
for(i in (1:4)^2) cat(i,"\n")

for (i in -2:4) {cat(i);cat("  ",i^2,"\n")} 

########################
# Conditional Execution
########################

A <- -2
if( A <0 ) { Abs.A <- (-1)*A }
Abs.A

A <- 1
B <- 2
if((A>2) || (B>2)) { C <- 1 } else { C <- 0 }

```

# Functions in R

```R

# Example 1 
incomes      <- c(60, 49, 40, 61, 64, 60, 59, 54, 62, 69, 70, 42, 56, 61, 61, 61, 58, 51, 48, 65, 49, 49, 41, 48, 52, 46, 59, 46, 58, 43)
income_means <- tapply( X=incomes, INDEX=statef, FUN=mean)

std_error        <- function(x) sqrt( var(x)/length(x) )
income_std_error <- tapply( incomes, statef, std_error )

# Example 2 
average <- function(a,b) 
{ 
  compute_average <- (a+b)/2 
  return ( compute_average )
}

ave <- average(4,6)
> ave

# Example 3
Stand_dev_function <- function( y )
{  
  SD       <- sqrt( var( y ) )
  return ( SD )
}

> Stand_dev_function(  vector_x )

```

# Installing R packages 

```R

# Install R package 'insuranceData'
install.packages( "insuranceData" )

# Call the R Library
library( insuranceData )

# Importa data from the R package 'insuranceData'
data( AutoClaims )
head( AutoClaims )

> head( AutoClaims )
     STATE CLASS GENDER AGE    PAID
1 STATE 14   C6       M  97 1134.44
2 STATE 15   C6       M  96 3761.24
3 STATE 15   C11      M  95 7842.31
4 STATE 15   F6       F  95 2384.67
5 STATE 15   F6       M  95  650.00
6 STATE 15   F6       M  95  391.12

age_variable    <- AutoClaims$AGE 
claims_variable <- AutoClaims$PAID

hist( claims_variable )

```

# Distribution Theory

## Example 1

```R

function (n) 
{ 
  # Let u be the sample of uniform distribution
  u<-runif(n)  
  
 # Let x be the new sample of the inverse of the given cdf
  x<-( sqrt(-log(1-u)) ) 
  
  makelabel<-paste(as.character(n), "samples from F(x)=1-exp(-x^2)")
  hist(x, prob=TRUE, main=makelabel, xlab='Sample value', ylab='Density')
  curve( (2*x*exp(-(x^2)) ), add=TRUE, col='red')
 
  # the function returns the sample median of the distribution
  return (median(x)) 
}

```

## Example 2

```R

############################
## Geometric Distribution ##
############################

N <- 1000
p <- 0.209205

U <- runif(N)
X <- log(U)/ log(1-p)
Y <- rgeom(N,p)

par(mfrow=c(1,2))
hist(X,freq=F,main="Geom from Uniform")
hist(Y,freq=F,main="Geom from R")

##############################
## Exponential Distribution ##
##############################

N <- 1000
U <- runif(N)
X <- -log(U)
Y <- rexp(N)

par(mfrow=c(1,2))
hist(X,freq=F,main="Exp from Uniform")
hist(Y,freq=F,main="Exp from R")

# Alternatively we can construct an R function as below 

expvar <-function(n=1,rate=1)
 {
   u<-runif(n)
   x<- -log(u)/rate
   return(x)
 }

# The function that computes an iid sample of size n from an exponential distribution with parameter rate. 
# It uses the inverse transformation method. 

```

<img src="https://github.com/christiskatsouris/Introduction-R/blob/main/Data/graph1.png" width="500"/>

## Example 3

```R

function (n)
  {
    x<-c(1:10000)
    for (i in 1:10000)
    {
      x[i]<-sum( runif(n) )
    }
    makelabel<-paste("10000 samples of sum X,with n= ", as.character(n))
    hist(x,prob=TRUE,xlab="X1+X2+...+Xn",ylab="Density",main=makelabel) 
                                         #ylim=c(0.0,1.5)only for the case n=1
    curve( dnorm (x, mean=(n*(1/2)), sd=( sqrt(n/12) ) ) , add=TRUE, col='red' )
 }

```

<img src="https://github.com/christiskatsouris/Introduction-R/blob/main/Data/graph2.png" width="500"/>

### Task

Similar to Example 3, draw random samples from the Exponential distribution and plot the distribution of the sum of i.i.d Exponentially distributed random variables for different sample sizes (e.g., $n = 1,2,4,8)$.

<img src="https://github.com/christiskatsouris/Introduction-R/blob/main/Data/graph3.png" width="500"/>

## Example 4

Write-up the code for an R function that estimates the maximum likelihood estimate for the geometric distribution. HINT: Use a stopping rule by considering the convergence of the computational algorithm. 

```R

fs.geom<- function(theta,avg)
{#begin of function

  if (theta<0 | theta>1) stop ("theta not in [0,1]")
  if (avg<0) stop ("avg must be positive")
 
  maxit   <-100
  epsilon <- 1e-5  

  theta.trace    <- array(NA,maxit+1)
  theta.trace[1] <- theta #store initial estimate

  for (i in 1:maxit)
   {
     theta.old        <- theta
     theta            <- ((1-theta)^2 )*avg + theta^2
     theta.trace[i+1] <- theta
     converge         <- abs(theta-theta.old)/theta.old < epsilon
     if (converge) break
   }

  list (theta=theta, niter=i, theta.trace=theta.trace[1:(1+i)],converge=converge)

}#end of function 

```

# Fitting a Linear Regression Model 

```R

#  Fitting the linear model
> calciummod<-lm(mortality~calcium)
> summary(calciummod)
> par(mfrow=c(2,2))
> plot(calciummod)

# To add the regression line on the plot
> plot(mortality~calcium)
> abline(calciummod$coef)

# The box-cox transformation

> boxcox(lm1)
> lm1<-lm(yield~tissue+pctp,data=RNA)
> lm2<-lm(yield~tissue,data=RNA)
> anova(lm1,lm2)


```

 ### Reference
 
 - Agarwal, Subhashish, et al. "Coronary calcium score and prediction of all-cause mortality in diabetes: the diabetes heart study." Diabetes care 34.5 (2011): 1219-1224.

# Background Statistical Theory

<p align="center">
  
<img src="https://github.com/christiskatsouris/Introduction-R/blob/main/Data/DOA.jpg" width="700"/>

</p>  


# Reading List

- [An Introduction to R](https://intro2r.com/). 
- Crawley, M. J. (2012). [The R book](https://www.wiley.com/en-gb/The+R+Book%2C+2nd+Edition-p-9780470973929). John Wiley & Sons.


# Disclaimer

The author (Christis G. Katsouris) declares no conflicts of interest.

The proposed Course Syllabus is currently under development and has not been officially undergone quality checks. All rights reserved.

Any errors or omissions are the responsibility of the author.

# Historical Background

### Maurice Fréchet

Maurice Fréchet was a French mathematician who made major contributions to the topology of point sets and defined and founded the theory of abstract spaces. Fréchet wrote an outstanding doctoral dissertation Sur quelques points du calcul fonctionnel Ⓣ submitted on 2 April 1906. In it he introduced the concept of a metric space, although he did not invent the name 'metric space' which is due to Hausdorff. The thesis concerns 'functional operations' and 'functional calculus' and is developed from ideas due to Hadamard and Volterra. The importance of the thesis is that it develops axiomatic analysis systems providing an abstraction of different objects studied by analysis in a similar way to group theory providing an abstraction of algebraic systems. This parallel is drawn by Fréchet himself who requires sufficient structure on his abstract systems so that limits and continuity can be studied. He defines a functional operation as a numerically valued function defined on arbitrary objects which he wants to include points, lines, functions, numbers, surfaces etc. The functional calculus of his thesis is then the systematic study of functional operations (see, [MathHistory](https://mathshistory.st-andrews.ac.uk/Biographies/Frechet/)). 

Fréchet, M. (1943). Sur l'extension de certaines évaluations statistiques au cas de petits échantillons. Revue de l'Institut International de Statistique, 182-205.

### Francis Edgeworth

Francis Ysidro Edgeworth (8 February 1845 – 13 February 1926) was an Anglo-Irish philosopher and political economist who made significant contributions to the methods of statistics during the 1880s. In particular, he examined correlation and methods of estimating correlation coefficients in a series of papers (see, [MathHistory](https://mathshistory.st-andrews.ac.uk/Biographies/Edgeworth/)). 
