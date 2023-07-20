# String Unplugged: Python Exercises that Fuse Creativity and Text Manipulation Skills

## TOC
### [Introduction](#intro)
### [Exercise 1: Palindrome Checker](#pr1)
### [Exercise 2: Password Strength Checker](#pr2)
### [Exercise 3: Anagram Finder](#pr3)
### [Exercise 4: Text Encryption/Decryption](#pr4)
### [Exercise 5: URL Parser](#pr5)
### [Exercise 6: Sentence Capitalizer](#pr6)
### [Conclusions](#summ)


<a name="intro"></a>
## Introduction
Dive into the captivating realm of string methods, where the mundane shackles of plain text are shattered, and the extraordinary takes center stage. Brace yourself for a mind-bending journey through the labyrinth of characters, where Python's string methods become your trusted allies in unraveling the mysteries that lie within. 

From unraveling the secrets of slicing and dicing to unleashing the forces of search and replace, these powerful tools will empower you to bend, shape, and transform text to your will. Get ready to embark on an extraordinary adventure where the ordinary becomes extraordinary, and the realm of strings is yours to conquer. 

These exercises will require you to apply various string methods such as strip(), split(), join(), lower(), upper(), replace(), find(), and more. They will help solidify your understanding of string manipulation in Python and provide practical experience with real-world scenarios.

## Exercise One: Palindrome Checker <a name="pr1"></a>
**Problem:** Implement a program that takes a string as input and checks if it is a palindrome (reads the same forwards and backwards). Use string methods to remove whitespace and punctuation, and compare the modified string with its reverse.

Solution:
```python
# imports
import string

def check_palindrome(word):
    # convert the word to lowercase
    word = word.lower()
    
    # remove punctuations
    word = word.translate(str.maketrans("", "", string.punctuation))
    
    # remove whitespaces
    word = word.replace(" ", "")
    
    # Reverse the string using slicing with a step of -1
    return word == word[::-1]

exaample = input("Enter a word: ")
# check_palindrome(exaample)

if check_palindrome(exaample):
    print("Palindrome😍")
else:
    print("Not a palindrome🤣")
```
In this code, the check_palindrome function takes a word as input. It converts the word to lowercase using the lower() method, removes punctuation using the translate() method with str.maketrans(), and removes whitespace using the replace() method. Then, it compares the modified word with its reverse using the slicing technique word[::-1] and returns True if they are equal, indicating that the word is a palindrome.

When you run the code, it prompts you to enter a word. It then checks if the word is a palindrome and prints the result.

## Exercise 2: Password Strength Checker <a name="pr2"></a>
**Problem:** Create a program that prompts the user to enter a password and evaluates its strength. Use string methods to check for various criteria such as length, presence of uppercase and lowercase letters, numbers, and special characters.

**Solution:**

```python
import string

def is_passkey_strong(passkey):
    # checks for strong passkey
    length = len(passkey) >= 8
    uppercase_check = any(key.isupper() for key in passkey)
    lowercase_check = any(key.islower() for key in passkey)
    special_char_check = any(key in string.punctuation for key in passkey)
    number_check = any(key.isdigit() for key in passkey)
    
    # check all the criteria and return the comment
    if (length and uppercase_check and lowercase_check and special_char_check and number_check):
        return True
    elif (length and uppercase_check and lowercase_check and special_char_check):
        return True
    elif (length and uppercase_check and lowercase_check):
        return False
    else:
        return False

# ask for input   

# check passkey strength
while True:
    user_key = input("Kindly create a passkey: ")
    if is_passkey_strong(user_key):
        print("Your 🔐 is 💪")
        break
    else:
        print("Enter a strong 🔐.....")
```
This code demonstrates a program that checks the strength of a user-defined passkey.

The function is_passkey_strong takes a passkey as input and evaluates its strength based on specific criteria. It checks if the passkey meets the following conditions:

- Length: The passkey must be at least 8 characters long.

- Uppercase Check: The passkey must contain at least one uppercase letter.

- Lowercase Check: The passkey must contain at least one lowercase letter.

- Special Character Check: The passkey must contain at least one special character (punctuation mark).

- Number Check: The passkey must contain at least one digit.

If the passkey satisfies all the criteria, the function returns True, indicating that the passkey is strong. Otherwise, it returns False.

The program uses a while loop to repeatedly prompt the user to enter a passkey until a strong passkey is provided. Upon entering a strong passkey, it displays a success message. If the passkey is not strong, it prompts the user to enter a strong passkey again.

The code relies on the string module from the Python standard library to access the punctuation constant, which contains all the punctuation characters.

Overall, this program provides a basic mechanism to enforce strong passkey requirements by checking for various criteria such as length, character types, and the presence of special characters.

## Exercise 3: Anagram Finder<a name="pr3"></a>
**Problem:** Develop a program that takes two strings as input and determines if they are anagrams (contain the same letters but in a different order). Use string methods to remove whitespace and compare the sorted versions of the strings.

**Solution:**

```python
import string

def is_anagram(str1, str2):
    # Remove whitespace from both strings
    str1 = str1.replace(" ", "")
    str2 = str2.replace(" ", "")

    # Remove punctuation from both strings
    str1 = str1.translate(str.maketrans("", "", string.punctuation))
    str2 = str2.translate(str.maketrans("", "", string.punctuation))

    # Convert both strings to lowercase
    str1 = str1.lower()
    str2 = str2.lower()

    # Sort the characters in both strings
    # sorted takes an iterable as input
    # returns a new sorted list containing the elements of the original iterable in ascending order.
    sorted_str1 = sorted(str1)
    sorted_str2 = sorted(str2)

    # Check if the sorted strings are equal
    return sorted_str1 == sorted_str2

# Test the is_anagram function
input_str1 = input("Enter the first string: ")
input_str2 = input("Enter the second string: ")

if is_anagram(input_str1, input_str2):
    print("The strings are anagrams.")
else:
    print("The strings are not anagrams.")

```

## Exercise 4: Text Encryption/Decryption<a name="pr4"></a>
**Problem:** Build a program that encrypts and decrypts text using a simple substitution cipher. Implement string methods to manipulate the text, such as shifting characters, replacing characters, or reversing the string.

**Solution:**

```python
def encrypt(text):
    encrypted_text = ""
    for char in text:
        # Replace characters with their 8-bit binary representation
        # convert the Unicode code point of the character char to its 8-bit binary representation
        binary_representation = format(ord(char), '08b')  # Get the 8-bit binary representation
        encrypted_text += binary_representation + " "

    return encrypted_text.strip()  # Remove trailing whitespace


# Test the encryption and decryption functions
input_text = input("Enter the text: ")

encrypted_text = encrypt(input_text)
print("Encrypted text:", encrypted_text)

```
The code demonstrates a program that encrypts text using a simple substitution cipher.

The encrypt function takes a text as input and performs the following steps:

- 
It initializes an empty string encrypted_text to store the encrypted text.

- 
It iterates over each character in the input text.
For each character, it obtains its Unicode code point using the ord function.

- 
It converts the Unicode code point to its 8-bit binary representation using the format function with the format specifier '08b'. This ensures that each binary representation is 8 bits long.

- 
The resulting binary representation is concatenated to the encrypted_text string, followed by a space.

- 
Finally, the function returns the encrypted text with trailing whitespace removed using the strip method.

The program prompts the user to enter a text, and then the encrypt function is called with the input text. The encrypted text is stored in the encrypted_text variable and printed.

In summary, this program provides a basic encryption mechanism by replacing characters with their 8-bit binary representations.

## Exercise 5: URL Parser<a name="pr5"></a>
**Problem:** Create a program that parses a URL and extracts specific components like the protocol, domain, path, and query parameters. Utilize string methods to extract and manipulate different parts of the URL.

**Solution:**

```python
def parse_url(url):
    # Remove the protocol prefix if present
    if url.startswith("http://"):
        url = url[len("http://"):]
    elif url.startswith("https://"):
        url = url[len("https://"):]

    # Split the URL into domain and path/query parts
    parts = url.split("/", 1)
    domain = parts[0]
    path_query = parts[1] if len(parts) > 1 else ""

    # Split the path/query part into path and query parameters
    parts = path_query.split("?", 1)
    path = parts[0]
    query = parts[1] if len(parts) > 1 else ""

    return {
        "domain": domain,
        "path": path,
        "query": query
    }

# Test the URL parser
input_url = input("Enter the URL: ")

parsed_url = parse_url(input_url)
print("Parsed URL:", parsed_url)

```
The code you provided is a function parse_url() that parses a given URL into its components: domain, path, and query. It removes the protocol prefix (http:// or https://) if present, splits the URL into domain and path/query parts, and then further splits the path/query part into path and query parameters.

To test the URL parser, the code prompts the user to enter a URL and then calls the parse_url() function with the input URL. It prints the parsed URL components: domain, path, and query.

## Exercise 6: Sentence Capitalizer<a name="pr6"></a>
**Problem:** Write a program that takes a paragraph as input and capitalizes the first letter of each sentence. Use string methods to split the paragraph into sentences, capitalize the first letter of each sentence, and join them back together.

**Solution:**

```python
def capitalize_sentences(paragraph):
    sentences = paragraph.split(". ")
    capitalized_sentences = [sentence.capitalize() for sentence in sentences]
    capitalized_paragraph = ". ".join(capitalized_sentences)
    return capitalized_paragraph

# Test the program
input_paragraph = input("Enter the paragraph: ")

capitalized_paragraph = capitalize_sentences(input_paragraph)
print("Capitalized Paragraph:")
print(capitalized_paragraph)
```

The code snippet provided demonstrates a function named capitalize_sentences that capitalizes the first letter of each sentence in a paragraph.

In this function, the paragraph is split into individual sentences using the split(". ") method, assuming that sentences are separated by a period followed by a space. Each sentence is then capitalized using a list comprehension, creating a new list of capitalized sentences.

The capitalized sentences are then joined back together using the join method with ". " as the separator, resulting in a capitalized paragraph. Finally, the capitalized paragraph is returned by the function.

To test the program, the user is prompted to enter a paragraph. The capitalize_sentences function is called with the input paragraph, and the resulting capitalized paragraph is printed.

This program offers a convenient way to capitalize the first letter of each sentence in a paragraph, enhancing readability and adhering to writing conventions.

## Conclusions <a name="summ"></a>
In this collection of projects, we delve into the world of string methods in Python. From checking palindromes, evaluating password strength, and finding anagrams, to parsing URLs, encrypting/decrypting text, and capitalizing sentences, these projects offer a diverse range of challenges. 

Additionally, exploring 8-bit binary representations adds an extra dimension to understanding string manipulation and encoding. Embark on this journey to enhance your understanding of string methods and unleash their power in various real-world scenarios.
