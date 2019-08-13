
## Data Structure

#### 19. List the basic data types in Python


```python
# int
print(type(1))

# float
print(type(1.0))

# complex
print(type(1+2j))

# string
print(type('hello'))

# boolean
print(type(True))

# list
print(type([1,2,3]))

# tuple
print(type((1,2,3)))

# dict
print(type({'a':1}))

#set
print(type(set([1,2,3])))
```

    <class 'int'>
    <class 'float'>
    <class 'complex'>
    <class 'str'>
    <class 'bool'>
    <class 'list'>
    <class 'tuple'>
    <class 'dict'>
    <class 'set'>
    

#### 20. Mutable vs Immutable data types in Python

<img src="https://miro.medium.com/max/658/1*uFlTNY4W3czywyU18zxl8w.png">

#### 21. Convert "hello world" to capitalized "Hello World"

There is a built-in method to do this:
https://docs.python.org/3/library/stdtypes.html#str.title


```python
"hello world".title()
```




    'Hello World'



However, as is mentioned in the docs, there is some problem:
> The algorithm uses a simple language-independent definition of a word as groups of consecutive letters. The definition works in many contexts but it means that apostrophes in contractions and possessives form word boundaries, which may not be the desired result:


```python
sentence = "they're bill's friends from the UK"
sentence.title()
```




    "They'Re Bill'S Friends From The Uk"



There is a ***capwords()*** function in ***string*** Python standard library to do a better work:  
https://docs.python.org/3.2/library/string.html#string.capwords


```python
import string
string.capwords(sentence)
```




    "They're Bill's Friends From The Uk"



However, this is still not perfect since the all-upper 'UK' is transformed into capitalized 'Uk', which is because that the ***string.capwords()*** function uses ***str.capitalize()*** method to do the capitalization (first upper, rest lower).  
https://docs.python.org/3.2/library/stdtypes.html#str.capitalize  
I haven't found any built-in solution to do the conversion in a "first upper, rest remained" pattern, but if you really want, you can write your own:


```python
def cap(string):
    words_list = string.split(' ')
    new_words_list = []
    for word in words_list:
        new_word = word[0].upper() + word[1:]
        new_words_list.append(new_word)
    return ' '.join(new_words_list)

cap(sentence)
```




    "They're Bill's Friends From The UK"



Of course you can do this with a one-line list comprehension, which is quicker to write but harder to read:


```python
' '. join([word[0].upper() + word[1:] for word in sentence.split(' ')])
```




    "They're Bill's Friends From The UK"




```python

```
