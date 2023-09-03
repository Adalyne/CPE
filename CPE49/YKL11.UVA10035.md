# 題目 : Primary Arithmetic
Children are taught to add multi-digit numbers from right-to-left one digit at a time. Many find the "carry" operation - in which a 1 is carried from one digit position to be added to the next - to be a significant challenge. Your job is to count the number of carry operations for each of a set of addition problems so that educators may assess their difficulty.
# Input
Each line of input contains two unsigned integers less than 10 digits. The last line of input contains 0 0.  
# Output
For each line of input except the last you should compute and print the number of carry operations that would result from adding the two numbers, in the format shown below.
# Sample Input
123 456  
555 555  
123 594  
0 0  
# Sample Output
No carry operation.  
3 carry operations.  
1 carry operation.  
# 題意
有多少位數進位  
以數學的基本邏輯，若有位數進位，則該位數會比原來相加的數還要小(e.g 29+36=65，其中個位數9+6進位後為5，5<9  and 5<6)  
0加上任何數都不會進位  
# Code 
**Python**  
```ruby
def over_digits(x,y):
    if(len(str(x))>len(str(y))):
        iter=len(str(x))
        num=str(x)
    else:
        iter=len(str(y))
        num=str(y)
    count=0
    sums=str(x+y)
    for i in range(iter-1,-1,-1):
        if(iter<len(sums)):
            if(num[i]>sums[i+1]):
                count+=1
        else:
            if(num[i]>sums[i]):
                count+=1
    return count

while(True):
    n,m=map(int,input().split(' '))
    if(n==0 and m==0):
        break
    else:
        carry_digit_num=over_digits(n,m)
        if(carry_digit_num==0):
            print('No carry operation.')
        elif(carry_digit_num==1):
            print('1 carry operation.')
        else:
            print(carry_digit_num,'carry operations.')

