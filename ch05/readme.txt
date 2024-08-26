Python與AI人工智慧開發入門-09：https://youtu.be/U3z3-TG5SL8
Python與AI人工智慧開發入門-10：https://youtu.be/VEwZXXFQ5P4

### 作業 文字接龍

txt = input("請輸入一個字串：")
strList = []
strList.append(txt)
msg = txt
count = 0
while count < 5:
    print("上一個字串是:"+msg)
    tmpTxt = input("請輸入-"+txt[-1]+"-開始的字串")
    if(tmpTxt[0]==txt[-1]):
        txt = tmpTxt
        strList.append(tmpTxt)
        msg = "-".join(strList)
    else :
        count +=1

### LIST 生成器

list1 = [i for i in range(1,51)]
print(list1)

## 幫我生成一個都是偶數的List 數字範圍是1~20
list2=[]
for i in range(1,21):
    if(i % 2 ==0):
        list2.append(i)
print(list2)

list2 = [i for i in range(1,21) if i%2 == 0]
print(list2)


### isinstance
isinstance(x,int) 代表判斷x是否為int型態
lit若要進行排序得先挑選出相同型態資料。
請使用isinstance(資料,資料型態)方式於list中撈出特定資料。
list2a=[x for x in list2 if isinstance(x,int)]
這樣的寫法的目的
避免程式流程受到外面的干擾
流程單純化，list的資料變化就在list區域內進行
促進語法的可讀性提高!

list4 = ['x',1,'y',2,'z',3,5.3,[8,9]]
print(list4)
sum = 0
for v in list4:
    if isinstance(v,int):
        sum += v
    elif isinstance(v,str):
        print("str:",v)
print(sum)

list5 = ['ken',1,'joy',2,'linda',3]
list6 = [v for v in list5]
print(list6)
listNo = [v for v in list5 if isinstance(v,int)]
print(listNo)
listName = [v for v in list5 if isinstance(v,str)]
print(listName)


### ZIP

nameList = ['ken', 'vivian', 'lucy']
scoreList = [98,77,65]
for i in range(len(nameList)):
    print(nameList[i],end="  ")
    print(scoreList[i])

nameList = ['ken', 'vivian', 'lucy']
scoreList = [98,77,65]
zipData = zip(nameList,scoreList)
print(list(zipData))

v1 = 10
v2 = 20
v1,v2 = (v2,v1)
print(v1,v2)
name,score = ('ken',98)
print(name)
print(score)

list5 = ['ken',1,'joy',2,'linda',3]
list6 = [v for v in list5]
print(list6)
listNo = [v for v in list5 if isinstance(v,int)]
print(listNo)
listName = [v for v in list5 if isinstance(v,str)]
print(listName)
for name,no in zip(listName,listNo):
    print(name,no)

list1 = ['a','b','c']
list2 = ['x','y','z']
list3 = []
list3.append(list1)
list3.append(list2)
print(list3)

list1 = ['a','b','c']
list2 = ['x','y','z']
list3 = []
list3.append(list1)
list3.append(list2)
print(list3) # 2*3矩陣
print(list3[0][1])
print(list3[1][2])
for ineerList in list3:
    #print(ineerList)
    for v in ineerList:
        print(v,end=" ")
    print()

### 展開

name = ['ken', 'joy', 'linda']
myList = ["Lucky","Iris"]
myList.append(name)
print(myList)
myList2 = ["Lucky","Iris"]
myList2.extend(name)
print(myList2)


### 輸出

age = 10
name = "ken"
height = 178.57689
msg = name + ":" + str(age) + ":" + str(height)
print(msg)
# %s字串 %d整數 %f浮點數
msg2 = "%s:%d:%.3f"%(name,age,height)
print(msg2)
msg3 = f"{name}:{age}:{height}"
print(msg3)


### Dictionary

d1 = {"a":100,"b":200,"c":300}
print(d1)
print(d1["b"])
print(d1["a"])
#print(d1["X"])

d2 = {"a":100,"b":200,"c":300}
for k in d2:
    print(f"{k}--{d2[k]}")
print()
for k2 in d2.keys():
    print(f"{k2}--{d2[k2]}")
print()
for v in d2.values():
    print(f"v:{v}")

d3 = {"a":100,"b":200,"c":300}
k="x"
findKey = False #預設沒有找到key
for key in d3:
    if key == k:
        findKey = True
        break
#找不到key顯示無此key
if findKey:
    print(d3[k])
else:
    print("無此Key")

d3 = {"a":100,"b":200,"c":300}
k="z"
for key in d3:
    if key == k:
        print(d3[k])
        break
else:#不是因為break離開迴圈就會執行
    print("無此Key")

d3 = {"a":100,"b":200,"c":300}
k = "b"
if k in d3:
    print(d3[k])
else:
    print("無此Key")

d3 = {"a":100,"b":200,"c":300}
k = "b"
v = d3[k] if k in d3 else "無此key"
print(v)

myList = [10,20,50,99]
v = 50
if v in myList:
    print(f"{v}存在")
else:
    print(f"{v}不存在")


### 新增與修改

dict2 = {"ken":100,"vivian":200,"lucy":300}
print(dict2)
dict2["vivian"] = 86 # key存在就修改
print(dict2)
dict2["tom"] = 99 # key不存在就新增
print(dict2)


