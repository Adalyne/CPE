# 題目  
You‘re given a square matrix M. Elements of this matrix are Mij : {0<i<n, 0<j<n}. In this problem you’ll have to find out whether the given matrix is symmetric or not.  
Definition: Symmetric matrix is such a matrix that all elements of it are non-negative and symmetric with relation to the center of this matrix. Any other matrix is considered to be non-symmetric.  
For example:
M =  

5 1 3  
2 0 2  
3 1 5  

M is symmetric  

M =  

5 1 3  
2 0 2  
0 1 5   
  
M is not symmetric, because 3 ̸= 0  
All you have to do is to find whether the matrix is symmetric or not. Elements of a matrix given in the input are −2exp(32) ≤ Mij ≤ 2exp(32) and 0<n ≤ 100.  

# Input  
First line of input contains number of test cases T ≤ 300. Then T test cases follow each described in the following way. The first line of each test case contains n – the dimension of square matrix.  
Then n lines follow each of then containing row i. Row contains exactly n elements separated by a space character. j-th number in row i is the element Mij of matrix you have to process.  

# Output  
For each test case output one line ‘Test #t: S’. Where t is the test number starting from 1. Line S is equal to ‘Symmetric’ if matrix is symmetric and ‘Non-symmetric’ in any other case.

# Sample Input  
2  
N = 3  
5 1 3  
2 0 2  
3 1 5  
N = 3  
5 1 3  
2 0 2  
0 1 5  

# Sample Output  
Test #1: Symmetric.  
Test #2: Non-symmetric.  

# 題意  
判斷矩陣是否對秤，但這題的對稱不是課本所定義的矩陣對稱，對稱的定義在題目說，若矩陣index 0 和最後一個的index 相同、 index 1 和倒數第二個index 相同、 index 2 和倒數第三個index 相同... 且元素均大於等於0，則對稱(Symmetric)  
，否則非對稱(Non-symmetric)  

# Code 
**Python**
```ruby
import numpy as np

def detect(arr):
    flat_arr=arr.flatten()
    i=0
    j=np.size(arr)-1
    tag=0
    while(i!=j):
        if(flat_arr[i]!=flat_arr[j] or flat_arr[i]<0):
            tag=1
            break
        print(i,j)
        i+=1
        j-=1
        if((i-1)==j):
            break
    return tag
    

max_num=int(input())
for num in range(max_num):
    n=int(input().split(' ')[2])
    arr=[]
    for i in range(n):
        arr.append(list(map(int,input().rstrip().split())))
    array=np.array(arr)
    tag=detect(array)
    if(tag==0):
        print('Test #{0}: Symmetric.'.format(num+1))
    else:
        print('Test #{0}: Non-symmetric.'.format(num+1))
```
