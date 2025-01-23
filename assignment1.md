# Assignment #1: 自主学习

Updated 0110 GMT+8 Sep 10, 2024

2024 fall, Complied by ==同学的姓名、院系==



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知9月19日导入选课名单后启用。**作业写好后，保留在自己手中，待9月20日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### 02733: 判断闰年

http://cs101.openjudge.cn/practice/02733/



思路：将题目中的要求转化为算数等式和不等式，再用条件语句讨论情况；花费5分钟



##### 代码

```python
a=int(input())
if a%4==0 and a%100!=0 or a%400==0:
    print("Y")
else :print("N")

```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20240922212723036](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240922212723036.png)



### 02750: 鸡兔同笼

http://cs101.openjudge.cn/practice/02750/



思路：讨论脚的数量是不是4的整数倍；花费10分钟



##### 代码

```python
a=int(input())
if a%4==0 :
    print(int(a/4),int(a/2))
elif a%4!=0 and a%2==0:
    print(int((a+2)/4),int(a/2))
else:
    print(0,0)

```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20240922213050590](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240922213050590.png)



### 50A. Domino piling

greedy, math, 800, http://codeforces.com/problemset/problem/50/A



思路：根据m，n奇偶数性质，列出算式；耗时35分钟



##### 代码

```python
def max_dominoes(m, n):
    return (m * n) // 2
m,n=map(int,input().split())
print(max_dominoes(m, n))

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240922221459999](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240922221459999.png)



### 1A. Theatre Square

math, 1000, https://codeforces.com/problemset/problem/1/A



思路：先定义函数，再将涉及到的数据用相应字母表示；耗时20分钟



##### 代码

```python
import math


def min_flagstones(n, m, a):
    stones_n = math.ceil(n / a)
    stones_m = math.ceil(m / a)

    return stones_n * stones_m


n,m,a=map(int,input().split())
print(min_flagstones(n, m, a)) 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240922220958564](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240922220958564.png)



### 112A. Petya and Strings

implementation, strings, 1000, http://codeforces.com/problemset/problem/112/A



思路：比较字符串长度；耗时5小时，对函数应用还是不怎么会，有些代码还是不明白它的用途



##### 代码

```python
def read_input():
    str1 = input().strip()
    str2 = input().strip()
    return str1, str2

def compare_strings(str1, str2):
    for c1, c2 in zip(str1.lower(), str2.lower()):
        if c1 < c2:
            return -1
        elif c1 > c2:
            return 1
    return 0
def main():
    str1, str2 = read_input()
    result = compare_strings(str1, str2)
    print(result)

if __name__ == "__main__":
    main()

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240923212951933](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240923212951933.png)



### 231A. Team

bruteforce, greedy, 800, http://codeforces.com/problemset/problem/231/A



思路：对于每个问题,确定解决问题的人数,并检查是否有至少两人确定.如果是,就增加计数器;耗时45分钟



##### 代码

```python
def main():
    n = int(input())

    solved_count = 0

    for _ in range(n):
        petya, vasya, tonya = map(int, input().split())
        confident_count = petya + vasya + tonya


        if confident_count >= 2:
            solved_count += 1

    print(solved_count)


if __name__ == "__main__":
    main()

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240922222428190](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240922222428190.png)



## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

平时会做OJ上面的题目，零基础确实很痛苦，但是慢慢学加上群里的解答，我比一开始好很多了，平时也在看菜鸟课程，对做题很有帮助，感觉继续坚持下去应该能越学越好



