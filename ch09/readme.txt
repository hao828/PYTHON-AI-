Python與AI人工智慧開發入門-17：https://youtu.be/njQb8yURsyA
Python與AI人工智慧開發入門-18：https://youtu.be/vp6JJgXPwtE

import numpy as np
x = np.empty((2,4))
print(x)
print("="*20)
x = np.zeros((2,4))
print(x)
==================================================
import numpy as np
x = np.ones((2,4))
print(x)
print(x*5)
print("="*20)
x = np.full((2,4),6)
print(x)
print("="*20)
==================================================
import numpy as np
x = np.eye(3) # 單位矩陣
print(x)
print("="*20)
x = np.diag([1,2,3,4])
print(x)
==================================================
### linspace arange
import numpy as np
x = np.linspace(1,10,6) #1~10分成6等分 #包含10
print(x)
==================================================
### reshape
import numpy as np
x = np.linspace(1,10,6)
print(x)
print("="*20)

print(x.reshape(3,2))
print(x.reshape(2,3))
==================================================
### arange
import numpy as np
r1 = np.arange(25,30,0.5)#不包含30
print("r1 => ",r1)
print(type(r1))
==================================================
### 陣列指定位置取值
間隔選取 [::c]
以 1 維陣列來說明 x[a:b:c]
a：選取資料的起始索引
b：選取資料的結束索引 +1
c：選取資料間隔，以索引值可以被此值整除的元素，不指定表示 1
倒序 [::-1]
### 只是單純的把順序反過來
陣列指定位置-給予一個整數
關於指定位置 [row,column]
假設給予一個整數為 N
如果是給固定的 N，那就代表 row 或 column 等於 N。
如果是 N：，那就代表 row 或 column 大於等於 N 的區域。
如果是：N，那就代表 row 或 column 小於 N 的區域。
如果是：，那就代表 row 或 column 是任意欄位。

import numpy as np
a = np.arange(1,10).reshape((3,3))
print(a)
print(a[0])
print(a[2][2])
print(a[1][2])
==================================================
import numpy as np
a = np.arange(1,10).reshape((3,3))
print(a)
print(a[1,1:3])
print("="*100)
print(a[:,1])
==================================================
import numpy as np
a = np.arange(1,10).reshape((3,3))
print(a)
print(a[1,1:3])
print("="*100)
print(a[:,1])
print("="*100)
a[1,2] = 75
print(a)
print("="*100)
a[:,0] = [100,101,102]
print(a)
==================================================
### 重設新陣列
resize 這個動作會依據原本的陣列再設定指定大小的新陣列。
resize 動作的參數如下：
numpy.resize(arr1，shape1)
arr1：原本的陣列
shape1：新規劃的大小
如果規劃的新陣列比較大，將會重新複製原有陣列的資料，填滿新的儲存格。
resize 這個動作建立新的陣列，而 reshape 則是依據原有的重新規劃，仍會受到原有陣列影響。
transpose()轉置

import numpy as np
a = np.array([[1,2,3],
             [4,5,6]])
print(a.shape)
print()

b = a.reshape(3,2) # 會改變:表示共用資料 優點:效率高 缺點:資料共用相互影響
print(b)
print(b.shape)
print()

a[0,1] = 100
print(a)
print(b)
print(b.shape)
print(a.shape)
==================================================
### resize
import numpy as np
a = np.array([[1,2,3],
             [4,5,6]])
print(a)
print(a.shape)
print()

b = np.resize(a,(3,2))#資料內容會複製一份
print(b)
print(b.shape)
print()

a[0,1] = 100
print(a)
print(a.shape)
print(b)#不會改變
print(b.shape)
print()

b = np.resize(a,(10,10)) #resize 大於原本size #超過原有size會自動重複輸出擴充
print(b)
==================================================
### 總和最大與最小
np.sum( ) 代表某一個陣列內容的總和，也可以指定這個陣列的哪一軸 (axis) 內容總和。
np.min( ) 代表某一個陣列內容的最小值，也可以指定這個陣列的哪一軸 (axis) 內容的最小值。
np.max( ) 代表某一個陣列內容的最大值，也可以指定這個陣列的哪一軸 (axis) 內容的最大值。
amin 與 min 是相同功能的方法。
amax 與 max 是相同功能的方法。
==================================================
### 總和sum()
import numpy as np
a = np.array([[0,30,45],
            [60,75,90]])
print(a)
print()

b = np.sum(a) # 沒有指定軸 每個元素相加
print(b)
print()

b = np.sum(a,axis=0) #軸0(row)的陣列相加
print(b) # 0+60 30+75 45+90
print()

b = np.sum(a,axis=1) #軸1(colum)的陣列相加
print(b) # 0+30+75 60+75+90
print()
==================================================
### max() min()
import numpy as np
a= np.array([[0,75,45],
            [60,30,90]])
print(a)
print()

b = np.max(a)
bi = np.argmax(a) #索引直
print(b)
print(bi)
print()

b = np.max(a,axis=0) #拿每個row的陣列找出最大值
bi = np.argmax(a,axis=0) #拿每個row的陣列找出最大值的索引值
print(b)
print(bi)
print()

b = np.max(a,axis=1)
bi = np.argmax(a,axis=1)
print(b)
print(bi)
print()
==================================================
### 中位數與平均
median( ) 方法可取出陣列或陣列中指定的軸之中位數。
把所有值高低排序後找出正中間的一個作爲中位數。如果資料數量為偶數，則中位數取最中間的兩個數值的平均數。
參數：
array：陣列
axis：軸
mean( ) 方法可取出陣列或陣列中指定的軸之平均數。
平均值就是把陣列或指定軸的所有資料除以數量後的數值。
參數：
array：陣列
axis：軸
average( ) 方法與 mean( ) 方法相似，但可以加入權重進行計算。
計算公式為 ((資料*權重)相加)/(權重相加)
參數：
array：陣列
axis：軸
weights：權重，若沒有則設定為 1
returned：若設定為 true，代表返回計算結果跟權重相加總合兩筆資料，若沒有設定或設定 false 則只有計算結果
沒有指定權重時與一般平均值相同。
加權平均值是由每個資料乘以權重以反映加上重要性因素後產生的平均值。
average( ) 使用時若沒有指定軸，則陣列將被平坦化。
假設有個陣列資料為 [1,2,3,4]，相應的權重 [40,30,20,10]，加權平均數是這樣： (1x40+2x30+3x20+4x10)/(40+30+20+10)

import numpy as np
a = np.array([[0,30,45],
             [60,75,90]])
print(a)
print()

b = np.mean(a) #平均值
print(b)
print()

b = np.mean(a,axis=0) #軸0的平均值
print(b)
print()

b = np.mean(a,axis=1) #軸1的平均值
print(b)
print()

==================================================
import numpy as np
a = np.array([1,2,3,4])
b = np.average(a)
print(a)
print(b)
print()

wts = np.array([4,3,2,1])
b = np.average(a,weights = wts)
#(1*4+2*3+3*2+4*1)/(4+3+2+1)  = 20/10  = 2
print(b)
print()

b = np.average([1,2,3,4],weights = [4,3,2,1],returned = True)
#(1*4+2*3+3*2+4*1)/(4+3+2+1)  = 20/10  = 2
print(b)
==================================================
### 中位數
import numpy as np
a = np.array([[0,30,45],
             [60,75,90]])
print(a)
print()

b = np.median(a) #6/2=3 取3.4編號的數字:45、60 (45+60)/2 = 52.5
print(b)
print()

b = np.median(a,axis=0)
print(b)
print()

b = np.median(a,axis=1)
print(b)
print()
==================================================
### 變異數與標準差
變異數代表所有資料到平均數的距離之平方。

標準差代表變異數開平方根，也就是可依此表示資料的分散程度。

var( ) 代表由陣列取得變異數的方法。

std( ) 代表由陣列取得標準差的方法。

定義：

變異數代表((每一個資料-平均值)平方後的加總結果)/總個數。

標準差是變異數的開根號結果。

import numpy as np
a= np.array([1,2,3,4])
print(a)
print()

b = np.var(a) #變異數
print("var: ",b)
print()

b = np.std(a) #標準差
print("std: ",b)
print()
==================================================
### 範圍與百分位數
np.ptp( ) 計算最大與最小值的差（最大 -(減) 最小）。
np.percentile( ) 方法代表百分位數，用於統計數據的度量指標，需要三個參數：
array：陣列。
percent：計算的百分位數，介於 0 到 100 之間。
axis：進行計算的軸。
百分位數是一種位置量數，有助於瞭解資料在最小值與最大值之間的分布情況。
p- 百分位數表示：
至少有 p-百分比 (p%) 的觀察值小於或者等於他。
至少有 (100-p)% 的觀察值大於或等於他。
計算方式：
將資料由小到大排序。
計算 i=(p%*樣本數) 之位置。
於 i 位置：
a. 若不是整數，無條件進位取比 i 大的下一個整數位置的值。
b. 若為整數，則由 i 與 i+1 兩個位置上的值取平均。

import numpy as np
a = np.array([[0,30,45],
             [60,75,90]])
print(a)
print()

print(np.ptp(a)) #90-0
print()

b = np.ptp(a,axis=0) #[60-0,75-30,90-45]
print(b)
print()

b = np.ptp(a,axis=1) #[45-0,90-60]
print(b)
print()
==================================================
import numpy as np
array = np.array([4,6,10,12,8])
# 位置                      1 2 3  4  5 
# 注意percentile會在內部排序 4 6 8 10 12
# n是長度
# 位置index = 1+(n-1)*p 
# n是全部元素的數量 p是百分比 
#以下案例是:n=5 p=50%
"""
先算出位置:
index 第一個是 1所以計算+是最左邊的位置 
(5-1)*0.5 = 2 :計算由最左邊位置右移多少到估算的百分比
1+(5-1)*0.5 = 3
正好落在 index為3的位置 答案是8
"""
b = np.percentile(array,50)
print("The percentile is:",b)
==================================================
import numpy as np
a = np.array([[11,8,9],
             [5,4,1]])

# n=6 p=25
# 位置    1 2 3 4 5
# 排序後  1 4 5 8 9
"""
1+(6-1)*0.25 = 2.25
2.25 : 位置2~3之間的數值
因為沒有若在點上，所以由計算好的點往下移動
2.25取出小數部分為0.25，故接下來需乘0.25
計算好的點位置為2，數字為4 所以
位置3數字為5
位置2數字為4
4+(5-4)*0.25 = 4.25
"""
b = np.percentile(a, 25)
print("The percentile is:",b)
==================================================
### 累加與累差
np.cumsum( ) 方法進行指定軸資料的累加。
參數：
array：陣列
axis：軸，沒有指定軸則會平坦化後進行累加
維持原有的資料數量，且在計算結果上進行下一個計算。
np.diff( ) 方法進行指定軸資料的累差。
參數：
array：陣列
axis：軸，沒有指定軸預設 axis 為 1
以原資料進行資料內容刪除，若 axis 為 0 則減少一個 row，若 axis 為 1 減少一個 column。

import numpy as np
a = np.array([[1,2,3],
             [13,6,9],
             [12,24,36]])
print(a)
print()
print(np.cumsum(a))
print()
print(np.cumsum(a,axis=0))
print()
print(np.cumsum(a,axis=1))
==================================================
import numpy as np
a = np.array([[1,2,3],
             [13,6,9]])
print(a)
print(np.diff(a)) #預設axis = 1
print()

print(np.diff(a,axis=0)) #[13-1,6-2,9-3]
print()

print(np.diff(a,axis=1)) #[2-1,3-2]
                         #[6-13,9-6]
print()
==================================================
### 平均中位標準差! 請查看男女生遲到天數，要如何進行分析?
import numpy as np
girl = np.array([8,10,15,20,27,29,29,30,30,162])
boy=np.array([34,34,35,35,36,36,36,37,38,39])
girlMean = np.mean(girl)
print("girl Mean: ",girlMean)
boyMean = np.mean(boy)
print("boy Mean: ",boyMean)
print()

girlMedian = np.median(girl)
print("girl Median: ",girlMedian)
boyMedian = np.median(boy)
print("boy Median: ",boyMedian)
print()

girlStd = np.std(girl)
print("girl Std: ",girlStd)
boyStd = np.std(boy)
print("boy Std: ",boyStd)
==================================================
### 圖表
figure 可加入參數
plt.figure( ) 方法會建立一個圖像，該代碼後的所有圖像會繪製到這個圖像中，一個項目中可以添加多個 figure，常用參數如下：
num：設置圖像的序號，不設置該參數，自動默認編號。
figsize：設置圖像大小。
facecolor：圖像前景色

import matplotlib.pyplot as plt
data = [-1, -4.3, 15, 21, 31]
plt.figure(figsize=(8, 5))
plt.plot(data) 
plt.show()
==================================================
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0,10,100)
# 創建第1個圖形，編號為1
plt.figure(num=1,figsize=(8,5))
plt.plot(x,np.sin(x))

# 創建第2個圖形，編號為2
plt.figure(num=2,figsize=(8,5))
plt.plot(x,np.cos(x))

# 再次選擇第一個圖形，編號為 1，並添加新的曲線
plt.figure(num=1)
plt.plot(x,np.cos(x))

# 顯示所有圖形
plt.show()
==================================================
# https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.plot.html
import matplotlib.pyplot as plt
import numpy as np
y1=[1,2,5,6,7,5,9,15]
y2=[4,5,6,7,8,11,20,5]

a = len(y1)+1
x = np.arange(1,a)
plt.figure(figsize=(8,5))
plt.plot(x,y1,'r-o') #劃出樣式
plt.plot(x,y2,'g--')
plt.xticks([1,3,5,7],('1','3','5','7')) #x軸的項目名稱
plt.grid() #劃出格線
plt.show()
==================================================
### 子圖表
一個 Figure 對象可以包含多個子圖 (Axes)，預設三個參數：
num_rows：幾個 rows。
num_cols：幾個 columns。
plot_num：代表第幾張圖表。
然後按照從左到右，從上到下的順序對每個子區域進行編號，左上的子區域的編號為 1。
Plot_num 參數指定創建的 Axes 對象所在的區域。
如果 numRows ＝ 2、numCols ＝ 3，那整個繪製圖表樣式為 2×3 的圖片區域,用坐標表示為
(1, 1), (1, 2), (1, 3)
(2, 1), (2, 2), (2, 3)
當 plotNum ＝ 3 時,表示的坐標為 (1, 3)，即第一 row 第三 column 的子圖。
如果 numRows、numCols 和 plotNum 這三個數都小於 10 的話，可以把它們縮寫為一個整數，例如 subplot(232) 和 subplot(2,3,2) 是相同的。

import matplotlib.pyplot as plt
import numpy as np
t = np.arange(0.0,20.0,1)
s = np.linspace(0,10,20)
# 由左往右數第幾張
plt.subplot(2,2,1) #產生2X2的圖表 第1張圖
plt.plot(t,s)
plt.subplot(2,2,2) #產生2X2的圖表 第1張圖
plt.plot(t,s,'r--')
plt.subplot(2,2,3) #產生2X2的圖表 第3張圖
plt.plot(t,s**2,'g-*')
==================================================
import matplotlib.pyplot as plt
import numpy as np
x = np.linspace(-np.pi,np.pi,256) #-pi~pi 間隔取256
y = np.cos(x)

plt.figure(figsize=(8,8)) #產生8*8的圖

plt.subplot(2,2,1) #產生2X2的圖表 第1張圖
plt.plot(x, y, color="blue") #線的顏色為'藍色'
plt.title('subplot(2,2,1)') #圖表標題為'subplot(2,2,1)'

plt.subplot(2,2,2)
plt.plot(x, y*-1, color="red")
plt.title('subplot(2,2,2)')

plt.subplot(2,2,(3,4)) #產生2X2的圖表 第3+4張圖
plt.plot(x, y*-1, color="green")
plt.plot(x, y, color="black")
plt.title('subplot(2,2,(3,4))')

plt.show( )
==================================================
### 垂直線
plt.axvline(X軸資料,位置起點,位置終點,其他參數)

這兩個方法的第二個與第三個參數其實是指圖表中的位置比例。

第二個位置預設為0，代表位置的起點。

第三個位置預設為1，代表位置的終點。

### 水平線
plt.axhline(Y軸資料,位置起點,位置終點,其他參數)
import matplotlib.pyplot as plt
import numpy as np
x = np.linspace(10,50,50)
y1 = np.power(x,2)+30*x-11
y2 = np.power(x,2)-3*x-11
plt.plot(x,y2,linewidth=0.5,linestyle='--')
plt.plot(x,y1,color='red',linewidth=3.0,linestyle=':')
plt.axvline(30,0.8,0.2,color='blue')
plt.axhline(30,0.5,1,color='green')
plt.show()
==================================================	
# ERROR
import  matplotlib.pyplot as plt
import  numpy as np
x=np.linspace(10,50,50)
y1=-np.power(x,2)+30*x-11
y2=np.power(x,2)-3*x-11
plt.plot(x,y2,linewidth=0.5,linestyle='--')
plt.plot(x,y1,color='red',linewidth=3.0,linestyle=':')
plt.axvline(30,0.8,0.5,color='blue')
plt.axhline(500,0.8,0.5,color='red')
plt.title('Title標題')
plt.xlabel('xlabel水平')
plt.ylabel('ylabel垂直')
plt.show()
==================================================	
import matplotlib.font_manager as fm
path = r'.\NotoSerifCJKtc-Medium.otf'
fontprop = fm.FontProperties(fname=path, size=13)

import  matplotlib.pyplot as plt
import  numpy as np
plt.figure(figsize=(8,5))
x=np.linspace(-10,10,50)
y1=2*x+1
y2=x**2-3*x-11
plt.plot(x,y2)
plt.plot(x,y1,color='red',linewidth=2.0,linestyle='dashdot')
plt.grid()
plt.title('中文',fontproperties=fontprop)
plt.xlabel('水平x',fontproperties=fontprop)
plt.ylabel('垂直y',fontproperties=fontprop)
plt.show()
==================================================
Bar 與 Stacked Bar

Bar 長條圖：可以垂直或水平繪製

Stacked 堆疊長條圖：多項資料的數據一一堆疊，可顯示每一長條的相對組成。

matplotlib.pyplot.bar(x, height, width=0.8, bottom=None, *, align='center', data=None, **kwargs)

https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.bar.html


import matplotlib.pyplot as plt
import numpy as np
city = ['Delhi', 'Beijing', 'Washington', 'Tokyo', 'Moscow']
pos = np.arange(len(city))
Happiness_Index = [60, 40, 70, 65, 85]
plt.bar(pos, Happiness_Index, color='blue', edgecolor='black')
plt.xticks(pos, city)
plt.xlabel('City', fontsize=16)
plt.ylabel('Index', fontsize=16)
plt.title('Barchart ', fontsize=20)
plt.show( )
==================================================
分析與圖表顯示 5- 堆疊長條圖調整
圖例於視覺上造成阻礙。
堆疊長條圖顯示方式略作調整。
loc編號 |功能 |編號| |-------------|-----| |最好(右上)預設| 0 | |右上方 | 1 | |左上 | 2| |左下角 | 3| |右下 | 4| |對 | 5| |中左 | 6| |中右 | 7| |下中心 | 8| |上中 | 9| |中央 | 10|

import  matplotlib.pyplot as plt
import  numpy as np
city=['Delphi','Beijing','Washington','Tokyo','Moscow']
pos=np.arange(len(city))
gender=['Male','Female']
happing_index_male=[60,40,70,65,85]
happing_index_female=[30,60,70,55,75]
plt.bar(pos,happing_index_male,color='blue')
plt.bar(pos,happing_index_female,color='pink')
plt.xticks(pos,city) 
plt.xlabel('capital')
plt.ylabel('index',rotation=0)
plt.legend(gender,loc=2)#小圖示
plt.title('barchart')
plt.show()
==================================================
import  matplotlib.pyplot as plt
import  numpy as np
city=['Delphi','Beijing','Washington','Tokyo','Moscow']
pos=np.arange(len(city))
gender=['Male','Female']
happing_index_male=[60,40,70,65,85]
happing_index_female=[30,60,70,55,75]
#bottom=happing_index_female由happing_index_femaled開始畫
plt.bar(pos,happing_index_male,color='blue',bottom=happing_index_female)
plt.bar(pos,happing_index_female,color='pink')
plt.xticks(pos,city) 
plt.xlabel('capital')
plt.ylabel('index',rotation=0)
plt.legend(gender,loc=2)
plt.title('barchart')
plt.show()
==================================================
import numpy as np
import matplotlib.pyplot as mp
city = ['A','B','C','D','E']
pos = np.arange(len(city))
bar_width= 0.35
gender = ['M','F']
happing_index_male=[60,40,70,65,85]
happing_index_female=[30,60,70,55,75]
plt.bar(pos,happing_index_male,bar_width,color='blue')
plt.bar(pos+bar_width,happing_index_female,bar_width,color='pink')#在旁邊
plt.xticks(pos,city) 
plt.xlabel('capital')
plt.ylabel('index',rotation=0)
plt.legend(gender,loc=1) 
plt.title('barchart',x=0.4,y=1.1)
plt.show()
==================================================
### 散佈圖 Scatter
import matplotlib.pyplot as plt
import numpy as np
h=np.array([159,169,174,165,163,155,180,190])
w=np.array([55,45,70,60,65,45,72,50])
print("身高的平均:",np.mean(h))
print("身高的中位:",np.median(h))
print("體重的平均:",np.mean(w))
print("體重的中位:",np.median(w))
#'散佈圖
plt.scatter(h,w)
plt.show()
==================================================
import matplotlib.pyplot as plt
import numpy as np
h=np.array([159,169,174,165,163,155,180,190])
w=np.array([55,45,70,60,65,45,72,50])
print(h)
print(w)
plt.scatter(h,w)
plt.xlabel('h')
plt.ylabel('w')
#plt.text(160,60,'test1',fontsize=20)
for temp1 in zip(h,w):
  print(temp1)
  plt.text(temp1[0],temp1[1],temp1,fontsize=10)
plt.grid()
plt.show()
==================================================
### Hist 直方圖：顯示資料頻率或著數值資料各類別範圍中的資料。
import  numpy as np
import  matplotlib.pyplot as plt
values = [82, 76, 24, 40, 67, 62, 75, 78, 71, 32, 98, 89, 78, 67, 72, 82, 87, 66, 56, 52]
print(len(values))
x1=np.arange(len(values))
plt.bar(x1,values)
plt.show()
plt.hist(values,bins=5)#bins分5個
plt.show()
==================================================
### 圓餅
import matplotlib.pyplot as plt
import numpy as np
values=[60,80,90,55,10,30]
colors=['b','g','r','c','m','y']
labels=['US','UK','India','Germany','Australia','South Korea']
explode=(0.1,0,0,0,0,0)
plt.pie(values)
plt.show()
print('上面看不出來誰是誰')
plt.pie(values,labels=labels)#加上文字
plt.show()
print('美國部份希望突出')
plt.pie(values,labels=labels,explode=explode)
plt.show()
==================================================
import matplotlib.pyplot as plt
import numpy as np
values=[60,80,90,55,10,30]
narray = np.array(values)
colors=['b','g','r','c','m','y']
labels=['US','UK','India','Germany','Australia','South Korea']
print('label希望呈現國家與數值')
labels2=[]
for temp1 in zip(labels,values):
  data1=str(temp1[0])+':'+str(temp1[1])
  labels2.append(data1)
#print(labels2)
plt.pie(values,labels=labels2)
plt.show()
==================================================
import matplotlib.pyplot as plt
values = [60, 80, 90, 55, 10, 30]
colors = ['b', 'g', 'r', 'c', 'm', 'y']
labels = ['US', 'UK', 'India', 'Germany', 'Australia', 'South Korea']
explode = (0.2, 0, 0, 0, 0, 0)
#逆時鐘counterclock
plt.pie(values, colors=colors, labels=values, explode=explode, counterclock=True, shadow=True)
plt.title('Population Density Index')
plt.legend(labels, loc=8)
plt.show( )
==================================================
### 箱型圖
import matplotlib.pyplot as plt
value1 = [82, 76, 24, 40, 67, 62, 75, 78, 71, 32, 98, 89, 78, 67, 72, 82, 87, 66, 56, 52]
d1 = plt.boxplot(value1,whis=1.5)
plt.show()
==================================================
## pandas
import numpy as np
name = np.array(['A','B','C'])
age = np.array([18,25,40])
print(type(age))
==================================================
import pandas as pd
import numpy as np
fruits  = ['蘋果','橘子','梨子','櫻桃']
quantities = [15,33,45,55]
n1 = np.array(quantities)
s1 = pd.Series(quantities)
s2 = pd.Series(quantities,index=fruits)
print(n1)
print("-"*70)
print(s1)
print("-"*70)
print(s2)
print("-"*70)
print(s2.index)
print("-"*70)
print(s2[1])
print("-"*70)
print(s2["梨子"])
==================================================
import  pandas as pd
fruits=['蘋果','橘子','梨子','櫻桃']
quantities=[15,33,45,55]
s1=pd.Series(quantities)
s2=pd.Series(quantities,index=fruits)
print(s1);print('-'*70)
print(s2);print('-'*70)
print(s1.median())
print(s1.mean())
print(s1.min())
print(s1.max());print('-'*70)
print(s1.describe())#輸出一群
==================================================
import  pandas as pd
groups=['Python','Django','Sqlite','Numpy','Security','Pandas']
numbers=[59,9,19,14,6,77]
group_dict={'groups':groups,'numbers':numbers}
df=pd.DataFrame(group_dict)
print(df)
==================================================
import  pandas as pd
import  numpy as np
array1=np.array([[10,30],[20,40]])

print(array1)
df=pd.DataFrame(array1)
print(df)

print('dataframe的row與column的index')
df2=pd.DataFrame(columns=['col1','col2'],index=['row1','row2'])
print(df2)
==================================================
import  pandas as pd
import  numpy as np
array1=np.array([[10,30],[20,40]])

print(array1)
df=pd.DataFrame(array1)
print(df)

df.columns=['col1','col2']
df.index = ['row1','row2']
print(df)

print('dataframe的row與column的index')
df2=pd.DataFrame(columns=['col1','col2'],index=['row1','row2'])
print(df2)
df2.loc['row1'] =array1[0]
df2.loc['row2'] =array1[1]
print(df2)
==================================================
import numpy as np
import pandas as pd
array1 = np.array([[10, 30],[20,40]])
df = pd.DataFrame(array1)
df1 = pd.DataFrame(
    array1, columns = ["col1", "col2"])
df2 = pd.DataFrame(
    array1,
    columns = ["col1", "col2"],
    index=['row1','row2'])
np1=np.array(df);print(np1);print('-'*70)
np2=np.array(df1);print(np2);print('-'*70)
np3=np.array(df2);print(np3);print('-'*70)
==================================================
import pandas as pd
d = {'one':pd.Series([1,2,3],index=['a','b','c']),
     'two':pd.Series([1,2,3,4],index=['a','b','c','d'])}#index多一點
df1 = pd.DataFrame(d)
print(df1)
==================================================
## 合併
import pandas as pd
d = {'one':pd.Series([1,2,3],index=['a','b','c']),
     'two':pd.Series([1,2,3,4],index=['a','b','c','d'])}
df1 = pd.DataFrame(d)
df1["three"] = [10,11,12,13]
print(df1)

df2 = pd.DataFrame([[20, 21, 22],
                    [23, 24, 25],
                    [26,27, 28]], columns=['one', 'two', 'three'],index=['a','b','c'])
print(df2)

df3= pd.concat([df1,df2],ignore_index=True)
print(df3)

df3.index=['a','b','c',"d","e","f","g"]
print(df3)

df4= pd.concat([df1,df2],axis=1,ignore_index=True)
print(df4)
==================================================
## 刪除
import pandas as pd
d = {'one':pd.Series([1,2,3],index=['a','b','c']),
     'two':pd.Series([1,2,3,4],index=['a','b','c','d'])}
df1 = pd.DataFrame(d)
df1["three"] = [10,11,12,13]
print(df1)
df1.drop('one', axis=1, inplace=True)
print(df1)

df1.drop('d', axis=0, inplace=True)
print(df1)
==================================================
### panda 讀CSV
import pandas as pd
df1 = pd.read_csv('./ex1.csv')
print('輸出ex1.csv完整資訊')
print(df1)
==================================================
import pandas as pd
df1 = pd.read_csv('./ex1.csv')
print('輸出ex1.csv完整資訊')
print(df1)
print("-----")
df2= pd.read_csv('./ex1.csv',header=None)
print('輸出ex1.csv，省略抬頭那一列')
print(df2)
==================================================
import pandas as pd
df1 = pd.read_csv('./ex1.csv')
print('輸出ex1.csv完整資訊')
print(df1)
print("-----")
df2= pd.read_csv('./ex1.csv',header=None)
print('輸出ex1.csv，省略抬頭那一列')
print(df2)
print("-----")
df3= pd.read_csv('./ex1.csv',names=["A","B","C","D","E"])
print('輸出ex1.csv，column名稱變更')
print(df3)
print("-----")
==================================================
import  pandas as pd
#龘 (音踏)
#犇(音奔)
data={
    'Name':['犇','中文','龘','Ricky'],
    'Age':[28,34,29,42]
}
print(data)
df=pd.DataFrame(data)
print(df)
df.to_html('df1.html',encoding="utf-8")
df.to_csv('df1a.csv')
df.to_csv('df1b.csv',index=False)
==================================================
#安裝讀取excel的指令
!pip install xlrd
==================================================
import  pandas as pd
import  numpy as np
#龘 (音踏)  犇(音奔)
data={
    'Name':['犇','中文','龘','Ricky'],
    'Age':[28,34,29,42]
}
print(data)
df=pd.DataFrame(data)
writer=pd.ExcelWriter('df.xlsx')#輸出Excel
df.to_excel(writer,'Sheet3')
df1=pd.DataFrame(np.arange(9).reshape(3,3),
                 index=['a','c','d'],
                 columns=['One','Two','Three'])
df1.to_excel(writer,'哈囉')
writer.close()
==================================================
