---
title:  "<13> 노마드 코드 python challenge을 진행하면서 새로 배운 문법들"
excerpt: "args, kwargs, sorted, continue etc"

categories:
  - python scrapper
tags:
  - 
  - 
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.  
> 2. 각 개념에 따른 코드 정리.  


# 새로배운 파이썬 문법들

나름 정리 해 보았다.

```python
########### += ###########

my_list=["banana","ball", "banana", "cat", "hat"] 
my_dict = dict()

for word in my_list:
    if word in my_dict.keys():
        my_dict[word] += 1 # plus one to the value of oneself
    else:
        my_dict[word] = 1
      
print(my_dict)

x = len(my_dict.values())

print(x)

y = list(my_dict.keys())

print(y)


############ BIBLE DICTIONARY ############
# Dict List for bible
BIBLE_BOOKS_LIST_DICT = [
("Genesis"), ("Exodus"), ("Leviticus"),
("Numbers"), ("Deuteronomy"), ("Joshua"),
("Judges"), ("1 Samuel"), ("2 Samuel"),
("1 Kings"), ("2 Kings"), ("1 Chronicles"),
("2 Chronicles"), ("Ezra"), ("Nehemiah"),
("Esther"), ("Job"), ("Psalms"), ("Proverbs"),
("Ecclesiastes"), ("Song of Solomon"),
("Isaiah"), ("Jeremiah"), ("Lamentations"),
("Ezekiel"), ("Daniel"), ("Hosea"), ("Joel"),
("Amos"), ("Obadiah"), ("Jonah"), ("Micah"),
("Nahum"), ("Habakkuk"), ("Zephaniah"),
("Haggai"), ("Zechariah"), ("Malachi"),
("Matthew"), ("Mark"), ("Luke"), ("John"),
("Acts"), ("Romans"), ("1 Corinthians"),
("2 Corinthians"), ("Galatians"), ("Ephesians"),
("Philippians"), ("Colossians"), ("1 Thessalonians"),
("2 Thessalonians"), ("1 Timothy"), ("2 Timothy"),
("Titus"), ("Philemon"), ("Hebrews"), ("James"),
("1 Peter"), ("2 Peter"), ("1 John"), ("2 John"),
("3 John"), ("Jude"), ("Revelation")
]

# Dict for bible categories
BIBLE_BOOKS_DICT = {
'The Law':BIBLE_BOOKS_LIST_DICT[:5],
'OT History':BIBLE_BOOKS_LIST_DICT[5:16],
'Poetry':BIBLE_BOOKS_LIST_DICT[16:21],
'Major Prophets':BIBLE_BOOKS_LIST_DICT[21:26],
'Minor Prophets':BIBLE_BOOKS_LIST_DICT[26:38],
'Gospels':BIBLE_BOOKS_LIST_DICT[38:42],
'NT History':BIBLE_BOOKS_LIST_DICT[42:43],
'Pauline Epistles':BIBLE_BOOKS_LIST_DICT[43:52],
'Pastoral Letters':BIBLE_BOOKS_LIST_DICT[52:55],
'General Epistles':BIBLE_BOOKS_LIST_DICT[55:64],
'Prophecy':BIBLE_BOOKS_LIST_DICT[64:65]
}

for key, value in BIBLE_BOOKS_DICT.items():
    if "Matthew" in value:
        print(key)

########### What is default arguments in python?###########
# Python has a different way of representing syntax and default values for function arguments. 
# Default values indicate that the function argument will take that value if no argument value is passed during function call. The default value is assigned by using assignment (=) operator. Below is a typical syntax for default argument. 
# Here, foo parameter has a default value Hi!



########## Visualizing! ##########
# always make a brief sequence of logic with words.
# ​
# visualize it!
# ​
# make it much more clear and easier to code. 


########## split ############
txt = "apple#banana#cherry#orange"

# setting the maxsplit parameter to 1, will return a list with 2 elements!
x = txt.split("#", 3)

print(x)


########## strip and replace ############
##1. get rid of word
txt = ",  h,,..rrttgg.,h..banana..,.rrr"

x = txt.rstrip(" ,rtg")

print(x)

##2. get rid of mulitiple words using replace

string.replace("condition1", "").replace("condition2", "text")

##3. get rid of multiple words using func with replace

a_string = "breads"
remove_characters = ["e", "s"]

for character in remove_characters:
    a_string = a_string.replace(character, "")

# replace character with an empty string

print(a_string)


########## while/break/continue ##########


while True:
    s = input('Enter something : ')
    if s == 'quit':
        break
    print('Length of the string is', len(s))
print('Done')


while True:
    s = input('Enter something : ')
    if s == 'quit':
        break
    if len(s) < 3:
        print('Too small')
        continue
    print('Input is of sufficient length')
    # Do other kinds of processing here...

#break, continue must be in for or while loop.

########## while/try/if/break ##########


while True:        
    try:
        age = int(input("Enter your age: "))
        if age > 0:
            break
        print("Invalid age entered")
    except Exception as e:
        print(e)



########## *args ##########

def my_function(*kids):
  print("The youngest child is " + kids[2])

my_function("Emil", "Tobias", "Linus")

#>>The youngest child is Linus



########## **kwargs ##########

def my_function(**kid):
  print("His last name is " + kid["lname"])

my_function(fname = "Tobias", lname = "Refsnes")
#>>His last name is Refsnes

########## itemgetter  ##########

from operator import itemgetter 
a = [-2, 1, 5, 3, 8, 5, 6]
b = [1, 2, 5]
print(itemgetter(*b)(a))
# Result:
(1, 5, 5)


########## chose elements at even position ##########

L = [1, 2, 3, 4, 5, 6, 7]
li = []
for i in L[1::2]:
    print(i)

# >>> 2, 4, 6 
# >>> because: some_list[start:stop:step]

########## sort dictionary by certain key ##########

from operator import itemgetter 

# Initializing list of dictionaries 
lis = [{ "name" : "Nandini", "age" : 20}, 
{ "name" : "Manjeet", "age" : 20 }, 
{ "name" : "hikhil" , "age" : 15 },
{ "name" : "sikhil" , "age" : 1135 },
{ "name" : "aikhil" , "age" : 134 },
{ "name" : "ktyikhil" , "age" : 126 },
{ "name" : "eqikhil" , "age" : 13 },
{ "name" : "cikhil" , "age" : 1754 }
] 

# using sorted and itemgetter to print list sorted by age 
print "The list printed sorting by age: "
print sorted(lis, key=itemgetter('age')) 

print ("\r") 

# using sorted and itemgetter to print list sorted by both age and name 
# notice that "Manjeet" now comes before "Nandini" 
print "The list printed sorting by age and name: "
print sorted(lis, key=itemgetter('age', 'name')) 

print ("\r") 

# using sorted and itemgetter to print list sorted by age in descending order 
print "The list printed sorting by age in descending order: "
print sorted(lis, key=itemgetter('age','name'),reverse = True)

>>>
# The list printed sorting by age: 
# [{'age': 13, 'name': 'eqikhil'}, {'age': 15, 'name': 'hikhil'}, {'age': 20, 'name': 'Nandini'}, {'age': 20, 'name': 'Manjeet'}, {'age': 126, 'name': 'ktyikhil'}, {'age': 134, 'name': 'aikhil'}, {'age': 1135, 'name': 'sikhil'}, {'age': 1754, 'name': 'cikhil'}]

# The list printed sorting by age and name: 
# [{'age': 13, 'name': 'eqikhil'}, {'age': 15, 'name': 'hikhil'}, {'age': 20, 'name': 'Manjeet'}, {'age': 20, 'name': 'Nandini'}, {'age': 126, 'name': 'ktyikhil'}, {'age': 134, 'name': 'aikhil'}, {'age': 1135, 'name': 'sikhil'}, {'age': 1754, 'name': 'cikhil'}]

# The list printed sorting by age in descending order: 
# [{'age': 1754, 'name': 'cikhil'}, {'age': 1135, 'name': 'sikhil'}, {'age': 134, 'name': 'aikhil'}, {'age': 126, 'name': 'ktyikhil'}, {'age': 20, 'name': 'Nandini'}, {'age': 20, 'name': 'Manjeet'}, {'age': 15, 'name': 'hikhil'}, {'age': 13, 'name': 'eqikhil'}]
```


