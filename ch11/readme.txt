Python與AI人工智慧開發入門-21：https://youtu.be/H7L2It5pjnw
Python與AI人工智慧開發入門-22：https://youtu.be/IXqVIO4R5VI

### 延續ch10
print("分別挑選出數值型態與字串型態欄位")
col4=[] #字串
col5=[] #數值
for i in auto_price.columns:
    if auto_price[i].dtype==object:
        col4.append(i)
    else:
        col5.append(i)
print("字串欄位有:\n",col4)
print("數值欄位有:\n",col5)
print("字串型態資料內資料出現的比數統計")
for colume in col4:
    print("欄位為:",colume)
    print(auto_price[colume].value_counts())
    print()
==================================================
print("字串資料以長條圖顯示")
import matplotlib.pyplot as plt
for cols in col4:
    auto_price[cols].value_counts().plot(
        kind='bar',title=cols,rot=90)
    plt.show()
==================================================
print("數值資料與price之間關係，以散布圖顯示")
for cols in col5:
    auto_price.plot(
        kind='scatter',
        title=cols,
        x=cols,
        y='price',
        rot=45)
    plt.show()
==================================================
print("想要了解多個欄位之間的關係")
import seaborn as sns
sns.heatmap(auto_price[col5].corr())
plt.show()
************************************************************
print('假設跑步為a，跳繩為b')
a_mean=25
b_mean=10
a_std=2.3
b_std=5.9
#變異係數=標準差/平均數
a_cv=a_std/a_mean
b_cv=b_std/b_mean
print('跑步的變異係數:',a_cv)
print('跳繩的變異係數:',b_cv)
print('變異係數愈大代表這個團體的離散程度愈大')
==================================================
import pandas as pd
import numpy as np
fortrne = pd.read_csv("./fortune1000.csv",index_col='Rank')
print(fortrne)
a = fortrne['Revenue']
b = fortrne['Employees']
print("共異變數的推算，計算波動的程度")
print(np.cov(b,a))
print("相關係數的推算，計算兩者的相關性")
print(np.corrcoef(a,b))
==================================================
import pandas as pd
import numpy as np
# 財富美國1000強
# Rank 等級
fortune = pd.read_csv("fortune1000.csv",index_col='Rank')
print(fortune)
a=fortune['Revenue'] # 收入
b=fortune['Employees'] # 公司員工人數
print(np.corrcoef(a,b))
==================================================
import numpy as np
array1 = np.eye(4)
print("單位矩陣")
print(array1)
array2=np.array([[3,5,6,8],
                 [13,25,46,98],
                 [111,234,556,567]])
print("轉至矩陣")
print(np.transpose(array2))
print(array2.T)

s = [[1,2],
     [2,1]]
s = np.array(s)
print(s)
print(s.T)
==================================================
import numpy as np
array1=np.array([[1,2,3],
                 [4,5,6]])
array2=np.array([[5,8,9],
                 [1,3,7]])
print(array2+array1)
print(array2-array1)
==================================================
import numpy as np
a = [[15,14,15],
     [12,13,17]]
b = [[10,14],
    [5,18],
    [8,10]]
a = np.array(a)
b = np.array(b)
print(a.shape)
print(b.shape)

print(np.dot(a,b))
print(a@b)
==================================================
import numpy as np
a = np.array([[4,-7],
              [2,-3]])
a_inv = np.linalg.inv(a)
print(a_inv)
print(a @ a_inv)
print(a_inv @ a )
==================================================
import numpy as np
#共線性不可逆
B = np.array([[1,2],
             [4,8]])
b_inv = np.linalg.inv(B)
==================================================
import numpy as np
print("總金額 / 單價")
print("=總金額 * 單價的反矩陣")
print("得到反矩陣代表可以被整除")

price = np.array([[3,3.5],
                [3.2,3.6]])
total = [[118.4,135.2]]

try:
    price_inv =  np.linalg.inv(price)
    print(price_inv)
    
    print("dot:",np.dot(total,price_inv))
    c = total@price_inv #算出大人.小孩人數
    print("@:",c)
    print(c@price) #算回總金額
except:
    print("得不到反矩陣")
==================================================
import numpy as np
import matplotlib.pyplot as plt
x=np.arange(1,8)
y=[1,3,3,12,5,7,9]
plt.plot(x,y)
plt.show()
==================================================
import numpy as np
import matplotlib.pyplot as plt
x=np.arange(1,8)
y=[1,3,3,12,5,7,9]
slope,intercept=np.polyfit(x,y,1) #1代表1次方
print(slope,intercept)
y1=[slope*i+intercept for i in x]
plt.plot(x,y,'--')
plt.plot(x,y1,'b')
plt.show()
==================================================
import sympy as sp #聯立方程式
x = sp.Symbol("x")
y = sp.Symbol("y")
f1 = 2*x + 3 * y - 23
f2 = x + 4 * y - 24
print(sp.solve([f1,f2],[x,y]))
==================================================
#x+y=20
#50x+30y=800
#x=? y=?

x = sp.Symbol("x")
y = sp.Symbol("y")
f1 = x+y-20
f2 = 50*x+30*y-800
print(sp.solve([f1,f2],[x,y]))
==================================================
### 二次函數呈現與最大最小值

import  matplotlib.pyplot as plt
import  numpy as np
x=np.arange(-100,101,1)
y=3*np.power(x,2)-12*x+4
print('因為平方前面的係數是正數，所以會有最小值')
print(np.min(y))#找出y最小
print(x[y.argmin()]) #找出x最小
plt.plot(x,y)
plt.grid()
plt.show()
==================================================
import  matplotlib.pyplot as plt
import  numpy as np
x=np.arange(-100,101,1)
y=-3*np.power(x,2)-12*x+4
print('因為平方前面的係數是負數，所以會有最大值')
print(np.max(y))
print(x[y.argmax()])
plt.plot(x,y)
plt.grid()
plt.show()
==================================================
### 線性迴歸訓練預估
import pandas as pd
tvmarketing=pd.read_csv('tvmarketing.csv')
print(tvmarketing.head())
print(tvmarketing.shape)
tvmarketing.to_html('tvmarketing1.html')
print(tvmarketing.isnull().any())
print(tvmarketing.dtypes)
==================================================
import matplotlib.pyplot as plt
plt.scatter(tvmarketing['TV'],tvmarketing['Sales'])
plt.xlabel('TV')#營銷預算
plt.ylabel('Sales')#銷售額
plt.show()
==================================================
from sklearn.model_selection import train_test_split
import sklearn.linear_model
print('我們先建立X與y資料，後續才能進行切割')
X=tvmarketing['TV']
y=tvmarketing['Sales']

print('準備做資料切割')
X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.3)# 70% 做訓練 30%做測試
print(X_train.shape)
print(X_test.shape)
==================================================