# Assignment #7: Nov Mock Exam立冬

Updated 1646 GMT+8 Nov 7, 2024

2024 fall, Complied by <mark>洪千濠 工学院</mark>



**说明：**

1）⽉考：未参加（请改为同学的通过数）</mark> 。考试题⽬都在“题库（包括计概、数算题目）”⾥⾯，按照数字题号能找到，可以重新提交。作业中提交⾃⼰最满意版本的代码和截图。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### E07618: 病人排队

sorttings, http://cs101.openjudge.cn/practice/07618/

思路：耗时20分钟



代码：

```python
n = int(input())

old = []
young = []

for _ in range(n):
    patient_id, age = input().split()
    age = int(age)
    if age >= 60:
        old.append((patient_id, age))
    else:
        young.append((patient_id, age))

old.sort(key=lambda x: -x[1])

sorted_patients = old + young

for patient in sorted_patients:
    print(patient[0])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241111212020786](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241111212020786.png)



### E23555: 节省存储的矩阵乘法

implementation, matrices, http://cs101.openjudge.cn/practice/23555/

思路：耗时1h



代码：

```python
n, m1, m2 = map(int, input().split())
a = [[0] * n for _ in range(n)]
b = [[0] * n for _ in range(n)]
for _ in range(m1):
    x, y, v = map(int, input().split())
    a[x][y] = v
for _ in range(m2):
    x, y, v = map(int, input().split())
    b[x][y] = v
c = [[0] * n for _ in range(n)]
for i in range(n):
    for j in range(n):
        c[i][j] = sum(a[i][k] * b[k][j] for k in range(n))
        if c[i][j] != 0:
            print(i, j, c[i][j])
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241111212524850](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241111212524850.png)



### M18182: 打怪兽 

implementation/sortings/data structures, http://cs101.openjudge.cn/practice/18182/

思路：耗时3h，最后去看了题解才看明白



代码：

```python
for _ in range(int(input())):
    n,m,b = map(int, input().split(' '))
    d = {}
    for i in range(n):
        t,x=map(int, input().split(' '))
        if t not in d.keys():
            d[t] = [x]
        else:
            d[t].append(x)
    for i in d.keys():
        d[i].sort(reverse=True)
        d[i] = sum(d[i][:m])
    dp = sorted(d.items())
    for i in dp:
        b -= i[1]
        if b<=0:
            print(i[0])
            break
    else:
        print('alive')
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241111213033269](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241111213033269.png)



### M28780: 零钱兑换3

dp, http://cs101.openjudge.cn/practice/28780/

思路：耗时40分钟



代码：

```python
n,m=map(int,input().split())
coins=list(map(int,input().split()))
dp=[0]+[float('inf')]*m
for i in range(1,m+1):
    for coin in coins:
        dp[i]=min(dp[i],dp[i-coin]+1)
print(dp[-1] if dp[-1]!=float('inf') else -1)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241111214809323](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241111214809323.png)



### T12757: 阿尔法星人翻译官

implementation, http://cs101.openjudge.cn/practice/12757

思路：耗时40分钟，感觉思路像罗马数字



代码：

```python
tokens = [str(i) for i in input().split()]
dic={"zero":0, "one":1, "two":2, "three":3, "four":4, "five":5, "six":6, 
     "seven":7, "eight":8, "nine":9, "ten":10, "eleven":11, "twelve":12, 
     "thirteen":13, "fourteen":14, "fifteen":15, "sixteen":16, "seventeen":17, 
     "eighteen":18, "nineteen":19, "twenty":20, "thirty":30, "forty":40, 
     "fifty":50, "sixty":60, "seventy":70, "eighty":80, "ninety":90, 
     "hundred":100, "thousand":1000, "million":1000000}

sign = 1
if tokens[0]=="negative":
    sign = -1
    del tokens[0]

total = 0
tmp = 0
for i in tokens:
    if i in ("thousand", "million"):
        total += tmp*dic[i]
        tmp = 0
        continue
    if i == "hundred":
        tmp *= dic[i]
    else:
        tmp += dic[i]
        
print( sign * (total + tmp) )
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241111213633280](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241111213633280.png)



### T16528: 充实的寒假生活

greedy/dp, cs10117 Final Exam, http://cs101.openjudge.cn/practice/16528/

思路：耗时1h，理解github大佬解法30分钟，感觉惊为天人



代码：

```python
n = int(input())
m = [[int(x) for x in input().split()] for i in range(n)]
for i in range(n):
    m[i][0], m[i][1] = m[i][1], m[i][0]
m.sort()
y = 1
a = m[0][0]
for i in range(n-1):
    if m[i+1][1]>a:
        y += 1
        a = m[i+1][0]
print(y)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241111213958558](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241111213958558.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

月考因为期中考试没考，感觉跟不上了，开始投入大量时间，很多时候是有思路但是不够简洁，而且表达的时候总会出现卡壳，很烦，理解GitHub上的高手做法有时候都要半天，思维也很需要提升。。。开始追赶



