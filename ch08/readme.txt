Python與AI人工智慧開發入門-15：https://youtu.be/GuXpduIRR1g
Python與AI人工智慧開發入門-16：https://youtu.be/ZCyjVH3edNE

### 作業
設計錢包總金額1000元，
如果購買商品總金額超過1000元，
會引發一個金額不足的例外OverflowError

sum=0
dic1 = {}
while True:
    item = input("消費項目")
    price = input("消費金額")   
    try:
        if  sum+ int(price) > 1000:
            raise OverflowError
        dic1[item] = price            
        sum+=int(price)   
    except OverflowError:
         print('已經超支了')
         break  

# 將JSON與CSV用檔案.ZIP檔案放在PY資料夾下

### 寫出檔案
file = open("myData.txt","w")
file.write("Hello!!")
file.close()

file = open("myData.txt","w")
file.write("KEN")
file.close()
print("完成")

file = open("myData2.txt","w")
file.write("犇這個字必須要是utf8編碼才有")
file.close()
print("完成")

file = open("myData2.txt","w",encoding="utf-8")
file.write("犇這個字必須要是utf8編碼才有")
file.close()
print("完成")

f = open("data.txt","r",encoding = "UTF-8")
msg = f.read()
print(msg)
f.close()


### CSV
CSV 格式是資料庫最常用的導入和導出格式。
資料均沒有類型，一切都是字串。
沒有字體或顏色與儲存格寬度高度的設置。
Python 語法必須加入 import csv。
讀取儲存格資料：
reader( )：依照每一列的編號 由0開始
DictReader( )
以第一列的值為每一行的名稱，第一列不是資料
也可以重新命名，但第一列必須是資料

### Read
import csv
f = open("example1.csv","r")
for row in csv.reader(f):
    print(row[0])
f.close()

import csv
f = open("example.csv","r",encoding="UTF-8")
for row in csv.DictReader(f):
    print(row["成交筆數"])
f.close()

#類別開頭都會習慣一律大寫
#函式開頭都會習慣一律小寫

###關於檔案關閉動作
檔案開啟後須進行 close( ) 方法進行關閉動作。
若檔案沒關閉會造成：
開啟的文件物件會占用系統資源。
Python 可以同時間開啟的文件數量有限制 (約 20 份文件)。
開啟文件物件的模式若為寫入 (w 或 a) 模式，一般都是暫存於緩衝區，系統閒置或文件關閉前才會進行寫入，若沒有進行 close( ) 動作可能造成文件儲存不完整。
import os
class TestFile :
    def openFile(self,filePath):
        self.handle = open(filePath,"w")
        self.handle.close()
t = TestFile()
t.openFile("test.txt")
os.remove("test.txt")
print("完成")

#error
import os
class TestFile :
    def openFile(self,filePath):
        self.handle = open(filePath,"w")
        self.handle.close()
t = TestFile()
t.openFile("test.txt")
os.remove("test.txt")
print("完成")

import os
class TestFile:
     def openFile(self,filePath):               
            with  open(filePath,"w") as f:
                f.write("Hello!")
t = TestFile()
t.openFile("test.txt")
os.remove("test.txt")
print("Success")

import csv
with  open('example1.csv','r') as f:
    for row in csv.reader(f):
        print(row[1])


### JSON
以 json.dumps( ) 函數從 Python 物件轉入 轉出JSON格式字串。
以 json.dump( )函數從 Python 物件轉入 轉出JSON 檔案中。
json資料於Python處理UTF8碼內容會產生亂碼，建議 dumps 時加入以下的參數才可以正確處理UTF8碼內容

import json
json1 = {'python':"課程",'gjun:':100,'python-class':True,'Line:':None}
print(json1)

import json
json1 = {'python':"課程",'gjun:':100,'python-class':True,'Line:':None}
print(json1)
print(type(json1))

import json
json1 = {'python':"課程",'gjun:':100,'python-class':True,'Line:':None}
print(json1)
print(type(json1))
jsonStr = json.dumps(json1)
print(jsonStr)

iimport json
json1 = {'python':"課程",'gjun:':100,'python-class':True,'Line:':None}
print(json1)
print(type(json1))
jsonStr = json.dumps(json1,ensure_ascii = False)
print(jsonStr)
print(type(jsonStr))

import json
json2 = {'python':"課程",'gjun:':100,'python-class':True,'Line:':None}
with open ("data0.json","w",encoding = "UTF-8") as outfile:
    json.dump(json2,outfile,ensure_ascii=False)

import json
data = { }
data['people'] = [ ]
data['people'].append({
    'name': 'Scott',
    'website': 'stackabuse.com',
    'from': 'Nebraska'
})
data['people'].append({
    'name': 'Larry',
    'website': 'google.com',
    'from': 'Michigan'
})
print(data)

import json
data = { }
data['people'] = [ ]
data['people'].append({
    'name': 'Scott',
    'website': 'stackabuse.com',
    'from': 'Nebraska'
})
data['people'].append({
    'name': 'Larry',
    'website': 'google.com',
    'from': 'Michigan'
})
print(data)
with open("data.json","w",encoding="UTF-8") as outfile:
    json.dump(data,outfile,ensure_ascii=False)

import json
data = { }
data['people'] = [ ]
data['people'].append({
    'name': 'Scott',
    'website': 'stackabuse.com',
    'from': 'Nebraska'
})
data['people'].append({
    'name': 'Larry',
    'website': 'google.com',
    'from': 'Michigan'
})
# indent=2 增加閱讀性
print(data)
with open("data.json","w",encoding="UTF-8") as outfile:
    json.dump(data,outfile,ensure_ascii=False,indent=2)

### Json 轉為 Python物件
以 json.loads( ) 函數從 JSON 字串中取出資料轉入 Python。
以 json.load( ) 函數從 JSON 檔案中取出資料轉入 Python。
import json
json1 = '{"python":"good","gjun":100,"python-class":true,"ICQ":null}'
json2 = json.loads(json1)
print(json2)
print(type(json2))
print(json2["gjun"])

import json
with open ("data.json","r",encoding="UTF-8") as jsonFile:
    data = json.load(jsonFile)
    for k in data:
        print(f"{k}-{data[k]}")
---------------------------------------------------------------------
import shutil
import os
try:
    os.mkdir('test2')
    print('建立目錄')
except:
    print('建立目錄失敗')

with open('./test2/test2.txt', 'a') as file2:
    file2.write('Programming is Fun.')
    print('完成附加檔案')
    
with open('./test2/test3.txt', 'a') as file2:
    file2.write('Programiz for beginners')
    print('完成附加檔案')
    
print('查看目錄內容')
os.listdir('./test2')
---------------------------------------------------------------------
###壓縮與解壓縮
但可以於Python程式內運用，可實現以下功能：
建立zip壓縮檔案
透過zipfile.ZipFile( )建立物件，再透過物件的write()動作將資料夾壓縮。
解壓縮zip壓縮檔案
透過zipfile.ZipFile( )建立物件，再透過物件的extractall()動作解壓縮。
列出zip壓縮檔案內容
+透過zipfile.ZipFile( )建立物件，再透過物件的namelist()動作查看。
import zipfile
def create_zip(path):
  zf = zipfile.ZipFile(f'{path}.zip', 'w', zipfile.ZIP_DEFLATED)
  for root, dirs, files in os.walk(path):
    for file_name in files:
      zf.write(os.path.join(root, file_name))
def ziplist(file_path):
  zf = zipfile.ZipFile(file_path, 'r')
  print(zf.namelist())
def extra_zip(file_path):
  zf = zipfile.ZipFile(file_path, 'r')
  zf.extractall()

try:
  print('壓縮資料')
  create_zip('test2')
except:
  print('壓縮失敗')

try:
  print('查看壓縮資料')
  ziplist('test2.zip')
except:
  print('查看壓縮資料失敗')

try:
  print('刪除目錄')
  shutil.rmtree("test2")
except:
  print('刪除目錄失敗')

try:
  print('解壓縮資料')
  extra_zip('test2.zip')
except:
  print('解壓縮失敗')
---------------------------------------------------------------------
### 爬蟲
安裝套件
pip install beautifulsoup4
pip install html5lib
#使用Anaconda Prompt 輸入安裝套件

from bs4 import BeautifulSoup
---------------------------------------------------------------------
html='''<a id='a1' class="c1">V1</a>
<a id='a2' class="c1">V2</a>
<a id='a3' class="c3">V3</a>
'''
soup = BeautifulSoup(html,"html5lib")
---------------------------------------------------------------------
BeautifulSoup Base
find() 只找第一個符合條件的

https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/#find-all

find_all() 找所有符合條件的

select_one() 只找一個符合條件的可直接使用css語法

select() 找所有符合條件的可使用css語法
---------------------------------------------------------------------
html='''<a id='a1' class="c1">V1</a>
<a id='a2' class="c1">V2</a>
<a id='a3' class="c3">V3</a>
'''
soup = BeautifulSoup(html,"html5lib")
obj1 = soup.find(id='a2')
print(obj1)
---------------------------------------------------------------------
html='''<a id='a1' class="c1">V1</a>
<a id='a2' class="c1">V2</a>
<a id='a3' class="c3">V3</a>
'''
soup = BeautifulSoup(html,"html5lib")
obj1 = soup.find(id='a2')
print(obj1)
obj2 = soup.find_all(class_='c1')
print(obj2)
---------------------------------------------------------------------
from bs4 import BeautifulSoup
html='''<a id='a1' class="c1" href="https://google.com">Google</a>
<a id='a2' class="c1"  href="https://yahoo.com">Yahoo</a>
<a id='a3' class="c3" href="https://facebook.com">Facebook</a>
'''
soup = BeautifulSoup(html,"html5lib")
print(soup.find(id="a1").text)
print(soup.find(id="a1").getText())
---------------------------------------------------------------------
from bs4 import BeautifulSoup
html='''<a id='a1' class="c1" href="https://google.com">Google</a>
<a id='a2' class="c1"  href="https://yahoo.com">Yahoo</a>
<a id='a3' class="c3" href="https://facebook.com">Facebook</a>
'''
soup = BeautifulSoup(html,"html5lib")
print(soup.find(id="a1").text)
print(soup.find(id="a1").getText())
print(soup.find(id="a2").get("href"))
---------------------------------------------------------------------
from bs4 import BeautifulSoup
html='''<a id='a1' class="c1" href="https://google.com">Google</a>
<a id='a2' class="c1"  href="https://yahoo.com">Yahoo</a>
<a id='a3' class="c3" href="https://facebook.com">Facebook</a>
'''
soup = BeautifulSoup(html,"html5lib")
print(soup.find(id="a1").text)
print(soup.find(id="a1").getText())
print(soup.find(id="a2").get("href"))

tmpList = soup.find_all(class_="c1")
for tag in tmpList:
    print(tag.get("href"),tag.getText())
---------------------------------------------------------------------
#### 電影排行榜
import requests
from bs4 import BeautifulSoup
url = 'https://zh.wikipedia.org/zh-tw/2024%E5%B9%B4%E7%94%B5%E5%BD%B1'
resp = requests.get(url)
resp.encoding="UTF-8"
print(resp.text)
---------------------------------------------------------------------
import requests
from bs4 import BeautifulSoup
url = 'https://zh.wikipedia.org/zh-tw/2024%E5%B9%B4%E7%94%B5%E5%BD%B1'
resp = requests.get(url)
resp.encoding="UTF-8"

soup = BeautifulSoup(resp.text,"html5lib")
movieTable = soup.find("table",class_="wikitable sortable")
tbody = movieTable.find("tbody")
print(tbody)
---------------------------------------------------------------------
import requests
from bs4 import BeautifulSoup
url = 'https://zh.wikipedia.org/zh-tw/2024%E5%B9%B4%E7%94%B5%E5%BD%B1'
resp = requests.get(url)
resp.encoding="UTF-8"

soup = BeautifulSoup(resp.text,"html5lib")
movieTable = soup.find("table",class_="wikitable sortable")
tbody = movieTable.find("tbody")
trList = tbody.find_all("tr")
print(trList)
---------------------------------------------------------------------
import requests
from bs4 import BeautifulSoup
url = 'https://zh.wikipedia.org/zh-tw/2024%E5%B9%B4%E7%94%B5%E5%BD%B1'
resp = requests.get(url)
resp.encoding="UTF-8"

soup = BeautifulSoup(resp.text,"html5lib")
movieTable = soup.find("table",class_="wikitable sortable")
tbody = movieTable.find("tbody")
trList = tbody.find_all("tr")
for inx in range (1,len(trList)):
    print("排名:",trList[inx].find("th").text,end="")
    print("片名:",trList[inx].select_one("a").text)
    print("全球票房:",trList[inx].find_all("td")[2].text)
---------------------------------------------------------------------
### NUMPY
c1 = [1,3,5,7,9]
d1 = [3,5,6,7,9]
f1 = c1+d1
print(f1)
---------------------------------------------------------------------
import numpy as np
c2 = np.array([1,3,5,7,9])
d2 = np.array([3,5,6,7,9])
f2 = c2+d2
print(f2)
---------------------------------------------------------------------
ndarray.ndim
維度的數量。
ndarray.shape
顯示出陣列在每個維度上的整數值。
ndarray.size
陣列內元素的總數。
ndarray.dtype
用來描述陣列中元素類型的對象。
https://numpy.org/doc/stable/user/basics.types.html

import numpy as np
i = [[1,2,3],
     [4,5,6]]
#軸(axis)
#軸0:[1,2,3]、[4,5,6]
#軸1:1、2、3、4、5、6
a = np.array(i,dtype = np.int8)
print(a.ndim) #軸0
print(a.shape) #軸0:2個元素 軸1:3個元素
print(a.size) #軸1
print(a.dtype)---------------------------------------------------.