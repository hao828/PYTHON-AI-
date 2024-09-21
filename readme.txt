Python與AI人工智慧開發入門-13：https://youtu.be/4WWusRGvyFo
Python與AI人工智慧開發入門-14：https://youtu.be/9by55Kp3q5U

### 作業
priceList=[]
priceSum = 0
for i in range(1,5):
    p = int(input(f"請輸入{i}個月的支出金額"))
    priceSum =priceSum + p
    priceList.append(p)
priceList.sort()
print(f"max:{priceList[len(priceList)-1]}") 
print(f"min:{priceList[0]}")
print(priceSum)    
print(priceList) 
print("=====================================")
print(sum(priceList)) 
print(max(priceList))    
print(min(priceList)) 


num1 = 10
num2 = 0
try:
    print(num1/num2)
except ZeroDivisionError :
    print("有問題發生:","ZeroDivisionError")
print("TEST!!")

myList = [1,2,3]
try:
    while True:
        print("TEST1")
        print(myList.pop())
        print("TEST2")
except:
    pass

def testScore(score:int):
    if score < 0 or score > 100:
        print("錯誤的成績")
        return
    print("score:",score)    
    #score是0~100顯示成績
    #不在範圍內 錯誤的成績
testScore(60)


### 使用raise 拋出例外
def testScore(score:int):
    if score < 0 or score > 100:
        raise OverflowError("錯誤的成績")
    print("score:",score)    
print("Test1!")
testScore(-1)
print("Test2!")


n1 = 10
n2 = 0
myList=[1,2,3]
try: 
    #n1/n2
    #myList[10]
    myListx.pop()
except ZeroDivisionError as ex:
    print("ZeroDivisionError:",ex)
except IndexError as ex:
    print("IndexError:",ex)
except Exception as ex: #除了以上其他的錯誤
    print("Exception",ex)


### 正規表示式
import re
s = "Tim's phone numbers are 12345-41521 and 78963-85214"
match = re.findall(r"\d",s)
print(match)

import re
s = "Tim's phone numbers are 12345-41521 and 78963-85214"
match = re.findall(r"\d{5}",s)
print(match)

import  re
s="Python was conceiaaaaaaaaaaaaaaaaaaaved in the late 1980s by Guido van Rossum"
match = re.findall(r"[a-t]",s)
print(match)
match2 = re.findall(r"[a-t]{2}",s)
print(match2)
match3 = re.findall(r"[a-t]{3,6}",s)
print(match3)
match4 = re.findall(r"[a-t]{4,}",s)
print(match4)

import re
pattern = re.compile(r"\d+")
r1 = pattern.findall("hell12o 12345 6789")
r2 = pattern.findall("abc 1545531 8465 456")
print(r1)
print(r2)

import re
str1 = "abc1d abcdd abc2d abc aaaa"
print(re.findall(r"abcd?",str1))
print(re.findall(r"abcd*",str1))
print(re.findall(r"abcd+",str1))


### split方法
import re
text = "one,two,ten"
v1 = re.split(",",text)
print(v1)
print(v1[0])
v2 = re.split(",",text,1)
print(v2)


### SUB方法
import re
inputStr = "This is Python.That is Java,This is SQLite"
nStr = inputStr.replace("is","-")
print(nStr)

import re
inputStr = "This is Python.That is Java,This is SQLite"
# \b 單詞邊界 空白無字的
nStr = re.sub(r"\bis\b","-",inputStr)
print(nStr)


### 物件導向入門
class Employee:
    pass

class Employee:
    pass
emp = Employee() #建立物件
print(type(emp))

class Employee:
    pass
emp = Employee() #建立物件
print(type(emp))
emp.name = "Ken"
emp.salary = 50000
print(emp.name,emp.salary)

class Employee:
    pass
emp = Employee() #建立物件
print(type(emp))
emp.name = "Ken" #建立屬性
emp.salary = 50000
print(emp.name,emp.salary)
emp2 = Employee()
print(emp2.name)

class Employee:
    def __init__(self,name,salary):
        self.name = name
        self.salary = salary
emp1 = Employee("Ken",25000)
print(emp1.name)
print(emp1.salary)

class Employee:
    def __init__(self,name,salary):
        self.name = name
        self.salary = salary
emp1 = Employee("Ken",25000)
print(emp1.name)
print(emp1.salary)
emp2 = Employee("vivian",50000)
print(emp2.name)
print(emp2.salary)

class Employee:
    def __init__(self,name,salary):
        self.name = name
        self.salary = salary
    def printInfo(self):
        print("name:",self.name,"salary:",self.salary)
emp1 = Employee("Ken",25000)
emp1.printInfo()
emp2 = Employee("vivian",50000)
emp2.printInfo()


### 繼承

class Animal:
    def __init__(self,name,age=0):
        self.name = name
        self.age = age
    def printInfo(self):
        print(self.name,self.age)
an1 = Animal("BOBO")
an1.printInfo()
an2 = Animal("LULU",5)
an2.printInfo()

class cat:
    pass
cat1 = cat("Kitty",3)
cat1.printInfo()

class cat(Animal):
    pass
cat1 = cat("Kitty",3)
cat1.printInfo()

class Dog(Animal):
    pass
dog1 = Dog("kiki",2)
dog1.printInfo()

class cat(Animal):
    def printInfo(self):
        print("C:",self.name,self.age)
cat1 = cat("Kitty",3)
cat1.printInfo()

 class Dog(Animal):
    def printInfo(self):
        print("D:",end="")
        super().printInfo() #super()呼叫父類別的東西
dog1 = Dog("kiki",2)
dog1.printInfo()

class S:
    def method1(self):
        print("S method1")
    def method2(self):
        print("S method2")
class A(S):
    def method3(self):
        print("A method3")
class B(S):
    def method2(self):
        print("B method2")
    def method3(self):
        print("B method3")
class C(A,B):
    def method4(self):
        print("C method4")
c=C()
c.method4()
c.method3()
c.method2()
c.method1()


### str可輸出物件的內容
class Point:
    def __init__(self,x,y):
        self.x = x
        self.y = y
p1 = Point(2,3)
p2 = Point(-1,2)
print(p1)
print(p2)

class Point:
    def __init__(self,x,y):
        self.x = x
        self.y = y
    def __str__(self):
        return f"({self.x},{self.y})"
p1 = Point(2,3)
p2 = Point(-1,2)
print(p1)
print(p2)

class Point:
    def __init__(self,x,y):
        self.x = x
        self.y = y
    def __str__(self):
        return f"({self.x},{self.y})"
p1 = Point(2,3)
p2 = Point(-1,2)
print(p1)
print(p2)
p3 = p1+p2

class Point:
    def __init__(self,x,y):
        self.x = x
        self.y = y
    def __str__(self):
        return f"({self.x},{self.y})"
    def __add__(self,other):
        x = self.x+other.x
        y = self.y+other.y
        return Point(x,y)
p1 = Point(2,3)
p2 = Point(-1,2)
print(p1)
print(p2)
p3 = p1+p2
print(p3)

class Point:
    def __init__(self,x,y):
        self.x = x
        self.y = y
    def __str__(self):
        return f"({self.x},{self.y})"
    def __add__(self,other):
        x = self.x+other.x
        y = self.y+other.y
        return Point(x,y)
    def __len__(self):
        myLen = (self.x**2) + (self.y**2)
        return myLen
p1 = Point(2,3)
p2 = Point(-1,2)
print(p1)
print(p2)
p3 = p1+p2
print(p3)
print(len(p1))

class Point:
    def __init__(self,x,y):
        self.x = x
        self.y = y
    def __str__(self):
        return f"({self.x},{self.y})"
    def __add__(self,other):
        x = self.x+other.x
        y = self.y+other.y
        return Point(x,y)
    def __len__(self):
        myLen = (self.x**2) + (self.y**2)
        return myLen
p1 = Point(2,3)
p2 = Point(-1,2)
p3 = Point(9,11)
p4 = Point(7,12)
pointList = [p1,p2,p3,p4]
pointList.sort()
for p in pointList:
    print(p)

class Point:
    def __init__(self,x,y):
        self.x = x
        self.y = y
    def __str__(self):
        return f"({self.x},{self.y})"
    def __add__(self,other):
        x = self.x+other.x
        y = self.y+other.y
        return Point(x,y)
    def __len__(self):
        myLen = (self.x**2) + (self.y**2)
        return myLen
    def __lt__(self,other):
        selfLen = len(self)
        otherLen = len(other)
        return selfLen < otherLen
p1 = Point(2,3)
p2 = Point(-1,2)
p3 = Point(9,11)
p4 = Point(7,12)
print(p1<p2)
print(p1>p2)
pointList = [p1,p2,p3,p4]
pointList.sort()
for p in pointList:
    print(p)


### 目錄管理
import os
print(os.getcwd())

import os
# 切換路徑
#os.chdir(r"C:\Users\HHH\ai_python_20240316\Ch7")
print(os.getcwd())
myDir = os.listdir()
for f in myDir:
    print(f)

from os import listdir
from os.path import isfile,isdir
files = listdir()
print(files)
for f in files:
    if isfile(f):
        print("檔案:",f)
    elif isdir(f):
         print("目錄:",f)

from os import walk
import os
print(os.getcwd())
mypath = "."
for root,dirs,files in walk(mypath):
    print("路徑:",root)
    print("  目錄:",dirs)
    print("  檔案:",files)


