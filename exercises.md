# String Manipulation

## 0. Warming Up
1. Write a `for` loop that prints each character of the string `"Coding_is_fun!"`

2. Repeat 1, but print replace every occurence of `"_"` with a space `" "`.

  **Hint**: Use an `if` statement inside the `for` loop.

3. Suppose you have two strings:
  ```
  str1 = "abc"
  str2 = "12"
  ```
  Print the concatanetation of each charachter in `str1` with each charachter in `str2`, for example for the given input, it should print:
  ```
  a1
  b1
  c1
  a2
  b2
  c2
  ```
  **Hint**: Use nested `for` loops.

4. Write a `while` loop that prints the characters in a string until an exclamation mark `!` is seen as a character. For example, for the following input

  `"Coding is fun! For now."` 

  It should print:

  `"Coding is fun!"`

5. Repeat 4 using a `break`.


## 1. Alternating Characters

You are given a string containing characters **A** and **B** only. Your task is to change it into a string such that there are no matching adjacent characters. To do this, you are allowed to delete zero or more characters in the string.

Your task is to find the minimum number of required deletions.

**Example**
`s = AABAAB`
Remove an `A` at positions `0` and `3` to make `s = ABAB` in **2** deletions.

**Hint**
It would be useful to have a variable within your loop that stores the previous character, `prev`, and another variable to store the current character, `curr`. This lets you compare the two to see if they alternate. Then you can assign prev to be curr, `prev = curr`.  

## 2. Compare Strings

You are given two strings and you are expected to compare them. You should compare each character in the strings one by one. 

**Example**

Assume you are comparing strings, `s1 = 'abcde'` and `s2 = 'abbcd`, then, you should select the smaller one (appears earlier than the other one in the dictionary). In this case, you should select the second one.

**Explanation:** Assume we are using `i` as an indexing variable, which we will initialize to 0 and increment by one at each comparison we make.

i = 0, s1 and s2's first characters are both `'a'`, in this case, we should look at the following characters.

i = 1, s1 and s2's second characters are both `'b'`, in this case, we should look at the following characters.

i = 2, s1's third character is `'c' and s2's third character is `'b'`. Since `'b'` is smaller than  `'c'` (in python, you can directly compare `'b' < 'c'`), we will select the second string.   

## 3. Merge Strings

You are given two strings and you are expected to merge them into a new string. You should take one element from one string and one element from the other string, and then add them to the new string. You should apply this operation until the strings do not contain any other elements. What happens if the strings are not the same length?

**Example**

`s1 = 'aaaa'` and `s2 = 'bbbb'`, the output should be `'abababab'`.  

## 4. Palindrome Check
Palindromes are words or phrases that are identical forward or backward.  
Write a code piece to check if a string is a palindrome or not in a not-case-sensitive way, ignoring spaces.

**Examples**:   
         `"Madam Im Adam"` -> `"Madam Im Adam is a palindrome"`   
         `"computer"` -> `"computer is not a palindrome"`  
​
## 5. Remove Zeros
​
Given a string consisting of numbers only, write a code piece to remove the leading zeros and trailing zeros after the decimal point.

**Example**: `"00054.2300"` -> `54.23`  
​
## 6. Replace
Given three strings `str_input`, `str1`, and `str2`, write a code piece to replace all the occurrences of `str_1` in `str_input` with `str_2`, if any. There is a function for it called `replace` but do not use it, implement it from scratch.

**Examples**:  
`comp`, `o`, `a` -> `camp`  
`comp`, `t`, `a` -> `comp`  
`autonomous`, `o`, `_` -> `aut_n_m_us`  
​
## 7. Intersection
Given two strings, write a code piece to find the common letters in them according to occurrence order in the first string. 

**Example**: `"introduction"`, `"instuition"` -> `"intou"`

**Hint:** For the case of duplicate common letters, you need to store them only once (when you first find them). e.g. "t" in the above example.  
​
## 8. Duplicate Letters
Given a string, write a code piece that will print any letter in the string that occurs more than once, in the order of repeated occurrence. 

**Example**: `"abccabacb"` -> `"cab"`  
​
## 9. Number of substrings
Given a string, print the total number of substrings that can be contructed out of it.  

**Hint:** Use `len()` function and do not forget about empty string which is a substring of any string.  


# Bisection Search

### 1. Root-finding

In mathematics, [the bisection method](https://en.wikipedia.org/wiki/Bisection_method#Example:_Finding_the_root_of_a_polynomial) can be used for root-finding for any continuous function, i.e. where the function is zero. Initially, we need to define the search region as an interval in which the function changes sign, and therefore must contain a root. This corresponds to finding two values with opposite signs.

For example, for the function

`f(x) = x^3 - x - 2`

these two numbers can be `a = 1` and `b = 2` because `f(1) = -2` and `f(2) = 4`. Because the function is continuous, there must be a root within the interval `[1, 2]`.


For this continuous function `f` and the interval `[a, b]`, we will perform the following steps at each iteration to find the root approximately:

### Part 1: Guess and Check
1. Start from some initial guess `x`. 
2. Increment gradually by some `increment`.
3. Stop when you find an approximate solution within some `epsilon` distance.
4. Count the number of steps and introduce a maximum number of steps to stop execution to avoid an infinite loop.

Experiment with different values of `increment` and `epsilon` to see the trade off between accuracy and run-time. 

### Part 2: Bisection Search

**Please write your solution to `bisection.py` file for this part only and push it to your GitHub repository. **

1. Calculate `c` as the midpoint of the interval, `c = (a+b) / 2` 
2. Calculate the function value at the midpoint, `f(c)`.
3. If convergence is satisfactory (that is, `c - a` is sufficiently small, or `|f(c)|` is sufficiently small), report `c` as the solution and stop iterating.
4. Otherwise, check the sign of `f(c)` and replace either `a` or `b` with `c` so that there is a zero crossing within the new interval. In other words, replace `a` with `c` if `f(c)` is negative, otherwise, replace `b` with `c`.

**Hint**: There can be problems with finite precision, so you might need additional convergence tests or limits to the number of iterations. For this purpose, count the number of iterations and stop when a pre-defined maximum number of iterations is reached, e.g. something like 10000.
