Python與AI人工智慧開發入門-07:https://youtu.be/0ABrdbSSq7w
Python與AI人工智慧開發入門-08:https://youtu.be/NtRMkHkQ5eg

### split

str4 = "python-java-c++-ruby"
print(str4.split("-"))
print(str4.split("-",2))

# 練習 文字接龍
error = 0
str1 = input("請輸入一個字串:")
print("上一個字串是",str1)
while error<5:
    strA = "請輸入-"+str1[-1]+"-開始的字串:"
    str2=input(strA)
    if str1[-1] == str2[0]:
        str1 = str1 + "-" + str2 
        print("上一個字串是",str1)
    else :
        error += 1
print("結束遊戲")

### List vs Tuple

myList = ["A",10,3.14]
myTuple = ("ken",35)
print(type(myList))
print(type(myTuple))

myList = ["Oen"]
print(myList)
myTuple = (10) #()也是算術的一種，故type會變成INT
print(myTuple)
print(type(myTuple))
myTuple = (10,)
print(myTuple)
print(type(myTuple))

# list的功能turple也有，但turple為固定資料，無法修改新增資料
myList = ["A","B","C","D","E"]
myTurple = ("X","Y","Z",20,30.14)
print(len(myList))
print(len(myTurple))
print(myList[:3])
print(myTurple[:3])

a1 = 5 
b2 = 9
a1,b2 = b2,a1
print(a1,b2)

result = ("ProjectName",10.5,24.3)
pName = result[0]
h = result[1]
w = result[2]
print(pName,h,w)
print(result)

result = ("ProjectName",10.5,24.3)
pName,h,w = result # 指定分配
print(pName,h,w)

result = ("ProjectName",10.5,24.3,25,67,88,99)
pName,h = result[1],result[-4] # 指定分配不能取非連續型的
print(pName,h)

result = ("ProjectName",10.5,24.3,25,67,88,99)
pName,h,w,*_ = result # *表示任何一種類型，_約定俗成為不需要用到的東西
print(pName,h,w)

a = (3,1,2)
b = (5,6)
c = a + b #turple 非修改
print(c)
listA = ["A","B","C"]
listB = ["D","E","F"]
listC = listA + listB
print(listC)

listA = ["KEN","VIVIAN","LUCY","IRIS"]
listA[0] = 10
print(listA)
print(listA[:-1])
print(listA[-1:-4:-1])
print(listA[::2])
print(listA[1:3])

myList = ["A","B","C","D","E"]
newList = myList[:3]
print("myList:",id(myList))
print("newList:",id(newList))
newList[0] = "X"
print(myList)
print(newList)
print("newList:",id(newList))

### 資料轉換

# 轉list
r = range(1,10)
rList = list(r)
print(rList)
rList[2] = 25
print(rList)
myTuple = (5,6,7,9)
tList = list(myTuple)
tList[0] = 11
print(myTuple)
print(tList)
print(tList)

### 拷貝與附加

list1 = [1,2,3,4,5]
list2 = list1
print(list2)
list2[1]=77
print(list1)
print(id(list1))
print(id(list2))

# 拷貝copy
list1 = [1,2,3,4,5]
list2 = list1.copy()
print(id(list1))
print(id(list2))
list2[2] = 77
print(list1)
print(list2)

# 附加 append
# 插入 insert
list1 = [1,2,3,4,5]
list1.append(99)
list1.append(100)
print(list1)
list1.insert(1,200)
print(list1)

### list 項目插入新資料

list1 = ["a","b","c","d","e"]
print(len(list1))
list1.insert(1,"X")
print(list1)
list1.insert(-2,"Y")
print(list1)
list1.insert(-4,"Z")
print(list1)
list1.insert(88,"GG")
print(list1)

### set
# 會過濾重複資料
# 不能夠透過索引值取值
mySet = {"A","B","A","C","B","E"}
print(mySet)
for v in mySet:
    print(v)

data = []
for _ in range(5):
    v = input("輸入字串:")
    data.append(v)
print(data)
dataSet = set(data) #過濾重複
print(dataSet)
dataList = list(dataSet)
print(dataList)
sorted(dataList) # 排序

### 移除

# remove
# 依據內容進行刪除
# list.remove(項目內容)
list1 = ["1","X","2","X","3","X"]
list1.remove("X")
if "X" in list1:
    list1.remove("X")
print(list1)

list1 = ["1","X","2","X","3","X"]
while True:
    if "X" in list1:
        list1.remove("X")
    else:
        break
print(list1)

# pop
# 如果pop()內沒有參數，則移除最後一筆資料
# pop()內若有參數，則移除指定位置的資料
list2 = []
list2.append("KEN")
list2.append("VIVIAN")
list2.append("LUCKY")
list2.append("IRIS")
print(list2)
print(list2.pop())
print(list2.pop()) #list如果空了會錯誤
print(list2.pop(1))
while len(list2)>0:
    print(list2.pop())

# del
# list 可透過del方式移除指定位置資料
# del list[]必須指定範圍:
#  del list[n]代表移除第n位索引值資料
#  del list[:m]代表移除第m位索引值(不包括m)之前的資料
#  del list[n:m]代表移除第n位到第m位索引值(不包括m)之前資料
list1 = ["a","b","c","d","e"]
print(list1)
del list1[2]
print(list1)
del list1[1:3]
print(list1)

### list生成器

nList = [i for i in range(1,23)]
print(nList)


