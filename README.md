# Experiment-2-Fitting-Poisson-Distribution
Aim: 
To fit Poisson distribution for the arrival of objects per minute from the feeder. 
# Software required: 

Python and Visual Component Tool
# Theory: 

1. The Poisson distribution gives the probability of a number of events occurring in a fixed interval of time or space when events occur independently and at a constant average rate (λ).
2. The probability mass function (PMF) is:  
<img width="1171" height="73" alt="image" src="https://github.com/user-attachments/assets/e28da9e9-3b3f-4969-baa9-2ff06c3358ba" />
3. Here, λ = mean number of occurrences, and e = 2.718 (base of natural logarithm).
4. The mean and variance of a Poisson distribution are both equal to λ.
5. Applicable when events occur independently, singly, and at a constant rate.
# Algorithm
<img width="1144" height="412" alt="image" src="https://github.com/user-attachments/assets/6bf357bd-7ba2-4908-8c93-ef74e4747a4f" />

# Program
Name: sriharikumar.k

Reg_No: 25018036

Slot_Name: 3P1-1

Date: 16-11-2025

Program: 
import numpy as np 
import math 
import scipy.stats 
 
L = [int(i) for i in input().split()] 
N = len(L) 
M = max(L) 
X = list() 
f = list() 
 
for i in range(M + 1): 
    c = 0 
    for j in range(N): 
        if L[j] == i: 
            c = c + 1 
    f.append(c) 
    X.append(i) 
 
sf = np.sum(f) 
p = list() 
 
for i in range(M + 1): 
    p.append(f[i] / sf) 
 
mean = np.inner(X, p) 
 
p = list() 
E = list() 
xi = list() 
 
print("X   P(X=x)   Obs.Fr   Exp.Fr   xi") 
print("-------------------------------") 
 
for x in range(M + 1): 
    p.append(math.exp(-mean) * mean**x / math.factorial(x)) 
    E.append(p[x] * sf) 
    xi.append(((f[x] - E[x])**2) / E[x]) 
    print("%2d   %.3f   %4d   %.2f   %.3f" % (x, p[x], f[x], E[x], xi[x])) 
 
print("-------------------------------") 
 
cal_chi2_sq = np.sum(xi) 
print("Calculated value of Chi square is %.4f" % cal_chi2_sq) 
 
table_chi2 = scipy.stats.chi2.ppf(1 - 0.01, df=M) 
print(f"Table value of Chi square at 1% level is {table_chi2:.4f}") 
 
if cal_chi2_sq < table_chi2: 
    print("The given data can be fitted in Poisson Distribution at 1% LOS") 
else: 
    print("The given data cannot be fitted in Poisson Distribution at 1% LOS")

Google_Colab-link:

https://colab.research.google.com/drive/1BkVHW9HNtn8Um_IOlSXhf5RyusfrEyVw?usp=sharing

# Output

<img width="737" height="409" alt="Screenshot 2025-11-16 222556" src="https://github.com/user-attachments/assets/4a6f67c4-7378-4669-92b3-f3bfaa3ed29b" />


# Result
The Poisson Distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test. 

