---
layout: page
title: Strings
tagline: Manipulating strings
---
{% include JB/setup %}

Strings are defined as a sequence of characters.  There are three ways to create strings: double quotes, single quotes or the `str()` function.  

>	dessert = "chocolate"
>	topping = 'cherries'
>	str(3.1415)

The function `len()` can be used to calculate the length of a string. 

>	len(dessert)

## String operators
The string operators + and * concatenate and repeat a given string. For example, 

>	'chocolate' + 'cake'
>	'chocolate' * 3

will make  'chocolatecake' and 'chocolatechocolatechocolate'. 

#### Bracket operator
To access a particular character in a string, you can use the bracket operator `[]`. The index must be an integer. In Python, the first character in a string starts at 0 (not 1). For example, the following would return the first character 'c' in the string 'chocolate':

>	dessert[0]

* To extract characters starting from the end of the string, use negative numbers (e.g. dessert[-1] for the last character and dessert[-2] for the second to last character, etc).  
* To extract multiple characters (or a segment), use the bracket operator with a colon (:) also known as a slice operator. For example, use `[m:n]` where m is the position to start and n-1 is the position to end (i.e. the slice operator will extract up to but not include the nth position). If the n is missing, then the characters starting from position m to the end of the string are extracted (similar idea if m is missing). 
* The bracket operator can take in a third argument `[m:n:s]` which is the step size of s between characters. A step size of -1  goes through the word backwards. For example, the following will print 'chocolate' backwards: 

>	dessert[::-1]


#### In operator
If you want to search if one string is a substring of a second string, use the boolean string operator `in`: 

>	`late` in `chocolate`

You can also use the `not in` operator in the opposite way. The `in` operator can be used in conditional statements such as `if` / `else` statements. Here is a function to print all the letters in one word that appear in a second word: 

>	if letter in word: 
>	    print letter

#### Relational operators
The operator == (or `is` ) can be used to test if two strings are equal. The operators <, > can be used to test the alphabetical order of strings. 


## Loop through strings
To traverse through all characters in a given string, you can use `for` or `while` loops. Here we create the names of the duck statues in the Public Gardens in downtown Boston: Jack, Kack, Lack, Mack, Nack, Oack, Pack, Qack. 

>	prefixes = 'JKLMNOPQ'
>	suffix = 'ack'
>	for letter in prefixes:
>	    print letter + suffix

If you want to compare adjacent letters, you may want to use a `while` loop. For example, if you want to determine if a word is a palindrome: 

>	def is_palindrome(word):
>	    i = 0
>	    j = len(word) - 1
>	    
>	    while i < j:
>	        if word[i] != word[j]:
>	            return False
>	        i = i + 1
>	        j = j - 1
>	    
>	    return True

## String methods
There are a set of methods in Python that take in a string and return a value (similar to a function, but different syntax).  The syntax is the name of the string followed by a dot (or period) followed by the name of the method. 

#### List of string methods
* `strip()` = gets rid of the white space in a string
* `upper()` = take in a string and return the string in all upper case letters
* `lower()` = take in a string and return the string in all lower case letters
* `find()` = find all the substrings in a string

For example, if you want to , use the word return all upper case letters, use the `upper()` method.  If you want to find all the 'o''s in a word, use `find()`: 

>	dessert.upper()
>	dessert.find('o')

The `find()` method can also take in a starting position and a stopping position of where it should search, but remember it starts at 0. 

* `split(delimiter)` = splits a string based on a delimiter. If no argument is provided, it splits based on white spaces. If the delimiter is provided as an argument, it will split based on that parameter.

>	"Howdy! How are you today?".split()

The `split(delimiter, num)` method can take an optional second argument which is the number of times to split (useful if you want to search a string for a substring and then work with everything before the substring). 

* `ljust(length)` and `rjust(length)` = pad the string with spaces on the left and ride side with a given length

* `replace('potato', 'tomato')` = searches a string and replaces all the words 'potato' with the word 'tomato'.  


