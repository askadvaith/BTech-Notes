# 1. Write a Python program that checks if a given non-negative integer from the user, is a palindrome. A palindrome is a number that remains the same when its digits are reversed. 
For example, 121 is a palindrome because it reads the same forward and backward, whereas 1231 is not a palindrome:

```py
def is_palindrome(number):
    # Convert the integer to a string
    number_str = str(number)
    
    # Compare the string with its reverse
    return number_str == number_str[::-1]

# Get the user input
try:
    user_input = int(input("Enter a non-negative integer: "))
    
    if user_input < 0:
        print("Please enter a non-negative integer.")
    else:
        if is_palindrome(user_input):
            print(f"{user_input} is a palindrome.")
        else:
            print(f"{user_input} is not a palindrome.")
except ValueError:
    print("Invalid input. Please enter a non-negative integer.")
```


# 2. Write a program that takes number of rows ‘n’ as input and prints the following pattern. 
For n=4, it is,
1
121
12321
1234321



```py
n = int(input("Enter the number of rows (n): "))

for i in range(1, n + 1):
    # Print the left part of the pattern (increasing numbers)
    for j in range(1, i + 1):
        print(j, end="")

    # Print the right part of the pattern (decreasing numbers)
    for j in range(i - 1, 0, -1):
        print(j, end="")

    # Move to the next line for the next row
    print()
```



# 3. Write a program that takes number of rows ‘n’ as input and prints the following pattern-
for n=4, it is,
###1
##21
#321
4321


```py
n = int(input("Enter the number of rows (n): "))

for i in range(1, n + 1):
    # Print spaces for alignment
    for j in range(n - i):
        print("#", end="")

    # Print the numbers in decreasing order
    for j in range(i, 0, -1):
        print(j, end="")

    # Move to the next line for the next row
    print()
```

# 4. Write a program that takes number of rows ‘n’ as input and prints the following pattern-
for n=4, it is,
1
10
101
1010

```py
n = int(input("Enter the number of rows (n): "))

for i in range(1, n + 1):
    for j in range(1, i + 1):
        # Print 1 if j is odd, and 0 if j is even
        print(1 if j % 2 == 1 else 0, end="")
    
    # Move to the next line for the next row
    print()
```


# 5. Write a program that takes an integer 'n' as the number of elements to be inserted inside a list. Accept the integer elements for list from the user and an integer 'k' as the desired occurrence frequency from the user. The program should remove all elements that do not occur exactly 'k' times within the list and print the resulting modified list.
Eg: n=7, input_lst=[10,20,20,30,40,10,50], k=2 Output=[20,20,10,10]

```py
n = int(input("Enter the number of elements: "))
input_lst = []

for i in range(n):
    element = int(input(f"Enter element {i + 1}: "))
    input_lst.append(element)

k = int(input("Enter the desired occurrence frequency 'k': "))

element_count = {}
filtered_lst = []

# Count the occurrences of each element in the input list
for element in input_lst:
    if element in element_count:
        element_count[element] += 1
    else:
        element_count[element] = 1

# Filter the elements that occur exactly 'k' times
for element, count in element_count.items():
    if count == k:
        filtered_lst.extend([element] * k)

print("Output =", filtered_lst)
```



# 6. Write a program that takes integer 'n' as the number of elements to be inserted inside a list.
# Accept the integer elements for list, and position 'k' from the user. The program's objective is to find and display the k'th smallest number from the list. It is important to note that the numbers in the list may be repeated, and a simple sorting approach may not yield the correct result. The program should handle this case by considering the frequency of each number.
Eg1:-n=6, lst1=[20,7,15,16,7,8], k=3 output=15
Eg 2:- n=5,lst1=[5,4,19,9,18], k=8 output=None

```py
n = int(input("Enter the number of elements: "))
lst = []

for i in range(n):
    element = int(input(f"Enter element {i + 1}: "))
    lst.append(element)

k = int(input("Enter the value of k: "))

# Create a dictionary to store the frequency of each element
element_count = {}
for element in lst:
    if element in element_count:
        element_count[element] += 1
    else:
        element_count[element] = 1

# Sort the unique elements in ascending order
unique_elements = sorted(set(lst))

# Find the kth smallest element by iterating through the unique elements
count = 0
kth_smallest = None

for element in unique_elements:
    count += element_count[element]
    if count >= k:
        kth_smallest = element
        break

if kth_smallest is not None:
    print(f"The {k}th smallest number is {kth_smallest}")
else:
    print("None")
```


# 7. Write a program that takes integer 'n' as the number of elements to be inserted inside a list, and the integer elements for list from the user. Modify each element of a list by replacing it with the sum of the next two elements. Assume the list is circular, so the last element will be the sum of the elements at index[0] and index[1].
Eg1:-n=4,lst1=[1,2,3,4] output=[5,7,5,3]
Eg2: n=2, lst1=[100,200], output=[300,300]

```py
n = int(input("Enter the number of elements: "))
lst = []

for i in range(n):
    element = int(input(f"Enter element {i + 1}: "))
    lst.append(element)

# Create a new list to store the modified elements
modified_lst = []

for i in range(n):
    # Get the indices of the next two elements in a circular manner
    next_index1 = (i + 1) % n
    next_index2 = (i + 2) % n

    # Calculate the sum of the next two elements
    sum_next_two = lst[next_index1] + lst[next_index2]

    # Append the sum to the modified list
    modified_lst.append(sum_next_two)

print("Output =", modified_lst)
```


# 8. Write a program that accepts a square 2D list (nested list/like matrix) representing a grid of integers from the user and prints the average of the elements along the main diagonal of the 2D list(nested list). 
Eg 1: row_ col= 3, input_lst1=[[1,2,3],[4,5,6],[7,8,9]], output= 5.0 (i.e. (1 + 5 + 9) / 3 =5.0)

```py
# Get the number of rows and columns from the user
n = int(input("Enter the number of rows and columns: "))
input_lst = []

# Initialize a variable to store the sum of diagonal elements
diagonal_sum = 0

# Accept the 2D list from the user
for i in range(n):
    row = []
    for j in range(n):
        element = int(input(f"Enter element at row {i+1}, column {j+1}: "))
        row.append(element)
        # Sum the diagonal elements
        if i == j:
            diagonal_sum += element
    input_lst.append(row)

# Calculate the average of diagonal elements
average_diagonal = diagonal_sum / n

print(f"The average of elements along the main diagonal is {average_diagonal}")
```

# 9. Write a program that accepts a square 2D list (nested list/like matrix) representing a grid of integers from the user and print the transpose of the 2D list(nested list/like matrix). 
Eg 1:- row_col=3 input_lst1= [[1, 5],[2, 7]] Output= [[1, 2],[5, 7]]

```py
# Get the number of rows and columns from the user
n = int(input("Enter the number of rows and columns: "))
input_lst = []

# Accept the 2D list from the user
for i in range(n):
    row = []
    for j in range(n):
        element = int(input(f"Enter element at row {i+1}, column {j+1}: "))
        row.append(element)
    input_lst.append(row)

# Calculate the transpose of the 2D list
transpose_lst = [[input_lst[j][i] for j in range(n)] for i in range(n)]

# Print the transpose
for row in transpose_lst:
    print(row)
```

# 10) Write a program that takes a sentence as input and converts each alphabet in a given sentence to the next letter in the alphabet, while preserving the case of the letters. For example, a is converted to b, b to c, so on and z to a. (ignore punctuations in the input sentence) 
Eg: inp_str=”Welcome to python” output=”Xfmdpnf up qzuipm”


```py
def shift_letter(letter):
    if 'a' <= letter <= 'z':
        # Shift lowercase letter
        return chr(((ord(letter) - ord('a') + 1) % 26) + ord('a'))
    elif 'A' <= letter <= 'Z':
        # Shift uppercase letter
        return chr(((ord(letter) - ord('A') + 1) % 26) + ord('A'))
    else:
        # Return non-alphabet characters as-is
        return letter

inp_str = input("Enter a sentence: ")

# Apply the shift_letter function to each character in the input string
output_str = ''.join([shift_letter(char) for char in inp_str])

print("Output:", output_str)
```



# 11) Write a program to take inputs of different data type as key input and then the value as its data_types name (i.e,. “string”, “integer” or “float”). Store the values in a dictionary with key as input and value as data type. Make a sentence with all the inputs which are of string data type and display the same. 
For example, for the dictionary {"hello":"string", 5:"integer", “world”: “string”} the sentence is "hello world".

```py
data_dict = {}

while True:
    key = input("Enter a key (or 'exit' to finish): ")
    if key == 'exit':
        break

    data_type = input("Enter the data type for the value (string, integer, or float): ")

    if data_type not in ["string", "integer", "float"]:
        print("Invalid data type. Please enter 'string', 'integer', or 'float'.")
        continue

    if data_type == "integer":
        value = int(input(f"Enter the value for '{key}': "))
    elif data_type == "float":
        value = float(input(f"Enter the value for '{key}': "))
    else:
        value = input(f"Enter the value for '{key}': ")

    data_dict[key] = (value, data_type)

sentence = ""
for key in data_dict:
    value, data_type = data_dict[key]
    if data_type == "string":
        sentence += str(value) + " "

print("Sentence with string values:", sentence.strip())
```


# 12) Write a python program that accepts two inputs as word from the user and checks if two words are anagrams of each other. An anagram is a word or phrase formed by rearranging the letters of another.
Eg 1: inp_string 1: anagram inp_string 2: nagaram , Output: True
Eg 2: inp_string 1: baseball, inp_string 2: basketball , Output: False


```py
def are_anagrams(word1, word2):
    word1 = word1.replace(" ", "").lower()
    word2 = word2.replace(" ", "").lower()
    return sorted(word1) == sorted(word2)

inp_string1 = input("Enter the first word: ")
inp_string2 = input("Enter the second word: ")

result = are_anagrams(inp_string1, inp_string2)

print("Output:", result)
```


# 13) Write a program that accepts word as input from the user and translates that word into Pig Latin. In Pig Latin, words are transformed by moving the first letter to the end and adding "ay." 
For example, "hello" becomes "ellohay."


```py
def pig_latin_translation(word):
    if len(word) > 0:
        first_letter = word[0]
        rest_of_word = word[1:]
        pig_latin_word = rest_of_word + first_letter + "ay"
        return pig_latin_word
    else:
        return word

inp_word = input("Enter a word: ")
translated_word = pig_latin_translation(inp_word)

print("Pig Latin Translation:", translated_word)
```


# 14) A cipher is a method of transforming a message to conceal its meaning. The simplest technique involves shifting the letters in the message by a certain number of positions, known as the “shift” or “key”. Given a message and an integer shift value, print the encrypted message. For instance, Encryption - If shift value is 2, A becomes C, B becomes D etc. Z cycles back and becomes B.
Eg1: inp_str=”Hello world” , shift_value=3, Output= Khoor zruog
Eg2: inp_str=” Zero to hero!” , shift_value=1, Output= Afsp up ifsp!

```py
def caesar_cipher_encrypt(message, shift):
    encrypted_message = ""
    
    for char in message:
        if char.isalpha():
            if char.islower():
                shifted_char = chr(((ord(char) - ord('a') + shift) % 26) + ord('a'))
            else:
                shifted_char = chr(((ord(char) - ord('A') + shift) % 26) + ord('A'))
            encrypted_message += shifted_char
        else:
            encrypted_message += char
    
    return encrypted_message

inp_str = input("Enter a message: ")
shift_value = int(input("Enter the shift value: "))

encrypted_message = caesar_cipher_encrypt(inp_str, shift_value)

print("Encrypted Message:", encrypted_message)
```

# 15) Write a Python program that takes a string as input, finds and prints all the unique substrings of the given string in a list in lexicographical order.

```py
def unique_substrings(input_str):
    substrings = set()
    n = len(input_str)

    for i in range(n):
        for j in range(i + 1, n + 1):
            substrings.add(input_str[i:j])

    sorted_substrings = sorted(list(substrings))
    return sorted_substrings

inp_str = input("Enter a string: ")
result = unique_substrings(inp_str)

print("Unique Substrings in Lexicographical Order:")
for substring in result:
    print(substring)
```