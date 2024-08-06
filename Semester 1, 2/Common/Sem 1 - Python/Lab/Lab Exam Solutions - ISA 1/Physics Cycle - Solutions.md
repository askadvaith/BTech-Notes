# WAP to accept a set of integers from the user as a matrix and calculate sum of both diagonals
```py
n = int(input())
#initializing the matrix
matrix = []
#diagonal values
primary_diagonal = 0
secondary_diagonal = 0
#accepting the values
for i in range(n):
    l =[] #three mini lists are formed
    for j in range(n):#same number of elements in row and columns
        m=int(input())
        l.append(m)
    matrix.append(l)#nesting the lists
for i in range(n):
    primary_diagonal += matrix[i][i]
    secondary_diagonal += matrix[i][n-i-1]#indexing the second bracket as indexes start from 0 (first loop index at 0)
print(primary_diagonal)
print(secondary_diagonal)
```

# Write a program that takes the number of rows 'n' as input from the user and prints a number pattern in increasing order as shown below. 
```
If n is 5, the expected pattern is:
1
2 3
4 5 6
11 8 9 10
11 12 13 14 15
```
```py
n = int(input("Enter the number of rows (n): "))


current_number = 1
for i in range(1, n + 1):
    for j in range(i):
        print(current_number, end=" ")
        current_number += 1
    print()
```

# Write a program that takes the number of rows 'n' as input from the user and prints a diamond pattern using asterisks (*) as shown in the sample example. Note that input ‘n’ will be an odd integer. The pattern should have a diamond shape with 'n' rows in the middle.
```
If n is 5, the expected pattern is:
   *
  ***
 *****
  ***
   *
```
```py
n=int(input("Enter number of rows"))
if n%2==0:
    print("Enter an odd number please")
else:
    for i in range(1,n+1):
        spaces = abs(n//2-i+1)
        stars = n-2*spaces
        print(" "*spaces + "*"*stars)
```

# Write a program that accepts a square 2D list (nested list/like matrix) representing a grid of integers from the user. Find and print the minimum value in the entire matrix along with its row and column indices.
```py
n = int(input())
max = -10000000000000000000000000000000000000000000000000000000
min = 100000000000000000000000000000000000000000000000000000000
Max_R = 0
Max_C = 0
Min_R = 0
Min_C = 0
matrix=[]
for i in range(n):
    l = []
    for j in range(n):
         x = int(input())
         l.append(x)
         if (x>max):
            max = x
            Max_C = j
            Max_R = i
         if (x<min):
            min = x
            Min_C = j
            Min_R = i
    matrix.append(l)
for i in range(n):
    print(matrix[i])
print(min,Min_C+1,Min_R+1,max,Max_C+1,Max_R+1)
```

# Write a program that takes an integer ‘n’ as the number of elements and an integer ‘k’ as the desired occurrence frequency from the user. The program should remove all elements that occur exactly k times from the list and print the modified list. Both ‘n’ and ‘k’ are positive integers and k <= n.
Eg: n=7, input_lst=[10,20,20,30,40,10,50], k=2. Output=[30,40,50]
```py
a = [10,20,20,30,40,50]
b = []
K = 2
for i in a :
    if (a.count(i)!=k):
        b.append(i)
```

# Write a program that takes a string ‘test_str’ and a substring ‘sub_str’ as inputs from the user. Find the sub_str that occurs the most in a list of words formed by splitting test_str into words.
For example, if the test_str string is "This is a test string testtest" and sub_str is "test". Then the output would be "testtest" as the sub_str has been repeated twice.
```py
# Input the main string
test_str = input("Enter the main string: ")
# Input the substring to search for
sub_str = input("Enter the substring to find: ")


# Split the test_str into words
words = test_str.split()


# Initialize variables to keep track of the most frequent substring
most_frequent_substring = ""
max_count = 0


# Iterate through the words to count occurrences of sub_str
for word in words:
    count = word.count(sub_str)
    if count > max_count:
        most_frequent_substring = word
        max_count = count


if most_frequent_substring:
    print("The most frequent substring is:", most_frequent_substring)
else:
    print("The substring was not found in any of the words.")
```

# Write a Python program that takes two strings as inputs from the user and checks if one string is a rotation of another string. 
For example, "waterbottle" is a rotation of "erbottlewat". Your program should print 'Y' if one string is a rotation of the other, and 'N' if it is not.
```py
# Input two strings from the user
str1 = input("Enter the first string: ")
str2 = input("Enter the second string: ")


# Check if the lengths of both strings are the same and not empty
if len(str1) != len(str2) or len(str1) == 0:
    print("N")
else:
    # Double the first string and check if the second string is a substring of the doubled string
    doubled_str1 = str1 + str1
    if str2 in doubled_str1:
        print("Y")
    else:
        print("N")
```

# Write a Python program that takes a string as input and then finds and prints all the unique substrings of the given string in a list in lexicographical order.
```py
s=input()
l=[]
for i in range(len(s)):
    for j in range(i+1,len(s)+1):
        if s[i:j] not in l:
            l.append(s[i:j])
l.sort()
print(l)
```

# Write a Python program that takes two strings as inputs from the user and checks if one string is an anagram of the other string.Your program should print 'Y' if one string is an anagram of the other, and 'N' if it is not. An anagram is a word or phrase formed by rearranging the letters of another word or phrase, using all the original letters exactly once. 
For instance, if the first string is "listen" and the second string is "silent", the program should print ‘Y’. Another example for anagram is "race" and "care" and thus the program should print ‘Y’ for this input as well.
```py
# Input two strings from the user
str1 = input("Enter the first string: ")
str2 = input("Enter the second string: ")


# Remove spaces and convert both strings to lowercase for case-insensitive comparison
str1 = str1.replace(" ", "").lower()
str2 = str2.replace(" ", "").lower()


# Check if both strings are anagrams of each other
if sorted(str1) == sorted(str2):
    print("Y")
else:
    print("N")
```

# Write a Python program that calculates the sum of numerical values assigned to each letter in a given string, where 'a' is assigned the value 1, 'b' is assigned the value 2, and 'z' is assigned the value 26. 
For instance, if the input string is "hello," the program should calculate the sum as follows: 'h' (8) + 'e' (5) + 'l' (12) + 'l' (12) + 'o' (15) for a total sum of 52. The program should then display the calculated sum as the result.
```py
# Input a string from the user
input_str = input("Enter a string: ")


# Convert the input string to lowercase for case-insensitive calculation
input_str = input_str.lower()


# Initialize a variable to store the sum
total_sum = 0


# Iterate through the characters in the string
for char in input_str:
    if 'a' <= char <= 'z':
        # Calculate the numerical value for the character and add it to the total sum
        value = ord(char) - ord('a') + 1
        total_sum += value


# Display the calculated sum
print("The sum of numerical values for the characters is:", total_sum)
```

# Write a program that takes a sentence as input from the user and converts each alphabet in a given sentence to the next letter in the alphabet, while preserving the case of the letters and prints it. For example, a is converted to b, b to c, so on and z to a.
For example, if the input is “Hello, World”, the expected output is “Ifmmp, Xpsme”.
```py
lower="abcdefghijklmnopqrstuvwyz"
upper="ABCDEFGHIJKLMNOPQRSTUVWXYZ"

s=input("Enter a sentence: ")
ns=""
for i in s:
    if i in lower:
        for d in range(len(lower)):
            if lower[d]==i:
                if i=="z":
                    ns+="a"
                else:
                    ns+=lower[d+1]
    elif i in upper:
        for d1 in range(len(upper)):
            if upper[d1]==i:
                if i=="Z":
                    ns+="A"
                else:
                    ns+=upper[d1+1]
    else:
        ns+=i
print(ns)
```
