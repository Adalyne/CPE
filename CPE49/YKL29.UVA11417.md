# 題目  
Given the value of N, you will have to find the value of G. The definition of G is given below:

![image](https://github.com/Adalyne/CPE/blob/209059eacc90d6b776740a2af237244157cf0018/CPE49/G%E5%85%AC%E5%BC%8F%E9%81%8B%E7%AE%97.png)

Here GCD(i,j) means the greatest common divisor of integer i and integer j.

For those who have trouble understanding summation notation, the meaning of G is given in the following code:

![image](https://github.com/Adalyne/CPE/blob/cd4a06e8ad4c3ab2fca02c7a942cdf267275ec90/CPE49/G%E7%9A%84%E6%BC%94%E7%AE%97%E6%B3%95.png)

# Input
The input file contains at most 100 lines of inputs. Each line contains an integer N (1<N<501). The meaning of N is given in the problem statement. Input is terminated by a line containing a single zero.  This zero should not be processed.

# Output
For each line of input produce one line of output. This line contains the value of G for corresponding N.

# Sample Input   
10  
100  
500  
0  

# Sample Output   
67  
13015  
442011  

# 題意：  
算1-N中彼此的最大公因數相加  
Input：每一列輸入為1-N的N(ex.10代表1-10,100代表1-100)  
Output：最大公因數相加  

# Code 
**Python**
```ruby
def GCD(a,b):  #利用輾轉相除法
    while b != 0:
        t = a % b
        a = b
        b = t
    return a

while True:
    N=int(input())
    if not N:  #若沒輸入N，則跳出迴圈
        break
    try:
        if(N!=0):
            G=0
            for i in range(1,N):
                for j in range(i+1,N+1):
                    G+=GCD(i,j)
            print(G)
        else:
            continue
    except ValueError:
        print('輸入錯誤')
```

