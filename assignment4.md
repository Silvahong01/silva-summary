# Assignment #4: T-primes + 贪心

Updated 0337 GMT+8 Oct 15, 2024

2024 fall, Complied by <mark>洪千濠 工学院</mark>



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知9月19日导入选课名单后启用。**作业写好后，保留在自己手中，待9月20日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### 34B. Sale

greedy, sorting, 900, https://codeforces.com/problemset/problem/34/B



思路：一开始没想到价格要最大化，只是想着要带满m个，所以一直报错：耗时20分钟



代码

```python
def max_profit(n, m, a):
    a.sort()
    profit = 0
    for i in range(m):
        if a[i]<=0 :
            profit -= a[i]

    return profit


n, m = map(int, input().split())
a = list(map(int, input().split()))
print(max_profit(n, m, a))

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241020092837856](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241020092837856.png)



### 160A. Twins

greedy, sortings, 900, https://codeforces.com/problemset/problem/160/A

思路：遍历每一个硬币：耗时30分钟



代码

```python
def minshu(a,b,n,m) :
    b.sort(reverse=True)
    for i in range(0,len(b)) :
        if n>sum(b)/2 :
            m+=0

        else :
            n+=b[i]
            m+=1
    return m

a=int(input())
b=list(map(int,input().split()))
n=0
m=0
print(minshu(a,b,n,m))

```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241020095424516](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241020095424516.png)



### 1879B. Chips on the Board

constructive algorithms, greedy, 900, https://codeforces.com/problemset/problem/1879/B

思路：耗时1小时



代码

```python
t = int(input())
for _ in range(t):
    n = int(input())
    *a, = map(int, input().split())
    *b, = map(int, input().split())
    
    min_a = min(a)
    min_b = min(b)
    
    ans1 = sum([min_a + i for i in b])
    ans2 = sum([min_b + i for i in a])
    print(min(ans1, ans2))

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241020155421316](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241020155421316.png)



### 158B. Taxi

*special problem, greedy, implementation, 1100, https://codeforces.com/problemset/problem/158/B

思路：在分类讨论的时候一开始一直脑子糊涂：耗时40分钟



代码

```python
def min_taxis(groups):
    count = {1: 0, 2: 0, 3: 0, 4: 0}
    for s in groups:
        count[s] += 1

    taxis = 0
    taxis += count[4]
    count[4] = 0

    while count[3] > 0:

        taxis += 1
        count[3] -= 1
        if count[1] > 0:
            count[1] -= 1

    while count[2] > 0:
        if count[2]%2==0 :
            taxis += int(count[2]/2)
            count[2] = 0
        else:
            taxis += int(-(-count[2]//2))
            count[2] = 0
            if count[1] >= 2:
                count[1] -= 2
            elif count[1]==1:
                count[1] -= 1
            elif count[1] ==0:
                break
    taxis += -(-count[1] // 4)

    return taxis

if __name__ == "__main__":
    n = int(input())
    groups = list(map(int, input().split()))
    print(min_taxis(groups))

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241020103708852](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241020103708852.png)



### *230B. T-primes（选做）

binary search, implementation, math, number theory, 1300, http://codeforces.com/problemset/problem/230/B

思路：

耗时1小时，没找到优化方案

代码

```python
import math
def is_prime(n):
    if n <= 1:
        return False
    if n <= 3:
        return True
    if n % 2 == 0 or n % 3 == 0:
        return False
    i = 5
    while i * i <= n:
        if n % i == 0 or n % (i + 2) == 0:
            return False
        i += 6
    return True

if __name__ == '__main__':
    n=int(input())
    a=list(map(int,input().split()))
    for i in a:
        if math.pow(int(math.sqrt(i)),2)==i and  is_prime(math.sqrt(i))==True:
            print('YES')
        else :
            print('NO')

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241020155158182](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241020155158182.png)



### *12559: 最大最小整数 （选做）

greedy, strings, sortings, http://cs101.openjudge.cn/practice/12559

思路：冒泡排序；耗时1小时



代码

```python
n = int(input())
nums = input().split()
for i in range(n - 1):
    for j in range(i+1, n):
        if nums[i] + nums[j] < nums[j] + nums[i]:
            nums[i], nums[j] = nums[j], nums[i]

ans = "".join(nums)
nums.reverse()
print(ans + " " + "".join(nums))

```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241020163142356](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241020163142356.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

感觉对贪心算法有了基本的了解，还上网看了一些讲解，在写作业过程中，发现有时候还是会忘记基础语法，平时已经开始坚持看网上的算法教程，感觉还蛮有帮助的，至少做题的时候大概有思路了。期中考试之后打算再多花些时间，边学边练，争取熟能生巧。



