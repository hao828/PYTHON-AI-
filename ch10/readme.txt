Python與AI人工智慧開發入門-19：https://youtu.be/877c6QuFz44
Python與AI人工智慧開發入門-20：https://youtu.be/9rgPtjY2BcY

import numpy as np
import pandas as pd
df = pd.DataFrame(
    np.arange(48).reshape(6,8),
    index =['a','b','c','d','e','f'],
    columns=['s','t','u','v','w','x','y','z'])
print(df)
============================================================
import numpy as np
import pandas as pd
df = pd.DataFrame(
    np.arange(48).reshape(6,8),
    index =['a','b','c','d','e','f'],
    columns=['s','t','u','v','w','x','y','z'])
print(df)
print()
print(df.loc['b',:])
============================================================
import numpy as np
import pandas as pd
df = pd.DataFrame(
    np.arange(48).reshape(6,8),
    index =['a','b','c','d','e','f'],
    columns=['s','t','u','v','w','x','y','z'])
print(df)
print("="*50)
print(df.loc['b',:])
print("="*50)
print(df.loc['c','w'])
============================================================
import numpy as np
import pandas as pd
df = pd.DataFrame(
    np.arange(48).reshape(6,8),
    index =['a','b','c','d','e','f'],
    columns=['s','t','u','v','w','x','y','z'])
print(df)
print("="*50)
newDf = df.loc[:,'y']
#刪除y
df.drop('y',axis=1,inplace=True)
print(df)
print("="*50)
#新增欄位A
df['A'] = newDf
print(df)
============================================================
import numpy as np
import pandas as pd
data_url = 'http://bit.ly/2cLzoxH'
gap1 = pd.read_csv(data_url)
print(gap1)
============================================================
import numpy as np
import pandas as pd
data_url = 'http://bit.ly/2cLzoxH'
gap1 = pd.read_csv(data_url)
print(gap1)
print(gap1.count())
============================================================
import numpy as np
import pandas as pd
data_url = 'http://bit.ly/2cLzoxH'
gap1 = pd.read_csv(data_url)
print(gap1)
print(gap1.count())
print("="*50)
is2002 = gap1['year'] == 2002
print(is2002)
print("="*50)
is2002Df = gap1[is2002]
print(is2002Df)
print(is2002Df.count())
============================================================
import numpy as np
import pandas as pd
data_url = 'http://bit.ly/2cLzoxH'
gap1 = pd.read_csv(data_url)
print(gap1)
gap2 = gap1.query("year==2002")
print(gap2)
gap2 = gap1.query("year==2002 or year==1992")
print(gap2)
============================================================
import numpy as np
import pandas as pd
data_url = 'http://bit.ly/2cLzoxH'
gap1 = pd.read_csv(data_url)
print(gap1)
gap2 = gap1.query("year==2002 or year==1992")
print(gap2)
print("="*50)

is1920 = gap1["year"].isin([1992,2002])
print(gap1[is1920])
============================================================
import numpy as np
import pandas as pd
data_url = 'http://bit.ly/2cLzoxH'
gap1 = pd.read_csv(data_url)
print(gap1)
print("想要查詢1997到2007年資料")
is2020  =gap1["year"].between(1997,2007)
print(gap1[is2020])
============================================================
import numpy as np
import pandas as pd
data_url = 'http://bit.ly/2cLzoxH'
gap1 = pd.read_csv(data_url)
print(gap1)
print("想要查詢1997到2007年資料")
is2020  =gap1["year"].between(1997,2007)
print(gap1[is2020])
gap2 = gap1.query("year.between(1997,2007)")
print(gap2)
============================================================
### 處理日期資訊
可使用 pandas 的 date_range( ) 函數，可以建立日期資料。
默認情況下，範圍的週期單位為天。
若要表達出工作天 (不包含周六周日)，則請選擇 bdate_range( ) 方法。
date_range 或 bdate_range( ) 內的參數：
('起始日期', periods=天數)
periods 由開始日取幾天
('起始日期','結束日期')
可加入另外一個參數：freq 代表範圍的週期單位

import numpy as np
import pandas as pd
a1 = pd.date_range('2024/5/18',periods=10)
print(a1)
============================================================
import numpy as np
import pandas as pd
a1 = pd.date_range('2024/5/18',periods=10)
print(a1)
a2 = pd.date_range('2024/5/18',periods=10,freq='W')
print(a2)
a3 = pd.date_range('2024/5/18',periods=10,freq='W-Mon')
print(a3)
============================================================
import pandas as pd
from datetime import date
start = date(2024,10,25)
end = date(2024,12,31)
a = pd.date_range(start,end)
b = pd.bdate_range(start,end) #工作日
c = pd.date_range(start,end,freq="W")
d = pd.date_range(start,end,freq="M")
print(a)
print('='*50)
print(b)
print('='*50)
print(c)
print('='*50)
print(d)
print('='*50)
============================================================
import numpy as np
import pandas as pd
from datetime import date
dates=pd.date_range('20241025',periods=200)
print(dates)
print("透過numpy產生200筆資料")
se=pd.Series(np.arange(1,201),index = dates)
print(se)
se.to_csv('se.csv')

print("計算這200筆資料整合")
se_1 = se.sum()
print(se_1)

print("計算每個月資料整合")
se_2 = se.resample('M').sum()
print(se_2)

print("計算每一季資料整合")
se_3 = se.resample('Q').sum()
print(se_3)
============================================================
print("想要以月為單位呈現每個月月底的那一筆資料")
se_2 = se.asfreq('M')
print(se_2)

print("想要以季為單位呈現每一季的最後一天資料")
se_2 = se.asfreq('Q')
print(se_2)
============================================================
# error
import pandas as pd
from  datetime import  date
import  numpy as np
se2=pd.read_csv(
    'se2.csv',
    index_col='Date',names=['Date','num'])
print(se2.index)
print(type(se2.index[0]))
print(se2.__class__)
print('顯示資料類型')
print(se2.dtypes)
print(se2)
print('計算每個月資料總和，為什麼異常?')
se2M=se2.resample('M').sum()
print(se2M)
============================================================
### 丟棄遺失值
您可以使用 dropna 方法再搭配 axis 參數方式進行搭配。
默認情況下，預設為 axis = 0，也就是會沿著 Rows 進行，當發現到任何值為 NA 就會整個 Row 刪除。
若加入參數 how=‘all’ 代表整個 Row 資料都是遺失值情況下才可以刪除丟棄。
加入參數 thresh=N 代表刪除包含少於 N 個觀察值的 row。

import numpy as np
import pandas as pd
from io import StringIO
csv_data = '''
A,B,C,D
1.0,2.0,3.5,4.0
5.5,34,3.4
10,,11.5,8.5
'''
data1=pd.read_csv(StringIO(csv_data))
print(data1)
============================================================
import pandas as pd
import numpy as np
df = pd.read_csv('./2017.csv',encoding='utf-8-sig')
print(df)
print("將資料轉成HTML，以便查看")
html = df.to_html()
with open('work1.html','w',encoding='utf-8') as file:
    file.writelines('<meta charset="utf-8">\n')
    file.write(html)
df=df.replace('—',np.NaN)
df=df.replace('…',np.NaN)
print(df.info())
html = df.to_html()
with open('work2.html','w',encoding='utf-8') as file:
    file.writelines('<meta charset="utf-8">\n')
    file.write(html)
============================================================
import numpy as np
import pandas as pd
from io import StringIO
csv_data = '''
A,B,C,D
1.0,2.0,x,4.0
5.5,34,3.4,x
10,x,11.5,8.5
'''
data3=pd.read_csv(StringIO(csv_data))
print(data3)
print(data3.info())
print("count:",data3.count())
print('='*50)

data3 = data3.replace('x',np.NaN)
print(data3)
print(data3.info())
print("count:",data3.count()) # NaN不算count
============================================================
import numpy as np
import pandas as pd
from io import StringIO
csv_data = '''
A,B,C,D
1.0,2.0,x,4.0
5.5,34,3.4,x
10,x,11.5,8.5
'''
data3=pd.read_csv(StringIO(csv_data))
print(data3)
print(data3.info())
print("count:",data3.count())
print('='*50)

data3 = data3.replace('x',np.NaN)
print(data3)
print(data3.info())
print("count:",data3.count()) # NaN不算count

print(data3.isnull())
print(data3.isnull().any()) # 欄位是否有NaN
print(data3.isnull().sum()) # 欄位NaN的數量
============================================================
import numpy as np
import pandas as pd
from io import StringIO
csv_data = '''
A,B,C,D
1.0,2.0,x,4.0
5.5,34,3.4,x
10,x,11.5,8.5
'''
data3=pd.read_csv(StringIO(csv_data))
print(data3)
print(data3.info())
print("count:",data3.count())
print('='*50)

data3 = data3.replace('x',np.NaN)
print(data3)
print(data3.info())
print("count:",data3.count()) # NaN不算count

print(data3.isnull())
print(data3.isnull().any()) # 欄位是否有NaN
print(data3.isnull().sum()) # 欄位NaN的數量

print("="*50)
print(data3)
print("type:",type(data3.loc[1,"A"]))
print("type:",type(data3.loc[0,"B"]))
print("type:",data3.loc[0,"B"])
print("="*50)
print("mean:")
print(data3.mean())
============================================================
import numpy as np
import pandas as pd
from io import StringIO
csv_data = '''
A,B,C,D
1.0,2.0,x,4.0
5.5,34,3.4,x
10,x,11.5,8.5
'''
data3=pd.read_csv(StringIO(csv_data))
print(data3)
data3 = data3.replace('x',np.NaN)
print(data3)
print("="*50)

for x in data3:
    print(f"x:{x}: data3:{data3[x]}")
    if data3[x].dtype == 'object':
        data3[x]=data3[x].astype('float64')
print("mean:")
print(data3.mean())
print(data3.count())
print(data3.isnull().any())
print(data3.isnull().sum())

import pandas as pd
import  numpy as np
from io import  StringIO
csv_data='''
A,B,C,D,E
2,3,4,5,
6,34,6,
10,,11,8,
,,,
3,,3,,
,5,,,
'''
drop=pd.read_csv(StringIO(csv_data))
print(drop)

print('沿著row進行刪除，只要有遺失值就刪除')
drop1=drop.dropna(axis=0)#只要一個Row是Nan就移除
print(drop1)
print('='*50)

print('沿著column進行刪除，只要有遺失值就刪除')
drop2=drop.dropna(axis=1)#因為每一欄都有NaN所以沒資料
print(drop2)
print('='*50)

drop3=drop.dropna(axis=0,how='all')# 所有都是Nan才移除
print(drop3)
============================================================
import pandas as pd
import  numpy as np
from io import  StringIO
csv_data='''
A,B,C,D,E
2,3,4,5,
6,34,6,
10,,11,8,
,,,
3,,3,,
,5,,,
'''
drop=pd.read_csv(StringIO(csv_data))
print(drop)
print("="*50)

drop4=drop.dropna(thresh=3)#非缺失值(有數值的)<thresh移除
print(drop4)
print("="*50)

drop5=drop.dropna(subset=['C','D'])# c跟d欄位都不是NaN的顯示
print(drop5)
print("="*50)

drop.dropna(thresh=2,inplace=True)# inplace=True可修改drop 非缺失值<thresh移除
print(drop)
============================================================
import pandas as pd
import  numpy as np
from io import  StringIO
csv_data='''
A,B,C,D,E
2,3,4,5,
6,34,6,
10,,11,8,
,,,
3,,3,,
,5,,,
'''
fill=pd.read_csv(StringIO(csv_data))
print(fill)
fill_zero = fill.fillna(0)  #Nan都填上0
print(fill_zero)

print("-------2--------")
fill_zero = fill.fillna(0,limit=2) #只填上2個0
print(fill_zero)

print("-------3--------")
fill2=fill.ffill()# 如果當前欄位是NaN  向上一筆同欄直到非NaN的值 寫入目前欄位
print(fill2)

print("-------4--------")
fill3=fill.bfill()# 如果當前欄位是NaN  向下一筆同欄直到非NaN的值 寫入目前欄位
print(fill3)
============================================================
import pandas as pd
import  numpy as np
from io import  StringIO
csv_data='''
A,B,C,D,E
2,3,4,5,
6,34,6,
10,,11,8,
,,,
3,,3,,
,5,,,
'''
fill=pd.read_csv(StringIO(csv_data))
print(fill)
fillmean1=fill.mean()
print(fillmean1)
print("="*50)
for x in fill:
    fill[x].fillna(fillmean1.loc[x],inplace=True)#填上平均值
print(fill)
print("="*50)
============================================================
import pandas as pd
import  numpy as np
from io import  StringIO
csv_data='''
A,B,C,D
2,3,5,5
5,5,5,5
5,5,5,5
13,23,5,5
'''
df2=pd.read_csv(StringIO(csv_data))
print(df2)
print("-------0---------")
print(df2.duplicated()) #因為index 2的row 5 5 5 與 index 1的row 5 5 5 一模一樣所以重複
print("-------1---------")
print(df2.duplicated('A'))# 單獨查A欄的數值是否重複
print("-------2---------")
print(df2.duplicated('D'))# 單獨查D欄的數值是否重複
print("-------3---------")
============================================================
import pandas as pd
import  numpy as np
from io import  StringIO
csv_data='''
A,B,C,D
2,3,5,5
5,5,5,5
5,5,5,5
13,23,5,5
'''
df2=pd.read_csv(StringIO(csv_data))
print(df2)
print("-------0---------")
print(df2.drop_duplicates(keep='last'))#保留最後一個重複的
print("-------1---------")
print(df2.drop_duplicates(keep=False))#不保留
print("-------2---------")
print(df2.drop_duplicates(subset=['C','D']))#因為C D 重頭到尾都重複 所以 只留index :0的資料
print("-------3---------")
print(df2.drop_duplicates(subset=['C','D'],keep='last'))#因為C D 重頭到尾都重複 keep 為 last 所以 只留index :3
print("-------4---------")
print(df2.drop_duplicates(subset=['C','D'],keep=False))#因為C D 重頭到尾都重複 keep 為 False都不留 所以空
print("-------5---------")
print(df2.drop_duplicates(subset=['A','D'],keep=False))
print("-------6---------")
print(df2.drop_duplicates(subset=['B']))#保留第一個
============================================================
### Pand群組

import pandas as pd
import numpy as np
company=["A","B","C"]
data1=pd.DataFrame(
{"company":[company[x] for x in np.random.randint(0,len(company),20)],
"salary":np.random.randint(5,50,20),
"age":np.random.randint(15,50,20)}    
)
print(data1)
============================================================
group = data1.groupby("company")
print(group)
print(list(group))
============================================================
group = data1.groupby("company")
print(group)
print(list(group))
k,v = list(group)[0]
print(k,type(v))
print(list(group))
print(group.size())
print(group.first())
print(group.last())
============================================================
import pandas as pd
fortune = pd.read_csv("fortune1000.csv",index_col='Rank',encoding="utf-8")
print(fortune)
print("="*100)
sectors = fortune.groupby("Sector")#部門
print(sectors.size())
============================================================
print(sectors.get_group('Energy').head(5))
print("="*100)
print(sectors.get_group('Energy').max())
print("="*100)
print(sectors.get_group('Energy').min())
============================================================
print(sectors.sum(numeric_only=True))
print()
print(sectors.mean(numeric_only=True))
print()
============================================================
print(sectors.agg({"Revenue":["size","sum","mean"],"Employees":"mean"}))
============================================================
import pandas as pd
auto_price=pd.read_csv('Automobile.csv') #看一下Automobile.csv 哪些是?
print(auto_price.head())
print('了解欄位名稱，-容易有被誤判的風險')
print(auto_price.columns)
print('儲存欄位名稱')
============================================================
print('查看資料內是否有遺失值')
print(auto_price.isnull().any())
print('查看每個欄位的資料型態')
print(auto_price.dtypes)
============================================================
import numpy as np
print('查看哪些欄位有？')
list1=[]
for col in auto_price:
    for filed1 in auto_price[col]:
          if filed1=='?':
                list1.append(col)      
print(list1)
print(len(list1))
print('太多資料重複，希望資料不要重複出現，我們將資料轉換為set型態')
set1=set(list1)
print(set1)
print(len(set1))
list2=list(set1)
============================================================
for column in list2:
    #print(auto_price[column] == "?")
    auto_price.loc[auto_price[column] == "?",column] = np.NaN
print(auto_price.isnull().any())
print(auto_price.dtypes)
============================================================
print('刪除之前資料的形狀')
print(auto_price.shape)
#print(type(auto_price.isnull()) )
print(auto_price.isnull().sum())
try:    
    auto_price.drop(["normalized-losses"],axis=1,inplace = True)
except:
    pass
print(auto_price.isnull().sum())
============================================================
auto_price.dropna(axis=0,inplace=True)
print(auto_price.isnull().sum())
============================================================
list3 = []
for i in auto_price.columns:
    
    if auto_price[i].dtype == object:
        try:
            auto_price[i] = auto_price[i].astype('float')
            list3.append(i)
        except:
            pass
print("轉換為float的欄位:")        
print(list3)  
============================================================
print('描述數值型態資料')
print(auto_price.describe( ))
print('描述字串型態資料')
print(auto_price.describe(include=['object']))