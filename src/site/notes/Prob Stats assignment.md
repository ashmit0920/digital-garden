---
{"dg-publish":true,"permalink":"/prob-stats-assignment/"}
---

# Assignment 5
# Q1

P_greater_than_45 = 1 - punif(45,0,60)
P_greater_than_45
P_between_20_and_30 = punif(30,0,60) - punif(20,0,60)
P_between_20_and_30

# Q2

a = dexp(3, rate = 1/2)
val = seq(0, 5, by = 0.01)

b = dexp(val, rate = 1/2)
plot(val, b, xlab="x", ylab="density plot", type="l")

c = pexp(3, rate = 1/2)
val = seq(0, 5, by = 0.01)

d = pexp(val,rate=1/2)
plot(val, d, xlab="x", ylab="cumulative density", type="l")

e = rexp(1000,rate=1/2)
hist(e,breaks=30,probability=TRUE, main="Histogram")
lines(val,b)

# Q3

a = dgamma(3,shape=2,scale=1/3)
b = 1 - pgamma(1,shape=2,scale=1/3)
c = qgamma(0.7,shape=2,scale=1/3)

# Assignment 6

# Q1

f = function(x,y) {
  (2*(2*x+3*y))/5
}

#### checking joint density function
int_result = integral2(f, xmin=0, xmax=1, ymin=0, ymax=1)

#### marginal distribution g(x) at x=1
g=function(y){
 f(1,y)
}

integral(g,0,1)
#### marginal distribution h(y) at y=0
h=function(x){
f(x,0)
}

integral(h,0,1)
#### expected value of g(x,y) = xy
fd = function(x,y){
  f(x,y)*x*y
}

integral2(fd, 0, 1, 0, 1)

# Q2
f = function(x,y) {
  (x+y)/30
}
#### joint mass function
m=matrix(c(f(0,0:2),f(1,0:2),f(2,0:2),f(3,0:2)), 4, 3, byrow=TRUE)

print(m)
sum(m) # checking if its joint mass func

g=apply(m,1,sum) # row-wise, margina dist g(x)
print(g)
h=apply(m,2,sum) # column-wise, marginal dist h(y)
print(h)
e=m[1,2]/h[2] # conditional prob at x=0, y=1
print(e)

x=0:3
y=0:2
e_x = sum(x * g)
e_y = sum(y * h)
e_x2 = sum(x * x * g)
e_y2 = sum(y * y * h)

varx = e_x2-(e_x * e_x)
vary = e_y2-(e_y * e_y)

f2=function(x,y){
  x*y*f(x,y)
}
m2=matrix(c(f2(0,0:2),f2(1,0:2),f2(2,0:2),f2(3,0:2)), 4, 3, byrow=TRUE)
e_xy=sum(m2)
covxy = e_xy - (e_x * e_y)
print(covxy)

# Assignment 7

# Q1 - t-distribution
n <- 100
df <- n - 1
t_values <- rt(n, df)
hist(t_values, main = "Histogram of t-Distribution", xlab = "t-values", col = "skyblue", border = "black")

# Q2 - chi square
n <- 100
df_values <- c(2, 10, 25)

#### Generate data
chi_sq_2 <- rchisq(n, df_values[1])
chi_sq_10 <- rchisq(n, df_values[2])
chi_sq_25 <- rchisq(n, df_values[3])

#### Plot histograms for each
par(mfrow = c(1, 3)) # Divide the plotting area into 1x3
hist(chi_sq_2, main = "Chi-Square (df=2)", xlab = "Values", col = "lightcoral", border = "black")
hist(chi_sq_10, main = "Chi-Square (df=10)", xlab = "Values", col = "lightgreen", border = "black")
hist(chi_sq_25, main = "Chi-Square (df=25)", xlab = "Values", col = "lightblue", border = "black")
par(mfrow = c(1, 1))

# Q3 t-distribution for 100 values in [-6, 6]

x <- seq(-6, 6, length.out = 100)

df_values <- c(1, 4, 10, 30)

density_df1 <- dt(x, df_values[1])
density_df4 <- dt(x, df_values[2])
density_df10 <- dt(x, df_values[3])
density_df30 <- dt(x, df_values[4])

plot(x, density_df30, type = "l", col = "blue", lwd = 2, main = "Student's t-Distribution (Density)", xlab = "x", ylab = "Density")
lines(x, density_df1, col = "red", lwd = 2, lty = 2)
lines(x, density_df4, col = "green", lwd = 2, lty = 3)
lines(x, density_df10, col = "purple", lwd = 2, lty = 4)

legend("topright", legend = c("df=1", "df=4", "df=10", "df=30"), col = c("red", "green", "purple", "blue"), lwd = 2, lty = c(2, 3, 4, 1))

# Q4

v1=10
v2=20

qf(0.95,v1,v2) # 95th percentile of the F-distribution with (10, 20) degrees of freedom
a1 = pf(1.5,v1,v2) # area under the curve for the interval [0, 1.5]
a2 = 1 - a1 # area under curve for [1.5, +inf]

qf(c(0.25,0.50,0.75,0.99),v1,v2) #  calculate the quantile for a given area (= probability) under the curve for a F-curve
#### with v1 = 10 and v2 = 20 that corresponds to q = 0.25, 0.5, 0.75 and 0.99.

rf(1000,v1,v2) # 1000 random values from the F-distribution
hist(random_val, main="Histogram")

# Assignment 8

# Q1

df=read.csv(file.choose())
num_row=nrow(df)
print(num_row)
head(df, 10)
pop_mean=mean(df$Wall.Thickness)
print(pop_mean)
hist(df$Wall.Thickness, main = 'Histogram', xlab = 'Wall Thickness', col = "lightblue")
abline(v = pop_mean, col = "red", lwd = 2)

s10=c()
s50=c()
s500=c()
s9000=c()
n=9000
for(i in 1:n) {
s10[i]=mean(sample(df$Wall.Thickness,10,replace=TRUE))
s50[i]=mean(sample(df$Wall.Thickness,50,replace=TRUE))
s500[i]=mean(sample(df$Wall.Thickness,500,replace=TRUE))
s9000[i]=mean(sample(df$Wall.Thickness,9000,replace=TRUE))
}
hist(s10, col="lightblue")
abline(v=mean(s10), col="red", lwd=2)
par(mfrow=c(1,3))
hist(s50,col="lightblue")
abline(v=mean(s50), col="red", lwd=2)
hist(s500, col="lightblue")
abline(v=mean(s500), col="red", lwd=2)
hist(s9000, col="lightblue")
abline(v=mean(s9000), col="red", lwd=2)

# Q2

age = c(58,69,43,39,63,52,47,31,74,36)
cholesterol = c(189,235,193,177,154,191,213,165,198,181)

plot(age, cholesterol, main="Scatter Plot", col="blue")
model = lm(cholesterol ~ age)
abline(model, color="red")

ch_60 = predict(model, data.frame(age=60))
print(ch_60)

# Q3
#### Scores before and after the course
before <- c(145, 173, 158, 141, 167, 159, 154, 167, 145, 153)
after <- c(155, 167, 156, 149, 168, 162, 158, 169, 157, 161)
#### Perform a paired t-test
t_test_result <- t.test(after, before, paired = TRUE, alternative = "greater", conf.level = 0.95)
#### Display the result
print(t_test_result)