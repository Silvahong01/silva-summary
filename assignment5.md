# Assignment #5: Greedy穷举Implementation

Updated 1939 GMT+8 Oct 21, 2024

2024 fall, Complied by <mark>洪千濠 工学院</mark>



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### 04148: 生理周期

brute force, http://cs101.openjudge.cn/practice/04148

思路：耗时20分钟



代码：

```python
num = 1
while True:
    p, e, i, d = map(int, input().split())
    if [p, e, i, d] == [-1, -1, -1, -1]:
        break
    p %= 23
    e %= 28
    i %= 33

    s = d + 1

    while (s - p) % 23 != 0 or (s - e) % 28 != 0 or (s - i) % 33 != 0:
        s += 1

    s -= d
    print(f'Case {num}: the next triple peak occurs in {s} days.')
    num += 1
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241026100839163](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241026100839163.png)



### 18211: 军备竞赛

greedy, two pointers, http://cs101.openjudge.cn/practice/18211

思路：耗时40分钟



代码：

```python
p = int(input())
cost = sorted(list(map(int, input().split())))

i, j, wqs = 0, len(cost) - 1, 0

while i < j:
    if cost[i] <= p:
        wqs += 1
        p -= cost[i]
        i += 1
    elif wqs:
        wqs -= 1
        p += cost[j]
        j -= 1
    else:
        break
print(wqs +(cost[i] <= p))
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241026101924922](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241026101924922.png)



### 21554: 排队做实验

greedy, http://cs101.openjudge.cn/practice/21554

思路：耗时40分钟



代码：

```python
n = int(input())
time = list(map(int, input().split()))
students = sorted([(time[i], i + 1) for i in range(n)])
print(" ".join(map(lambda stu: str(stu[1]), students)))
pre_sum, total = 0, 0
for stu in students:
    total += pre_sum
    pre_sum += stu[0]
print(f"{total/n:.2f}")
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241026125202897](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241026125202897.png)



### 01008: Maya Calendar

implementation, http://cs101.openjudge.cn/practice/01008/

思路：耗时20分钟



代码：

```python
Haab = {"pop": 0, "no": 1, "zip": 2, "zotz": 3, "tzec": 4, "xul": 5, "yoxkin": 6, "mol": 7, "chen": 8, "yax": 9, "zac": 10, "ceh": 11, "mac": 12, "kankin": 13, "muan": 14, "pax": 15, "koyab": 16, "cumhu": 17, "uayet": 18}
Tzolkin = {0: "imix", 1: "ik", 2: "akbal", 3: "kan", 4: "chicchan", 5: "cimi", 6: "manik", 7: "lamat", 8: "muluk", 9: "ok", 10: "chuen", 11: "eb", 12: "ben", 13: "ix", 14: "mem", 15: "cib", 16: "caban", 17: "eznab", 18: "canac", 19: "ahau"}
n = int(input())
print(n)
for _ in range(n):
    day, month, year = input().split()
    day = int(day.rstrip("."))
    total = int(year) * 365 + Haab[month] * 20 + day
    print(total % 13 + 1, Tzolkin[total % 20], total // 260)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241026103548841](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241026103548841.png)



### 545C. Woodcutters

dp, greedy, 1500, https://codeforces.com/problemset/problem/545/C

思路：耗时50分钟



代码：

```python
n = int(input())
s = [[int(x) for x in input().split()] for i in range(n)]
count = 2
if n == 1:
    print(1)
else:
    for i in range(1, n - 1):
        if s[i][0] - s[i - 1][0] > s[i][1]:
            count += 1
        elif s[i + 1][0] - s[i][0] > s[i][1]:
            count += 1
            s[i][0] += s[i][1]

    print(count)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241026104030881](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241026104030881.png)



### 01328: Radar Installation

greedy, http://cs101.openjudge.cn/practice/01328/

思路：耗时3h



代码：

```python
import math

def solve(n,d,islands):
    if d<0:
        return -1

    ranges =[]
    for x,y in islands:
        if y>d:
            return -1
        delta=math.sqrt(d*d-y*y)
        ranges.append((x-delta,x + delta))
    ranges.sort(key=lambda x: x[1])
    number=1
    r=ranges[0][1]
    for start,end in ranges[1:]:
        if r<start:
            r=end
            number+=1
    return number
case=0
while True:
    n,d=map(int,input().split())
    if n==0 and d==0:
        break
    case+=1
    islands=[]
    for i in range(n):
        islands.append(tuple(map(int,input().split())))
    result=solve(n,d,islands)
    print(f'Case{case}: {result}')
    input()
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241026140807417](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241026140807417.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

开始冲刺期中，期中之后设定更多的时间投入，近期在b站上看视频学习但训练较少，期中之后一定积极追上每日选做



