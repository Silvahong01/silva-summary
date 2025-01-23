# Assignment #B: Dec Mock Exam大雪前一天

Updated 1649 GMT+8 Dec 5, 2024

2024 fall, Complied by <mark>洪千濠 工学院</mark>



**说明：**

1）⽉考： AC6<mark>（请改为同学的通过数）</mark> 。考试题⽬都在“题库（包括计概、数算题目）”⾥⾯，按照数字题号能找到，可以重新提交。作业中提交⾃⼰最满意版本的代码和截图。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### E22548: 机智的股民老张

http://cs101.openjudge.cn/practice/22548/

思路：耗时30分钟



代码：

```python
a= list(map(int, input().split()))
min_price = float('inf')
max_profit = 0

for price in a:
    min_price = min(min_price, price) 
    max_profit = max(max_profit, price - min_price)  

print(max_profit)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241208092550064](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241208092550064.png)



### M28701: 炸鸡排

greedy, http://cs101.openjudge.cn/practice/28701/

思路：耗时20分钟



代码：

```python
n, k = map(int, input().split())
t = list(map(int, input().split()))
t.sort()
s = sum(t)
while True:
    if t[-1] > s / k:
        s -= t.pop()
        k -= 1
    else:
        print(f'{s / k:.3f}')
        break
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241208094105503](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241208094105503.png)



### M20744: 土豪购物

dp, http://cs101.openjudge.cn/practice/20744/

思路：耗时40分钟



代码：

```python
a=list(map(int,input().split(",")))
n=len(a)
dp1,dp2=a[0],a[0]
ans=0
for i in range(1,n):
    dp1,dp2=max(a[i],dp1+a[i]),max(dp1,dp2+a[i])
    ans=max(ans,dp2)
print(ans)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241208095111389](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241208095111389.png)



### T25561: 2022决战双十一

brute force, dfs, http://cs101.openjudge.cn/practice/25561/

思路：耗时1h



代码：

```python
result = float("inf")
n, m = map(int, input().split())
store_prices = [input().split() for _ in range(n)]
you= [input().split() for _ in range(m)]
la=[0]*m
def dfs(i,sum1):
    global result
    if i==n:
        jian=0
        for i2 in range(m):
            store_j=0
            for k in you[i2]:
                a,b=map(int,k.split('-'))
                if la[i2]>=a:
                    store_j=max(store_j,b)
            jian+=store_j
        result=min(result,sum1-(sum1//300)*50-jian)
        return
    for i1 in store_prices[i]:
        idx,p=map(int,i1.split(':'))
        la[idx-1]+=p
        dfs(i+1,sum1+p)
        la[idx-1]-=p
dfs(0,0)
print(result)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241208134223696](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241208134223696.png)



### T20741: 两座孤岛最短距离

dfs, bfs, http://cs101.openjudge.cn/practice/20741/

思路：耗时30分钟



代码：

```python
import heapq
n=int(input())
land=[]
dir=[[0,1],[0,-1],[1,0],[-1,0]]
for i in range(n):
    land.append(input())
visited=[[True]*(len(land[i])) for i in range(len(land))]
def find(x1,y1):
    pos=[]
    heapq.heappush(pos,(0,x1,y1))
    visited[x1][y1]=False
    while pos:
        step,x,y=heapq.heappop(pos)
        if land[x][y]=="1" and step!=0:
            return step
        for dx,dy in dir:
            nx,ny=x+dx,y+dy
            if 0<=nx<n and 0<=ny<len(land[nx]) and visited[nx][ny]:
                visited[nx][ny]=False
                if land[nx][ny]==land[x][y] and land[x][y]!="0":
                    heapq.heappush(pos,(step,nx,ny))
                else:
                    heapq.heappush(pos,(step+1,nx,ny))
mark=False
for i in range(n):
    for j in range(len(land[i])):
        if land[i][j]=="1":
            print(find(i,j)-1)
            exit()
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241208134120283](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241208134120283.png)



### T28776: 国王游戏

greedy, http://cs101.openjudge.cn/practice/28776

思路：耗时50分钟



代码：

```python
n=int(input())
a0,b0=map(int,input().split())
numbers=[]
for _ in range(n):
    a,b=map(int,input().split())
    numbers.append((a,b))
numbers.sort(key=lambda x:(x[0]*x[1]))
result=0
for i in range(n):
    result=max(result,a0//numbers[i][1])
    a0*=numbers[i][0]
print(result)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241208134457189](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241208134457189.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

月考没去参加，自己掐时间做感觉很差，超级紧张，现在一直掐时间做题想快点适应，模板都开始卡壳，可能原本就不扎实吧。



