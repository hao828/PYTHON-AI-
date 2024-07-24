20240316 課堂筆記

講師提供程式碼
https://github.com/xvpowerg/ai_python20240316/tree/main/ai_python_20240316

開發軟體 Anaconda
https://www.anaconda.com/download-success

windows系統安裝Anaconda注意事項
→務必點選ALL User

開啟Jupyter Notebook
Anaconda→Jupyter Notebook(以系統管理員身分執行)

Jupyter網頁 新增一個資料夾
new→folder
建立專案Python 3(ipykernel)

若Jupyter當機，則將其完全關閉後重新打開網站F5
---------------------------------------------------------------------------------------------------
Shift + Enter 執行
---------------------------------------------------------------------------------------------------
MarkDown 可用於新增筆記內容(標題.字體大小.段落等)
https://hackmd.io/@eMP9zQQ0Qt6I8Uqp2Vqy6w/SyiOheL5N/%2FBVqowKshRH246Q7UDyodFA?type=book
# 標題1
### 小標題 輸出
*斜體字*
**粗體字**
***斜體兼粗體***
~~刪除線~~
[GOOLGE](https://www.google.com.tw/"游標顯示") #超連結
![01-3.png](attachment:01-3.png) #插入圖片
---------------------------------------------------------------------------------------------------
# 輸出

print("Test!") #函式 function
---------------------------------------------------------------------------------------------------
# 變數


### 整數 浮點數
a1 = 1.34
print(a1)
ans = a1+5
print(ans)

### 文字
msg = "你好"
print(msg)
中文 = "午安" # 變數名稱可使用中文
print(中文)
For = 10
print(For)

### 同時宣告多個變數
a,b = 10,20
print(a,b)
c,d,e = 1.35,"OK",70
print(c,d,e)

### 變數沒有固定類型
v1 = 20
print(v1)
v1 = 123.56
print(v1)
v1 = "strin1"
print(v1)
v1 = True
print(v1)

### type 可輸出類型

v2 = 20
print(type(v2))
v2 = 1.34
print(type(v2))
v2 = "MSG"
print(type(v2))
v2 = False
print(type(v2))

### id 可輸出記憶體位置
a = 5
print(id(a))
b = 65
print(id(b))
g = 5
print(id(g))

### 串接
# 字串不能跟數字串接
# 串接只能跟相同類型的
age = 15
msg = "年齡" + age

#使用str將age轉換成文字
age = 15
msg = "年齡:"+ str(age)
print(msg)

#文字類型*n次意思就是輸出n次
msg = "午安 "
n = 5
print(msg*n)

#a = 50,b = 3.14,c = "vivin" 錯誤
a,b,c = 50,3.14,"Ken"
print(a,b,c)

# 2變數交換數值(傳統作法)
v1 = 56
v2 = 38
print ("v1:",v1,"  v2:",v2)
c = v1 # C=56
v1 = v2 # v1=38
v2 = c # v2=56
print ("v1:",v1,"  v2:",v2)

# 2變數交換數值(python作法)
v3 = 72
v4 = 94
print("v3:",v3,"v4:",v4)
v3,v4 = v4,v3
print("v3:",v3,"v4:",v4)

# 多變數指定為同一值
v1=v2=v3=v4=0
print(v1,v2,v3,v4)

# 算術運算+-/*
a,b = 10,3
print(a + b)
print(a - b)
print(a * b)
print(a / b) 
print(a // b) # 無條件捨去(取商數)
print(a % b) # 取餘數
#round 取到小數點到第n位
ans = a/b
print(round (ans,2))
print(round (ans,3))
# **次方
v1 = 2
ans = v1 ** 3 #v1的3次方
print(ans)
ans2 = v1 ** -1 #2的-1次方
print(ans2)
ans3 = v1 ** 0.5 #開根號(2的1/2次方)
print(ans3)
