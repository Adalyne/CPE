# 題目:  
The well known Fibonacci sequence is obtained by starting with 0 and 1 and then adding the two last numbers to get the next one. For example the third number in the sequence is 1 (1=1+0), the forth is 2 (2=1+1), the fifth is 3 (3=2+1) and so on.   
![image](https://github.com/Adalyne/CPE/blob/31e436664804d855afde8cf7deb26156c7854755/CPE49/Fibonacci.png)

The sequence appears on many things in our life, in nature, and has a great significance. Among other things, do you know that all positive integer numbers can be represented as a sum of numbers in the Fibonacci sequence? More than that, all positive integers can be represented as a sum of a set of Fibonacci numbers, that is, numbers from the sequence, without repetition. For example: 13 can be the sum of the sets {13}, {5,8} or {2,3,8} and 17 is represented by {1,3,13} or {1,3,5,8}. Since all numbers have this property (do you want to try to prove this for yourself?) this set could be a nice way to use as a "base" to represent the number. But, as we have seen, some numbers have more than one set whose sum is the number. How can we solve that? Simple! If we add the constraint that the sets cannot have two consecutive Fibonacci numbers, than we have a unique representation for each number! This restriction is because the sum of any two consecutive Fibonacci numbers is just the following Fibonacci number.
Now that we know all this we can prepare a nice way to represent any positive integer. We will use a binary sequence (just zeros and ones) to do that. For example,17 = 1 + 3 + 13 (remember that no two consecutive Fibonacci numbers can be used). Let's write a zero for each Fibonacci number that is not used and one for each one that is used, starting at the right. Then, 17 = 100101. See figure 2 for a detailed explanation. In this representation we should not have zeros at the left, this is, we should only write starting with the first one. In order for you to understand better, note that in this scheme, not using two consecutive Fibonacci numbers means that the binary sequence will not have two consecutive ones. When we use this representation for a number we say that we are using the Fibonaccimal base, and we write it like 17 = 100101 (fib).
![image](https://github.com/Adalyne/CPE/blob/5fb1994eccd4eab64d4e7a3031f4a51ce420499f/CPE49/Fibonacci%20base.png).

# Description   
Given a set of numbers in decimal base, your task is to write them in the Fibonaccimal base.

# Input
The first line of input contains a single number N, representing the quantity of numbers that follow ( 1 ≤ N ≤ 500).
Than follow exactly N lines, each one containing a single positive integer smaller than 100 000 000. These numbers can come in any order.

# Output
You should output a single line for each of the N integers in the input, with the format "DEC_BASE = FIB_BASE (fib)". DEC_BASE is the original number in decimal base and FIB_BASE is its representation in Fibonaccimal base. See the sample output for an example.


# Sanple Input  
10  
1   
2   
3  
4  
5  
6  
7  
8  
9  
10  

# Sample Output  
1 = 1 (fib)  
2 = 10 (fib)  
3 = 100 (fib)  
4 = 101 (fib)  
5 = 1000 (fib)  
6 = 1001 (fib)  
7 = 1010 (fib)  
8 = 10000 (fib)  
9 = 10001 (fib)   
10 = 10010 (fib)  

# 題意    
將10進位的數字換成以Fibonacci base為底的bin  
所以先將Fibonacci的矩陣儲存起來，運算會比較快  
然後像二進位的方式一樣寫法，只記錄整數除法直到數字為零  
# Code 
**Python**  
```ruby  
def fib(n):
    Fib=list() #因為list可以當一維陣列用，用numpy一維陣列也可
    Fib.append(0)
    Fib.append(1)
    Fib.append(1)
    for i in range(3,n+1):  
        Fib.append(Fib[i-1]+Fib[i-2])
    return Fib

while True:
    input_num=int(input())
    if not input_num:
        break
    try:
        fib_n=40  #因為測資的範圍，可以開 40 格就夠 (因為 [40] = 102334155 超過範圍)
        Fib_list=fib(fib_n)
        for i in range(1,input_num+1):
            input_num=int(input())
            num=input_num
            index=fib_n
            bit_str=''
            tag=0  #因為不紀錄前面開頭為0，開始數字1後面開始加進str
            while index!=1:
                bit=num//Fib_list[index]
                num=num%Fib_list[index]
                if bit==1:
                    tag=1 
                if tag==1:
                    bit_str+=str(bit)
                index-=1
            print(input_num,'=',int(bit_str.replace('\n','').replace('\r','')),'(fib)')  #最後的格式為1=1(fib), 所以將\r\n換掉，以免換行或空格導致格式不對
    except ValueError:
        print('輸入錯誤')
```
