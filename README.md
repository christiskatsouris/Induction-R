# Induction-R
Teaching page

# Operations in R

```R

height <- 1.81
weight <- 75
age    <- 26
job    <- "Researcher"

#####################
# Generating Sequences
#####################

rep(c(1:4),3)
rep(c(1:4), times = 3)
rep(c(1:4), each = 3)

seq(from = 1, to = 4, by = 1)
seq(4,19,3)

#####################
# Generating Matrices
#####################

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

#####################
# Generating Vectors 
#####################

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

# Descriptive Data Analysis
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
# Conditional Execution:
########################

A <- -2
if( A <0 ) { Abs.A <- (-1)*A }
Abs.A

A <- 1
B <- 2
if((A>2) || (B>2)) { C <- 1 } else { C <- 0 }

```

# Installing R packages 

```R

install.packages( "insuranceData" )
library( insuranceData )
data( AutoClaims )
head( AutoClaims )

age_variable    <- AutoClaims$AGE 
claims_variable <- AutoClaims$PAID

hist( claims_variable )

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


# Distribution Theory

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

```
