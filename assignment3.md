# Assign #3: Oct Mock Exam暨选做题目满百

Updated 1537 GMT+8 Oct 10, 2024

2024 fall, Complied by Hongfei Yan==洪千濠 工学院==



**说明：**

1）Oct⽉考： AC==2 。考试题⽬都在“题库（包括计概、数算题目）”⾥⾯，按照数字题号能找到，可以重新提交。作业中提交⾃⼰最满意版本的代码和截图。

2）请把每个题目解题思路（可选），源码Python, 或者C++/C（已经在Codeforces/Openjudge上AC），截图（包含Accepted, 学号），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、作业评论有md或者doc。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### E28674:《黑神话：悟空》之加密

http://cs101.openjudge.cn/practice/28674/



思路：耗时50分钟



代码

```python
def jiami(k, text):
    xintext = ""


    for char in text:

        if char.isalpha():

            base = ord('A') if char.isupper() else ord('a')

            xintext += chr((ord(char) - base - k) % 26 + base)
        else:
            xintext += char

    return xintext

import sys


k = int(input().strip())

text = input().strip()

xintext = jiami(k, text)
print(xintext)

```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241013214329727](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241013214329727.png)



### E28691: 字符串中的整数求和

http://cs101.openjudge.cn/practice/28691/



思路：将数字提取并转换类型；耗时3分钟



代码

```python
m,n=map(str,input().split())
a=int(m[0])*10+int(m[1])+int(n[0])*10+int(n[1])
print(a)

```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20241013165124718](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241013165124718.png)



### M28664: 验证身份证号

http://cs101.openjudge.cn/practice/28664/



思路：耗时1h且借助AI



代码

```python
def is_valid_id_number(id_number):

    coefficients = [7, 9, 10, 5, 8, 4, 2, 1, 6, 3, 7, 9, 10, 5, 8, 4, 2]

    check_digits = '10X98765432'


    id_number_17 = id_number[:17]

    check_digit = id_number[-1].upper()


    weighted_sum = sum(int(id_number_17[i]) * coefficients[i] for i in range(17))


    remainder = weighted_sum % 11


    calculated_check_digit = check_digits[remainder]


    return calculated_check_digit == check_digit



if __name__ == "__main__":
    import sys


    n = int(input().strip())



    for _ in range(n):
        id_number = input().strip()

        if is_valid_id_number(id_number):
            print("YES")
        else:
            print("NO")

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20241013214741120](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241013214741120.png)



### M28678: 角谷猜想

http://cs101.openjudge.cn/practice/28678/



思路：耗时15分钟



代码

```python
n=int(input())
while n!=1 :
    if n%2==0 :
        n=int(n/2)
        m=int(n*2)
        print(f'{m}/2={n}')
    elif n%2!=0 and n!=1 :
        n=int(n*3+1)
        m=int((n-1)/3)
        print(f'{m}*3+1={n}')
else :
        print('End')

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20241013170400549](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241013170400549.png)



### M28700: 罗马数字与整数的转换

http://cs101.openjudge.cn/practice/28700/



思路：耗时1h；仍然超时



##### 代码

```python
def convert(shuru):

    roman_to_int = {
        'M': 1000, 'CM': 900, 'D': 500, 'CD': 400,
        'C': 100, 'XC': 90, 'L': 50, 'XL': 40,
        'X': 10, 'IX': 9, 'V': 5, 'IV': 4, 'I': 1
    }

    int_to_roman = [
        ('M', 1000), ('CM', 900), ('D', 500), ('CD', 400),
        ('C', 100), ('XC', 90), ('L', 50), ('XL', 40),
        ('X', 10), ('IX', 9), ('V', 5), ('IV', 4), ('I', 1)
    ]


    if isinstance(shuru, str) and all(c in 'IVXLCDM' for c in shuru):
        num = 0
        i = 0
        while i < len(shuru):
            if i + 1 < len(shuru) and shuru[i:i+2] in roman_to_int:
                num += roman_to_int[shuru[i:i+2]]
                i += 2
            else:
                num += roman_to_int[shuru[i]]
                i += 1
        return num

    elif isinstance(shuru, int) and 1 <= shuru <= 3999:
        result = ''
        for roman, value in int_to_roman:
            while shuru >= value:
                result += roman
                shuru -= value
        return result
    else:
        raise ValueError("Invalid input")

print(convert(input()))

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20241014130813290](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241014130813290.png)



### *T25353: 排队 （选做）

http://cs101.openjudge.cn/practice/25353/



思路：实力有限，来日方长



代码

```python


```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“计概2024fall每日选做”、CF、LeetCode、洛谷等网站题目。==

月考之后感觉对一些基本的语法还不是十分熟悉，有点起飞困难，而且发现对一些之前没见过的用法还是有畏难心理，思路还是不那么清晰，感觉之后要再加时间去啃，希望能有顿悟（^ _ ^)









