# 題目：  
Looking throw the “Online Judge’s Problem Set Archive” I found a very interesting problem number 498, titled “Polly the Polynomial”. Frankly speaking, I did not solve it, but I derived from it this problem.
Everything in this problem is a derivative of something from 498. In particular, 498 was “... designed to help you remember  ...  basic algebra skills, make the world a better place, etc., etc.”.  This problem     is designed to help you remember basic derivation algebra skills, increase the speed in which world becomes a better place, etc., etc.
In 498 you had to evaluate the values of polynomial

a0xn + a1xn−1 + . . . + an−1x + an.

In this problem you should evaluate its derivative. Remember that derivative is defined as

a0nxn−1 + a1(n − 1)xn−2 + . . . + an−1.

All the input and output data will fit into integer, i.e. its absolute value will be less than 231.


# Input  
Your program should accept an even number of lines of text. Each pair of lines will represent one problem. The first line will contain one integer - a value for x. The second line will contain a list of integers a0, a1, ..., an−1, an, which represent a set of polynomial coeﬃcients.


# Output  
For each pair of lines, your program should evaluate the derivative of polynomial for the given value x and output it in a single line.

 
# Sample Input    
7  
1 -1  
2  
1 1 1  

 

# Sample Output    
1  
5  


# 題意：  
計算a0xn + a1xn−1 + . . . + an−1x + an.的微分  
input的資料兩列為一組，每一組的第一列為x值; 第二列為函數的係數a0、a1、a2  
output為函數的微分  

# Code 
**Python**  
```ruby
while True:
    x=int(input())
    if not x: #若沒輸入x，則跳出while迴圈
        break
    try:
        a=input().split(' ')
        f_len=len(a)-1 #function的長度，(-1)是因為function從0開始算

        ans=0
        for item in a:
            ans+=int(item)*f_len*(x**(f_len-1))
            f_len-=1

        print(int(ans))
    except ValueError:
        print('輸入錯誤')
```
