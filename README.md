Turkey
======
STATA
*Question 1

reg ahe age
dis _b[_cons]
dis _b[age]

*Earnings increase by approx. .605 as worker age increases by 1 yr

*Question 2

sca Bob = _b[age]*26 + _b[_cons]
sca Alexis = _b[age]*30 + _b[_cons]
dis Bob
dis Alexis

*Question 3

*Interpretation

*Question 4

reg ahe age if bachelor == 0
dis _b[_cons]
dis _b[age]

*Question 5

*Interpretation

*Question 6

reg ahe age female bachelor
dis _b[age]

*Question 7

*Interpretation

*Question 8

sca Bob2 = _b[age]*26 + _b[_cons]
sca Alexis2 = _b[age]*26 + _b[_cons] + _b[bachelor] + _b[female]
dis Bob2
dis Alexis2

*Question 9

*Interpretation

*Question 10
graph twoway (lfit ahe age) (scatter ahe age)
graph rename Figure_1

*Question 11

gen hello = log(ahe)
reg hello age female bachelor
sca earningsone = _b[age]*26 - _b[age]*25
sca earningstwo = _b[age]*34 - _b[age]*33
dis earningsone
dis earningstwo

*Question 12

gen goodbye = log(ahe)
gen agesqr = age^2
reg goodbye age agesqr female bachelor

sca earningsthree = _b[age]*26 - _b[age]*25
sca earningsfour = _b[age]*34 - _b[age]*33
dis earningsthree
dis earningsfour

clear
exit

PYTHON

MAKE A DICTIONARY
def makeDictionary(key, value):
    dict = {}
    for i in range(len(key)):
        dict[key[i]]=value[i]
    return dict

names = ['joe','tom','barb','sue','sally']
scores = [10,23,13,18,12]

scoreDict = makeDictionary(names, scores)

STANDARD DEVIATION
import math
def standardDev(alist):
  theMean = mean(alist)
  
  sum = 0
  for item in alist:
    difference = item - theMean
    diffsq = difference ** 2
    sum = sum + diffsq
  
  sdev = math.sqrt(sum/(len(alist)-1))
  return sdev
  
  FREQUENCY TABLE
  def frequencyTable(alist):
    countdict = {}
    
    for item in alist:
      if item in alist:
        countdict[item] = countdict[item] + 1
      else:
        countdict[item] = 1
    
    itemlist = list(countdict.keys())
    itemlist.sort()
    
    print("ITEM","FREQUENCY")
    
    for item in itemlist:
      print(item,"     ",countdict[item])

MODE
def mode(alist):
  countdict = {}
  
  for item in alist:
    if item in countdict:
      countdict[item] = countdict[item] + 1
    else:
      countdict[item] = 1
  
  countlist = countdict.values()
  maxcount = max(countlist)
  
  modelist = []
  for item in countdict:
    if countdict[item] == maxcount:
        modelist.append(item)
  
  return modelist
  
KEYS
adict.keys()
*Returns a dict_keys object, ex:
  
  list(ages.keys())
  ['Hannah', 'Kelsey', 'Brenda', 'Rylea', 'David']

note that you have to put the list first

VALUES
adict.values()
*Returns a dict_values object

ITEMS
adict.items()
*Returns a dict_items object

GET
adict.get(k)
*Returnst he value associated with k; None otherwise

GET
adict.get(k,alt)
*Returns the value associated with k; alt otherwise

IN
key in adict
*Returns True if key is in the dictionary; False otherwise. ex:

  'Rylea' in ages
  True

NOT IN
key not in adict
*Returns Ture if key is not in the dictionary; False otherwise

INDEX
adict[key]
*Returns the value associated with key

DEL
del adict[key]
*Removes the entre from the dictionary. ex:

  del ages['David']

EXAMPLES OF ADDING AND MODIFYING VALUES IN A DICTIONARY
ages['David']
ages['Kelsey'] = 19
  *to add a key
ages['David'] = ages['David'] + 1
  *To add a value to the key

STRUCTURE OF A KEY
ages = {'David':45,'Brenda':46}

MEDIAN
def median(alist):
  copylist = alist[:]
  copylist.sort()
  if len(copylist)%2 == 0:
    rightmid = len(copylist)//2
    leftmid = rightmid - 1
    median = (copylist[leftmid] + copylist[rightmid])/2.0
  else:
    mid = len(copylist)//2
    median = copylist[mid]
  return median

MEAN
def mean(alsit):
  mean = sum(alist) / len(alist)
  return mean
