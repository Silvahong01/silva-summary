# Assignment #6: Recursion and DP

Updated 2201 GMT+8 Oct 29, 2024

2024 fall, Complied by <mark>洪千濠 工学院</mark>



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### sy119: 汉诺塔

recursion, https://sunnywhy.com/sfbj/4/3/119  

思路：耗时1h，一开始写屎山代码，毫无悬念的失败，后来看了题解，又花好久才明白为什么这么做是对的



代码：

```python
def hannuota(n, from_rod, to_rod, mid_rod):
    if n == 0:
        return
    hannuota(n - 1, from_rod, mid_rod, to_rod)
    print(f"{from_rod}->{to_rod}")
    hannuota(n - 1, mid_rod, to_rod, from_rod)

n = int(input())
print(2**n - 1)
hannuota(n, 'A', 'C', 'B')
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241103135611299](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241103135611299.png)



### sy132: 全排列I

recursion, https://sunnywhy.com/sfbj/4/3/132

思路：耗时1h



代码：

```python
def dfs(idx, n, used, temp, result):
    if idx == n + 1:  
        result.append(temp[:])  
        return

    for i in range(1, n + 1):
        if not used[i]:  
            temp.append(i)  
            used[i] = True  
            dfs(idx + 1, n, used, temp, result) 
            used[i] = False  
            temp.pop()  


def qpl(n):
    result = []
    used = [False] * (n + 1)  
    dfs(1, n, used, [], result) 
    for perm in result:
        print(" ".join(map(str, perm)))  

n = int(input())
qpl(n)
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241103140355609](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241103140355609.png)



### 02945: 拦截导弹 

dp, http://cs101.openjudge.cn/2024fallroutine/02945

思路：耗时1.5h



代码：

```python
def max_intercepted_missiles(k, heights):
    dp = [1] * k
    for i in range(1, k):
        for j in range(i):
            if heights[i] <= heights[j]:
                dp[i] = max(dp[i], dp[j] + 1)

    return max(dp)


if __name__ == "__main__":

    k = int(input())
    heights = list(map(int, input().split()))

    result = max_intercepted_missiles(k, heights)
    print(result)
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241103140730058](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241103140730058.png)



### 23421: 小偷背包 

dp, http://cs101.openjudge.cn/practice/23421

思路：耗时3h



代码：

```python
n,b=map(int, input().split())
price=[0]+[int(i) for i in input().split()]
weight=[0]+[int(i) for i in input().split()]
bag=[[0]*(b+1) for _ in range(n+1)]
for i in range(1,n+1):
    for j in range(1,b+1):
        if weight[i]<=j:
            bag[i][j]=max(price[i]+bag[i-1][j-weight[i]], bag[i-1][j])
        else:
            bag[i][j]=bag[i-1][j]
print(bag[-1][-1])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241103141114432](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241103141114432.png)



### 02754: 八皇后

dfs and similar, http://cs101.openjudge.cn/practice/02754

思路：耗时5h



代码：

```python
list1 = []

def queen(s):
    if len(s) == 8:
        list1.append(s)
        return
    for i in range(1, 9):
        if all(str(i) != s[j] and abs(len(s) - j) != abs(i - int(s[j])) for j in range(len(s))):
            queen(s + str(i))

queen('')
samples = int(input())
for k in range(samples):
    print(list1[int(input()) - 1])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241103141559738](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241103141559738.png)



### 189A. Cut Ribbon 

brute force, dp 1300 https://codeforces.com/problemset/problem/189/A

思路：耗时4h



代码：

```python
n, a, b, c = map(int, input().split())
dp = [0]+[float('-inf')]*n

for i in range(1, n+1):
    for j in (a, b, c):
        if i >= j:
            dp[i] = max(dp[i-j] + 1, dp[i])

print(dp[n])
```



代码运行截图 <mark>（至少包含有"Accepted"）</mark>

![image-20241103141940318](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241103141940318.png)



## 2. 学习总结和收获

<mark>如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。</mark>

题目好难，基本都要看了题解才能倒推出思路，再加上期中逼近感觉心态有点乱。



