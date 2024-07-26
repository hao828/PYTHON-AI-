Python與AI人工智慧開發入門-05:https://youtu.be/wD7nOWyjT9s
Python與AI人工智慧開發入門-06:https://youtu.be/DYwgWtWuuMA
### for迴圈
name = "Howard"
for c in name:
    print(c)
print(name[2])


### 索引標籤與取值
msg = "abcdefghij"
print(len(msg))
print(msg[0])
print(msg[9])
print(msg[5])
print(msg[-3])
print(msg[-1])

msg = "abcdefghij"
for i in range(0,len(msg)):
    print(i,msg[i])

msg = "abcdefghij"
for i in range(len(msg)-1,-1,-1):
    print(i,msg[i])

msg = "abcdefghij"
for i in range(1,4):
    print(msg[i],end="")

msg = "abcdefghij"
print(msg[1:4])

msg = "abcdefghij"
print(msg[4:7])
print(msg[-3:])
print(msg[:-3])
print(msg[::2]) # 0開始每次index加2

msg = "abcdefghij"
msgLan = len(msg)
newMsg = msg[msgLan-1::-1] # 產生新的字串
print(newMsg)

msg = "abcdefghij"
newMsg = msg[-3:-8:-2]
print(newMsg)


### 反斜線作為跳脫字元，可用於引用特殊字元
# 跳脫
print("AB\nCD")
print("12\t34\t56")

