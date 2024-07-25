Python與AI人工智慧開發入門-03:https://youtu.be/juQ7ecT2zHs
Python與AI人工智慧開發入門-04:https://youtu.be/3alvNd4BcF4

輸入資料
### input("可放提示詞")

# 輸入的資料一律都是字串類型
a = input("請輸入一個數字")
print("a:",a)
print("type:",type(a))
b = int(a) # 把a內容轉成整數int
print("b:",b)
print("type:",type(b))

score = int(input("請輸入成績:"))
print("成績:",score)
print(type(score))

# 練習
# 輸入2個數字是 5 2
# 輸出 5 + 2 =7
v1 = int(input("請輸入第一個數字:"))
v2 = int(input("請輸入第二個數字:"))
print(v1,"+",v2,"=",v1+v2)


### 指定運算子
hp = 100
atk = 2
up = 1
hp = hp -atk
print(hp)
hp = hp + up
print(hp)

#指定運算子 -= +=
hp = 100
atk = 2
up = 1
hp -= atk
print(hp)
hp += up
print(hp)


### 關係運算子
a = 10
b = 5
print(a>b)
print(a<b)
print(a >= b)
print(a <= b)
print(a == b) #a與b是否相等 ==
print(a != b) #a與b是否不相等 !=


### 邏輯運算
b1 = True
b2 = False
print(b1 and b2) # 左右兩個條件若都為真則為真，否則為假
print(b1 or b2) # 左右兩個條件只要一個為真則為真，否則為假
print(not b1) # 條件若為真則改為假，為假則改為真

# if else
age = 18
if age >= 18:
    print("成年")
else:
    print("未成年")

score = 75
if score >= 70 and score <= 100 :
    print("過關")
else:
    print("有問題")

score = 75
if 70 <= score <= 100:
    print("過關")
else:
    print("有問題")

# if elif else
# 0~35 低
# 36~53 中
# 54~70 高
# >70 非常高
pm = int(input("請輸入PM值:"))
if pm < 0 :
    print("錯誤")
elif 0 <= pm <= 35 :
    print("低")
elif 36 <= pm <= 53 :
    print("中")
elif 54 <= pm <= 70 : 
    print("高")
else :
    print("非常高")

# 練習
# 輸入身高體重
# 輸出BMI = 體重/身高^2(單位公尺)
# BMI <18.5 太輕
# BMI 18.5~25 正常
# BMI 25~30 過重
# BMI >30 肥胖
h = float(input("請輸入身高，單位為公分:"))
w = int(input("請輸入體重，單位為公斤:"))
bmi = w/((h/100)**2)
if bmi < 18.5:
    ans = "太輕"
elif 18.5 <= bmi < 25:
    ans = "正常"
elif 25 <= bmi < 30:
    ans = "過重"
else:
    ans = "肥胖"
print("your BMI is",bmi,"您的體重",ans)
---------------------------------------------------------------------------------------------------

FOR 迴圈
### 知道數量時使用for loop
### python的for 有一種由頭到取數值的想法

### range
r1 = range(5)
r1 = list(r1)
print(r1)
r2 = range(2,11)
r2 = list(r2)
print(r2)
r3 = range(1,20,2)
print(list(r3))
r4 = range(20,0,-2)
print(list(r4))

### for
for i in range(10):
    print(i)

for k in range(2,8):
    print(k,end=" ") #end每次呼叫print結尾輸出什麼
print()
print(2,end=" ")
print(3,end=" ")
print(4,end=" ")
print(5,end=" ")
print(6,end=" ")
print(7,end=" ")

for x in range(2,18,3):
    print(x,end = " ")

for y in range(10,1,-2):
    print(y,end = " ")

for i in range(4):
    print(i)
print("離開後的i:",i)
for x in range(i,-1,-1):
    print(x)
print("離開後的x:",x)

### while 迴圈

a = 6
while a>0:
    print(a)
    a-=1

n='y'
while n == 'y':
    a = int(input("請輸入第一個數字:"))
    b = int(input("請輸入第二個數字:"))
    ans = a*b
    print(a,"*",b,"=",ans)
    n = input("是否繼續y/n :")
    n = n.lower()

# break 代表不回頭，跳出迴圈
# continue 代表繼續執行下一個迴圈
for i in range(11):
    print(i)
    if i == 5:
        break

for i in range(11):
    if i == 5 or i == 7:
        continue
    print(i,end=" ")

