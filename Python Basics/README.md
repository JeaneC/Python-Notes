
# Python Notes - Jeane Carlos

#### Description: These aren't full guides on how to use certain elements in Python, it's more of a way for me to have all the things I use in one place (as opposed to google/stackoverflow everytime). I also link documentation that I found the most useful (or probably just the first one I found) about each matter.


[Markdown Cheat Sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet "Markdown Cheat Sheet")

## Checking for type
> type(object/variable)


## Loops

> [Reference](http://www.pythonforbeginners.com/loops/for-while-and-nested-loops-in-python)
> 

> Loops are ways to iterate through a statement or group of statements. We have three different types of loops for-loops, for-each loops, while loops.


```python
def loops():
    list = [1,2,3,4,5,6]
    x = 0
    
    # These are three diferent loops that accomplish the same thing
    for index in range(0,len(list)):  
        print(list[index])
    for item in list:
        print(item)
    while x<len(list):
        print(list[x])
        x+=1
        
    for _ in range(0,len(list)): #It is common to use _ when you don't actually need a counter
        print("Hello")
        
    for index in range(len(list)): #The start index is defaulted at 0 and not necessary
```

## Lists
> [Documentation](https://docs.python.org/3/tutorial/datastructures.html)
- By lists we usually refer to arrays
- Lists in python can contain multiple variable types
- You can create an empty list like list = [None] * 10, but cases like these a dictionary is more preferable
- You can cast objects to list using list(object)
- Lists can be nested

## Tuples
> Like lists, but you can't modify them.


```python
def lists():
    list = []
    list2 = [1,2,3]
    list.insert(0,5) #insert(index, element)
    list.remove(5) #remove(item) delete the first occurence of item
    list.append(10) #append(item) append item at the end of the list
    list.sort() #sort the list
    list.pop() #pop(index) removes the last element if the index is not given and returns it
    list.reverse() #reverses the order in the list
    list.list(list2) # appends list 2 to the end of list
    list.count(10) # returns the number of occurents of an element
    
    list10 = [1,2,3,4,5]
    list10[-1] # returns last element
    list10[0:3] # returns a list contain the first 3 elements, not including index 3
    list10[:3] # returns a list of elements before index 3 (not including index 3)
    list10[2:] # returns a list of elements starting/including index 2
    
    len(list10)
    sum(list10)
    max(list10)
    min(list10)
    sorted(list10) 
    # list.sort() sorts the list and returns nothing, sorted(list) creates a seperate sorted list and returns that, but the original list is still not sorted
```

## List Comprehensions
> [Video](https://youtu.be/3dt4OGnU5sM)
>

> List comprehensions are designed to read English-like, you can construct an entire loop in one sentence.


- List comprehensions have 3 generic parts
- The first part is what each list element will look like
- The second part is the for loop
- The third part is an optional conditional
- The first and second parts can contain layers of loops inside of it


```python
def lComprehensions():
    x = 2
    y = 2
    z = 2
    n = 5
    l = [[i,j,k] for i in range(0,x+1) for j in range(0,y+1) for k in range(0,z+1) if ((i+j+k) !=n)]
    print(l)
    
    #[i,j,k] is what the list element looks like
    # we have three for loops inside of each other
    # Our last conditional just says to exclude all generated lists where the 
    # sum of x,y,z is equal to n
    
    pow2 = [2 ** x for x in range(10)]
    print(pow2)
            
    # 2 ** x is how each element will look like
    # Next is just one for loop
    # No conditional needed
    
    
    # This code alternates uppercases and lowercases
    s = "i Love chicken WinSa"
    s2 = ''.join([i.lower() if i.isupper() else i.upper() for i in s]) #.join combines a string with a sequence
    print(s2)
```

## Strings

> Strings are a sequence of characters, and as such they have very similar functions to an array


```python
def sMethods():
    s = "Hello"
    b = 'World'
    s = s + " " + b #concatenation between 3 string literals
    print(s)
    s.capitalize()
    s.count("l", 0, len(s)) # count(str, start, end)
    s.find("str",0, len(s)) # returns index if found, otherwise -1
    s.islower() #s.isupper()
    s.lstrip() # remove leading whitespace
    s.rstrip() # removing trailing white space
    s.strip() #lstrip and rstrip
    s.swapcase() # alternates cases in a string
    s.title()
    s.split() #Splits by spaces if no parameter is given
    
    list = ["a", "b", '1']
    "".join(list) #converts a list to string
    
    "-".join(list) # converts a list to a string with elements separated by -
```


```python
def formatting():
    #General Formatting
    '{} {}'.format('one', 'two') #Python 3
    # '%s %s' % ('one', 'two') # Python 2, %s means string

    #Truncating
    '{:.5}'.format('xylophone')
    # '%.5s' % ('xylophone',) # Python 2

    #Check rounding below for NumberFormatting
```

## Hash

___Although important, this part can be skipped___

__Description__: Understanding hashses will explain the logic and implementation behind dictionaries and sets. Hash Tables or "Dictionaries" are arrays with indexing that is determined by a hash function. Since indexing starts at 0 and we are unlikely to need a billion elements, taking the modulo of a hash number results in a smaller range of index values.


> [Great Documentation](http://www.laurentluce.com/posts/python-dictionary-implementation/)
> 

> To _hash_ something is to create an index for an array. The hash() function in Python returns an extremely large integer that is designed to minimize collisions

> A hash collision is where two distinct inputs result in the same output (inputs result in the same index). When a collision happens, hash implementations "probe" or search for a new slot through a process called open addressing. Once a unique slot is found, the key and value pair are stored there.

> The "fix" to avoiding collisions is to create an efficient enough hash function that results in as many unique "keys" as possible.

## Dictionaries

> Arrays require you to access elements by an index. Dictionaries allow you to access elements with string literals as well. Dictionaries work similar to that of a real-life dictionary, there is a word you want to look up, and when you look it up, it has a definition. Like wise, when you feed a dictionary a "key" to look up, it returns its "value"



```python
def dictionary():
    dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}
    print(dict['Name']) #Returns Zara
    dict['Name'] = "Mike" #Changes they "Name" key to have a value of "Mike
    dict['Weight'] = 175 # Since thhe key "Weight" doesnt exist yet, it creates it
    
    # Methods
    del dect['Weight']
    dict.clear()
    dict.items() # Returns a list of tuple key-value pairs
    dict.keys() # Returns a list of the keys
    dict.values() # Returns a list of dictionary values
    
```

## Sets
> Sets are an unordered collection of elements without duplicate entries. Sets are basically dictionaries with no values because they "key" is the "value" in that sense.


```python
def sets():
    x = {3,5,3,5} #{} braces are Python 3 Implementation
    b = set(['a', 'c', 'e', 'H', 'k', 'n', 'r', 'R']) #Python 2 implementation still works
    
    #These operations change the set
    b.add('c') # adds an element, does nothing if it exists
    b.update([1,2,3,4,5]) #like add but for multiple values
    b.remove('c') # removes the element if it exists
    
    # These operations do not change the set, but merely return a set/value
    x.intersection(b) # values that are shared between a and b only]
    x & b # same as above
    x.union(b) # values in a or b
    x | b # same as above
    x.difference(b) # values in a but not in b
    x - b # same as above
    x.symmetric_difference(b) # Returns a list of elements in the set and in the other set/iterable, but not in both. DO NOT CONFUSE WITH INTERSECTION
    x ^ b # same as above
    x.issubset(b) # returns true if x is a subset of b
    
    #These operations are like those above, but they change the set, and do not return anything
    x |= b #same as update above
    x &= b #interesection update, similar to x & b, but instead the set itself is modified
    x -= b #you guessed it
    x ^= b #genius incoming
```

## Other Collections
__Must import collections__

### Counter
> A counter stores elements as dictionary keys and their frequency as the dictionary value.

### Ordered Dictionary
> An OrderedDict remembers the orders the keys were inserted.

### DefaultDict
> Like a regular dictionary but contains it's own key as a key-value

### Dequeues
> Essentialy a double linked list



```python
import collections

def counterExample():
    counter = collections.Counter([1,2,3,4,5,1,3,4])

    for i in range(8):
        if counter[i]: # If the counter exists and is not 0
            counter[i] -=1 #subtract 1 from it
    print(counter)    
```

## Rounding


```python
def rounding():
    print("%.2f" % 10.5555) #.2f represents 2 decimal places
    print("{0:.2f}".format(10.55555))  # Same thing
    print(round(1000.12345,4)) # Rounds to 4 decimal places
```

## Any
> Any() is a convenient method that iterates through each element in the list and returns true if at least one instance of a condition is found

> All() returns true if ALL elements find the condition to be true


```python
def anyTest():
    str = "abc#2151AagoZ"
    
    #These functions naturally only return true if ALL the digits are true
    #Using any, and a for loop, we check for only one instance
    
    print(any(c.isalnum()  for c in str)) # True if at least one is alphanumeric
    print(any(c.isalpha() for c in str)) # True if at least one is alpha
    print(any(c.isdigit() for c in str)) # True if at least one is a digit
    print(any(c.islower() for c in str)) # True if at least one is lower
    print(any(c.isupper() for c in str)) # True if at least one is upper
```

## GetAttr
> [Documentation](https://docs.python.org/3/library/functions.html#getattr)

> GetAttr is a very useful tool in python, especially for interacting with the user. GetAttr takes two parameters, an object and an attribute of that object (function, variable, etc.)

>[Source of Bottom Example](https://www.hackerrank.com/challenges/py-set-discard-remove-pop/forum/comments/197551r) 


```python
def getAttrExample():
    listA = [1,2,3,4,5,6,7,8]
    print(list) # -> [1,2,3,4,5,6,7,8]
    
    command = "insert 1 10" #1 
    method, *args = command.split() #2
    getattr(listA, method) (*(int(x) for x in args)) #3
    
    print(listA) # -> [1, 10, 2, 3, 4, 5, 6, 7, 8]
    
    """
    
    #1 Lets say the user inputs this in text,the user wants to insert 5 at index 1
    
    #2 In python we can neatly do something like a, b = 1, 2. This makes a =1, b = 2. However, 
    we can't really do a, b = 1, 2, 3. Since 3 would have no where to go, we can modify it to 
    a, *b = 1,2,3. This forces b, to take in arguments that are remaining a, *b = 1, 2, 3 would 
    result in -> a = 1, b = [2,3]. In our case, args is = [1,10]
    
    #3 getattr(setA, method) basically writes "setA.method" = setA.insert(). The expression int(x)
    for x in args is a generator expression (like list comprehension) to make elements in args int.
    The asterisk this this time performs the role of "argument unpacking", this converts a sequence
    into function arguments. So our sequence was a list [1,10] becomes arguments to a function as
    (1,10).
    
    All in all 3 does, setA.insert(1,10)
    
    """
```

## Map


```python
def mapExample():
    userInput = "1 2 3 4 5 6 7 8 9 10"
    s = userInput.split() # s = ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10']
    print(s)
    
    try:
        print(sum(s))
    except:
        print("Can't take sum of strings/chars") #Because s is a list of characters

    s = list(map(int,s)) #All the characters are now integers, [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    print(sum(s)) # - > 55
```

## Itertools
> A set of functions for working with iterable data sets ([source](https://pymotw.com/2/itertools/))


```python
def itertools():
    import itertools
    
    a = [1,2,3,4,5]
    b = [7,8,9,10,11]
    
    itertools.product(a,b) # Returns an itertools object (not easily readable)
    list(itertools.product(a,b)) # Returns a list (easily readable)
    
    itertools.permutations(a,2) # Returns all possible 2 ordered tuple permutations
    itertools.combinations(a,2) # Returns all possible 2 ordered combinations
    
```

## Calendar
> https://docs.python.org/2/library/calendar.html#calendar.TextCalendar

## Zip
> zip(\*seq) - takes in 1 or multiple sequence arguements and returns a list of tuples matching each index of one sequence to another


```python

```
