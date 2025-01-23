# Assignment #2: 语法练习

Updated 0126 GMT+8 Sep 24, 2024

2024 fall, Complied by ==洪千濠 工学院==



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知9月19日导入选课名单后启用。**作业写好后，保留在自己手中，待9月20日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### 263A. Beautiful Matrix

https://codeforces.com/problemset/problem/263/A



思路：确定1的位置，耗时20分钟



##### 代码

```python
def read_matrix():
    matrix = []
    for i in range(5):
        row = list(map(int, input().split()))
        matrix.append(row)
    return matrix

def minimum(matrix):
    for i in range(5):
        for j in range(5):
            if matrix[i][j] == 1:
                return abs(i - 3) + abs(j - 3)

matrix = read_matrix()

print(minimum(matrix))

```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241008103616861](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241008103616861.png)



### 1328A. Divisibility Problem

https://codeforces.com/problemset/problem/1328/A



思路：分类讨论，耗时5分钟



##### 代码

```python
t = int(input())

for _ in range(t):
    a, b = map(int, input().split())
    yushu = a % b

    if yushu == 0:
        print(0)
    else:
        print(b - yushu) 

```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241008103326108](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241008103326108.png)



### 427A. Police Recruits

https://codeforces.com/problemset/problem/427/A



思路：分类讨论；耗时20分钟



##### 代码

```python
def zongshijian(n):
    a = 0
    b = 0

    events = list(map(int, input().split()))

    for event in events:
        if event == -1:  
            if a > 0:
                a -= 1
            else:
                b += 1
        else:  
            a += event

    return b

n = int(input())

print(zongshijian(n))

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20241008104312223](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241008104312223.png)



### 02808: 校门外的树

http://cs101.openjudge.cn/practice/02808/



思路：耗时5分钟



##### 代码

```python
L, m = map(int, input().split())

shu = [1]*(L+1)

for i in range(m):
    start, end = map(int, input().split())
    for j in range(start, end+1):
        shu[j] = 0

print(shu.count(1))

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20241008115054136](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241008115054136.png)



### sy60: 水仙花数II

https://sunnywhy.com/sfbj/3/1/60



思路：耗时15分钟



##### 代码

```python
def find_narcissistic_numbers(m, n):
    result = []  

    for i in range(m, n + 1):
        a = i // 100
        b = (i % 100) // 10
        c = i % 10

        if a ** 3 + b ** 3 + c ** 3 == i:
            result.append(i)  

    if result:
        print(" ".join(map(str, result)))

    else:
        print("NO")


m,n = map(int, input().split())
find_narcissistic_numbers(m,n)

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20241008110338116](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241008110338116.png)



### 01922: Ride to School

http://cs101.openjudge.cn/practice/01922/



思路：耗时20分钟



##### 代码

```python
import math

while True:
    n = int(input())
    if n == 0:
        break

    longest = float("inf")
    for i in range(n):
        speed, time = map(int, input().split())
        if time < 0:
            continue
        zsc = math.ceil((4500 / speed) * 3.6 + time)
        longest = min(longest, zsc)

    print(longest)

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20241008122511208](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241008122511208.png)



## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

感觉题目做的比以前要顺利一点，把思路转化为python语言的能力有所提升，最近在尝试每日选做的题目



