# Assignment #C: 五味杂陈 

Updated 1148 GMT+8 Dec 10, 2024

2024 fall, Complied by <mark>洪千濠 工学院</mark>



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

2）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

3）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### 1115. 取石子游戏

dfs, https://www.acwing.com/problem/content/description/1117/

思路：耗时1h，在取的过程中出现一个是另一个的n倍一开始没想到



代码：

```python
def jc(a,b) :
    if a<b :
        a,b=b,a
    if a//b>=2 or a%b==0:
        print('win')
    elif a//b==1 and a%b!=0 and b%(a-b)!=0 and b//(a-b)==1:
        a,b=2*b-a,a-b
        return jc(a,b)
    else :
        print('lose')
while True :
    a,b=map(int,input().split())
    if a==0 and b==0 :
        break
    else :
        jc(a,b)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241210202559297](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241210202559297.png)



### 25570: 洋葱

Matrices, http://cs101.openjudge.cn/practice/25570

思路：耗时1h，一直runtime error，看完题解心态炸了，人家解题思路差不多，但是代码写的更简洁，代码的思路更惊艳，我写的只是傻傻加起来再减去重复的，人家直接用min解决重复问题，还那么简洁，唉，技不如人，故默写了一遍



代码：

```python
from math import ceil
n = int(input()) 
matrix = [0 for _ in range(n)] 
for i in range(n): 
    matrix[i] = [int(_) for _ in input().split()] 
ans = [0] * ceil(n/2) 
for i in range(n): 
    for j in range(n): 
        ans[min(i, j, n-1-i, n-1-j)] += matrix[i][j] 
print(max(ans))
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241210214040833](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241210214040833.png)



### 1526C1. Potions(Easy Version)

greedy, dp, data structures, brute force, *1500, https://codeforces.com/problemset/problem/1526/C1

思路：耗时20分钟



代码：

```python
n=int(input())
queue=list(map(int,input().split()))
dp=[0]+[-1]*n
m=0
for i in queue:
    for j in range(m,-1,-1):
        dp[j+1]=max(dp[j+1],dp[j]+i)
    if dp[m+1]!=-1:
        m+=1
print(m)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241213201248169](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241213201248169.png)



### 22067: 快速堆猪

辅助栈，http://cs101.openjudge.cn/practice/22067/

思路：耗时30分钟



代码：

```python
a = []
m = []

while True:
    try:
        s = input().split()
    
        if s[0] == "pop":
            if a:
                a.pop()
                if m:
                    m.pop()
        elif s[0] == "min":
            if m:
                print(m[-1])
        else:
            h = int(s[1])
            a.append(h)
            if not m:
                m.append(h)
            else:
                k = m[-1]
                m.append(min(k, h))
    except EOFError:
        break
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241211104721840](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241211104721840.png)



### 20106: 走山路

Dijkstra, http://cs101.openjudge.cn/practice/20106/

思路：耗时2h



代码：

```python
import heapq
m, n, p = map(int, input().split())
info = []
for _ in range(m):
    info.append(list(input().split()))
directions = [(-1, 0), (1, 0), (0, 1), (0, -1)]


def dijkstra(start_r, start_c, end_r, end_c):
    pos = []
    dist = [[float('inf')] * n for _ in range(m)]
    if info[start_r][start_c] == '#':
        return 'NO'
    dist[start_r][start_c] = 0
    heapq.heappush(pos, (0, start_r, start_c))
    while pos:
        d, r, c = heapq.heappop(pos)
        if r == end_r and c == end_c:
            return d
        h = int(info[r][c])
        for dr, dc in directions:
            nr = r + dr
            nc = c + dc
            if 0 <= nr < m and 0 <= nc < n and info[nr][nc] != '#':
                if dist[nr][nc] > d + abs(int(info[nr][nc]) - h):
                    dist[nr][nc] = d + abs(int(info[nr][nc]) - h)
                    heapq.heappush(pos, (dist[nr][nc], nr, nc))
    return 'NO'


for _ in range(p):
    x, y, z, w = map(int, input().split())
    print(dijkstra(x, y,z,w))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241211120819845](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241211120819845.png)



### 04129: 变换的迷宫

bfs, http://cs101.openjudge.cn/practice/04129/

思路：耗时1.5h



代码：

```python
from collections import deque

def bfs(x, y):
    visited = {(0, x, y)}
    dx = [0, 0, 1, -1]
    dy = [1, -1, 0, 0]
    queue = deque([(0, x, y)])
    while queue:
        time, x, y = queue.popleft()
        for i in range(4):
            nx, ny = x + dx[i], y + dy[i]
            temp = (time + 1) % k
            if 0 <= nx < r and 0 <= ny < c and (temp, nx, ny) not in visited:
                cur = maze[nx][ny]
                if cur == 'E':
                    return time + 1
                elif cur != '#' or temp == 0:
                    queue.append((time + 1, nx, ny))
                    visited.add((temp, nx, ny))
    return 'Oop!'


t = int(input())
for _ in range(t):
    r, c, k = map(int, input().split())
    maze = [list(input()) for _ in range(r)]
    for i in range(r):
        for j in range(c):
            if maze[i][j] == 'S':
                print(bfs(i, j))
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241211121459769](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241211121459769.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

感觉还是达不到题解的高度，技不如人，只能说应该是时间花的不够，继续努力



