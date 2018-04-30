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



#Write a program that outputs all possibilities to put+or-or nothing between the numbers 1,2,...,9
# (in this order)
# such that the result is 100. For example 1 + 2 + 3 - 4 + 5 + 6 + 78 + 9 = 100.

def calculateSum(array):
    sum=0
    num=1
    sign=1
    for k in range(0,8):
        if array[k]==0:
            num=num*10+k+2 # k+2 num
        else:
            if sign==2: # look to l
                sum-=num
            else:
                sum+=num
            sign=array[k]
            num=k+2
    if sign==2:
        sum-=num
    else:
        sum+=num
    return sum





def solve(i,array):

    if i==8 :
        if calculateSum(array) == 100:
            print(1,end='')
            for k in range(0,8):
                if array[k]==1:
                    print(' + ',end='')
                if array[k]==2:
                    print(' - ',end='')
                print(k+2,end='')
            print()
    else:
        for l in range(0,3):     #000 001 012 etc
            array[i-1]=l
            solve(i+1,array)

array=[]
for n in range(0,8):
    array.append(0)
solve(0,array)




