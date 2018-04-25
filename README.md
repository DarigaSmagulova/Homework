# Homework
#Exercises 5,6,9

#The prime factors of 13195 are 5, 7, 13 and 29. What is the largest prime factor of the number 600851475143 ?

import math
n=int(input('Num is '))
all_divisors=[]
prime_factors=[]
is_prime=True
for i in range(2,int(math.sqrt(n)+1)):
    if n%i==0:
        all_divisors.append(i)

for num in all_divisors:
    is_prime=True
    for divisors in range(2,num):
        if num%divisors==0:
            is_prime=False

    if is_prime:
        prime_factors.append(num)


print('Largest prime factor is ',prime_factors[-1])
