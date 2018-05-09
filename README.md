# Homework
#Exercises 5,6,9

#The prime factors of 13195 are 5, 7, 13 and 29. What is the largest prime factor of the number 600851475143 ?

import math
def largest_prime_factor():
    n=int(input('Number is '))
    all_divisors=[]
    prime_factors=[]
    for i in range(2,int(math.sqrt(n)+1)):
        if n%i==0:
            all_divisors.append(i)
    if all_divisors==[]:
        return n
    else:

        for num in all_divisors:
            is_prime=True
            for divisors in range(2,num):
                if num%divisors==0:
                    is_prime=False

            if is_prime:
                prime_factors.append(num)
    return prime_factors[-1]


print('The largest prime factor is ',largest_prime_factor())



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


#Translator Morse-English 
CODE = {' ': '_',	"'": '.----.',	'(': '-.--.-',	')': '-.--.-',	',': '--..--',	'-': '-....-',	'.': '.-.-.-',	'/': '-..-.',
	'0': '-----',	'1': '.----',	'2': '..---',	'3': '...--',	'4': '....-',	'5': '.....',	'6': '-....',	'7': '--...',
	'8': '---..',	'9': '----.',	':': '---...',	';': '-.-.-.',	'?': '..--..',	'A': '.-',	'B': '-...',	'C': '-.-.',
	'D': '-..',	'E': '.',	'F': '..-.',	'G': '--.',	'H': '....',	'I': '..',	'J': '.---',	'K': '-.-',	'L': '.-..',
	'M': '--',	'N': '-.',	'O': '---',	'P': '.--.',	'Q': '--.-',	'R': '.-.',	'S': '...',	'T': '-',	'U': '..-',
	'V': '...-',	'W': '.--',	'X': '-..-',	'Y': '-.--',	'Z': '--..',	'_': '..--.-', '':' '}

inverseMorseAlphabet = {v: k for k, v in CODE.items()}

def convertToMorseCode(sentence):
    sentence = sentence.upper()
    englishcodedSentence = ""
    for character in sentence:
        englishcodedSentence += CODE[character] + " "
    return englishcodedSentence


def convertToEnglish(sentence1):
    b = sentence1.split(' ')
    MorsecodedSentence1 = ""
    for character in range(len(b)):
        MorsecodedSentence1 += inverseMorseAlphabet[b[character]]
    return MorsecodedSentence1

choice=input("Choose language:Text or morse: ")


if choice == "text":
    given_sentence = input("enter text code: ")
    print(convertToMorseCode(given_sentence))


elif choice == "morse":
    given_sentence = input("enter morse code: ")
    print(convertToEnglish(given_sentence))




