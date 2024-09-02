Python與AI人工智慧開發入門-11：https://youtu.be/4c-vNbOLWAI
Python與AI人工智慧開發入門-12：https://youtu.be/-IjHrgwcXVE
作業
myFruit = ["apple","watermalon","papaya"]
fruit = input("請輸入水果:")
if fruit in myFruit:
    print(f"{fruit}在清單內")
else:
    print(f"{fruit}不在清單內")

myFruit = ["apple","watermalon","papaya"]
fruit = input("請輸入水果:")
for f in myFruit:
    if fruit == f:
        print(f"{fruit}在清單內")  
        break
else:
    print(f"{fruit}不在清單內")


### 自訂函數的運用
程式設計時儘量減少相同語法的重複出現，為什麼?
修改時可能忘記其他地方沒有改，導致程式執行出現錯誤結果。
減少重複語法對於之後的維修會比較方便。
要如何減少重複的相同語法?
把重複的相同語法當作工具看待，需要的時候呼叫他。
這種工具於程式語法內叫做函數(function)。

for i in range(1,6):
    print(i,end=" ")
print()
for i in range(3,9):
    print(i,end=" ")
print()
for i in range(5,8):
    print(i,end=" ")
print()

def testFun():
    print("Test1")
testFun()
testFun()

def testFun2(a,b):
    c = a+b
    print(c)
testFun2(5,6)
testFun2(7,9)

def forLoop(s,e):
    for i in range(s,e+1):
        print(i,end="  ")
    print()
forLoop(1,5)
forLoop(2,9)
forLoop(3,8)

def funcX(x):
    ans = x**2
    return ans
for i in range (1,10):
    point = funcX(i)
    print(point)

import matplotlib.pyplot as plt
fig,ax = plt.subplots()
yList = []
xList = []
for x in range(0,1000):
    y = funcX(x)
    yList.append(y)
    xList.append(x)
ax.plot(xList,yList)
plt.show()

def func3(v1,v2,v3):
    a1 = v1+2
    a2 = v2+3
    a3 = v3+4
    return(a1,a2,a3)
ans = func3(2,3,5)
print(ans)

def func3(v1,v2,v3):
    a1 = v1+2
    a2 = v2+3
    a3 = v3+4
    return(a1,a2,a3)
ans = func3(2,3,5)
print(ans)
x,y,z = func3(2,3,5)
print(x,y,z)

def manyValue(v1,v2):
    v3 = v1+v2
    return v1,v2,v3
x,*_ = manyValue(2,3)
print(x)
data = manyValue(2,3)
print(data[0],data[-1])


### 變數影響範圍
函數外的變數：
函數內可以顯示該變數內容
不屬於函數的區域內都可以使用
函數內的變數：
只在函數內產生效果，不會影響函數外的變數
若函數內沒有進行變數宣告而進行改變內容動作將會產生錯誤訊息!

a = 5
def func_sum():
    print("a:",a)
func_sum()

a = 5
def chang():
    a = 100
    print("內部a:",a)
chang()
print("外部a:",a)

a = 5
def add():
    #a=0
    a=a+2
    print("內部a:",a)
add()
print("外部a:",a)

a = 5
def add():
    a=0
    a=a+2
    print("內部a:",a)
add()
print("外部a:",a)

a = 5
def add():
    global a #跟python說a是外部變數
    a=a+2
    print("內部a:",a)
add()
print("外部a:",a)


### 排序

myList = [8,1,2,7,6]
sortList = sorted(myList) # 預設小到大
sortList2 = sorted(myList,reverse=True)  #reverse=True 大到小
print(myList)
print(sortList)
print(sortList2)

myList2 = [8,1,2,7,6]
myList2.sort(reverse=True)
print(myList2)

## 函數的其他用法
### 預設函數

def printInfo(name):
    print("name:",name)
def printInfo(name,age):
    print("name:",name,"age:",age)
printInfo("ken")
printInfo("ken",18)

def printInfo(name="Iris",age=18):
    print("name:",name,"age:",age)
printInfo("ken") 
printInfo("vivin",18)

#順序必須: 必填,預設
def testDefault(v1,v2=10,v3=20):
    print(v1,v2,v3)
testDefault(1)
testDefault(2,4)
testDefault(1,5,6)

# error
def testDefault(v1=10,v2,v3=20):
    print(v1,v2,v3)

def printInfo(name="lucy",age=18,height=180):
    print(name,age,height)
printInfo("iris",20,160)
printInfo(name="iis")
printInfo(age=24)
#只要使用參數名稱傳遞參數，必須持續使用
#printInfo(age=23,height=170,"joy")
printInfo(age=23,height=170,name="joy")
printInfo("joy",age=44,height=190)


###不固定接收數量
( ) 內接收資料若是以 * 表示代表可以引入不定數量的參數：
一個*代表以 tuple 的方式引入
兩個*代表以 dict 的方式引入
接收資料若需加入多個設定，這些設定請依照順序排列：
第一個參數設定為接收值
第二個參數設定為初始值
第三個參數設定為不固定值，可以是 tuple 或 dict 方式

def printInfo(arg1,arg2="default",*arg3):
    print("arg1:",arg1)
    print("arg2:",arg2)
    print("arg3:",arg3)
    print("==================")
printInfo(1)
printInfo(1,2)
printInfo(1,2,3)
printInfo(1,2,3,4)

def printInfo(*arg3,arg1,arg2="default"):
    print("arg1:",arg1)
    print("arg2:",arg2)
    print("arg3:",arg3)
    print("==================")
#printInfo(arg1=10,arg2=20,3,4)
#printInfo(1,2,3,4,5)
printInfo(1,2,3,arg1=4,arg2=5)

def sumValue(*args):
    v = 0
    for a in args:
        v += a
    return v
print(sumValue())
print(sumValue(2))
print(sumValue(2,3))
print(sumValue(2,3,4))

def fun4(arg1,arg2="default",**arg3):
    print(arg1)
    print(arg2)
    print(arg3)
    print("="*20)
fun4(1)
fun4(1,2)
fun4(1,2,name="kevin",age=15,score=86)

def calculate(*values,**args):
    cType = "+"
    result = 0
    if "cType" in args:
        cType = args["cType"]
    if cType == "*":
        result = 1
    for v in values:
        if cType == "+":
            result += v
        elif cType == "*":
            result *= v
    return result
r = calculate(3,2,4,cType="*")
print(r)

def testReturn(b1):
    print("Test1")
    if b1 :
        return #函式結束
    print("Test2")
testReturn(False)
print("="*20)
testReturn(True)

# 暫時先不寫，後面可以再寫
def testPass():
    pass


### 匿名函數
不需要定義函數名稱，只需要用到運算式或表達分析語法
Python使用lambda語法定義匿名數。
匿名函數是一個表達式或計算式，並不是一個執行程區塊。
匿名函數出現在一般函數不允許的地方，例如list裡面或著函數呼叫參數的位置。

def fx(x,y,z):
    return x+y+z
print(type(fx))
print(fx(5,6,7))

def fx(x,y,z):
    return x+y+z
print(type(fx))
print(fx(5,6,7))
myFx2 = fx
print(myFx2(3,2,8))

f2 = lambda x,y,z : x+y+z
print(f2(2,30,400))

list2 = [lambda x:x**2,lambda x:x**3,lambda x:x**4]
for f in list2:
    print(f(3))

findMain = lambda x,y:x if x<y else y
print(findMain(10,20))
print(findMain(40,30))


### MAP 適合轉換

list3=[1,2,3,'',4,5,'']
map0b=map(lambda x:x if x!='' else 0,list3)
print(list(map0b))

list4 = ['M','W','M','M','W']
myDirc = {'M':0,'W':1}
objMap = map(lambda x:myDirc[x],list4)
print(list(objMap))


### Filter 適合過濾

a = [1,2,3,4,5,6]
f1 = filter(lambda x : x%2==0 , a)
print(list(f1))

list3 = [1,2,3,'',4,5,'']
f2 = filter(lambda x:x!='',list3)
print(list(f2))


###Python 程式偵錯
Syntax Errors 語法錯誤
該行語法錯誤，Python 無法編譯執行。
修正語法錯誤
Exception 例外
語法撰寫上沒有錯誤，執行時因資料邏輯或外部系統狀態發生錯誤， Python 會引發例外(Exception)
如果例外沒有被處理而傳遞到Python直譯器，程式中斷執行

num1 = 10
num2 = 0
print(num1/num2)


### 例外語法
try: 保護的程式區段
except 例外1 : 例外1發生時執行的程式
except : 其他例外發生時執行的程式 #未指定例外型態，捕捉所有例外物件
else: 若try程式區段沒產生例外執行的程式
finally: 不管有沒有發生例外都會執行的程式

num1 = 10
num2 = 0
myList = [5,6,7]
try:
    myList[8]
    print(num1/num2)
except ZeroDivisionError:
    print("分母不可為0")
except IndexError:
    print("Index錯誤")
print("Test1")

list1 = [7,99,61]
try:
    while True:
        print(list1.pop())
except:
    pass