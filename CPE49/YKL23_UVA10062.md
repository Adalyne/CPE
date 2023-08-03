# 題目  
Give a line of text you will have to find out the fequencies of the ASCII characters present in it.  
The given lines will contain none of the first 32 or last 128 ASCII characters.  
Of course lines may end with \n and \r but always keep those out of consideration.  

# Input
Several lines of text are given as input. Each line of text is cconsidered as a single input. Maximum length of each line is 1000.  

# Output
Print the ASCII value of the ASCII characters which are present and their freqeuncy according to the given format below.  
A blank line should separate each set of output. Print the Ascii characters in the ascending order of their frequencies.  
If two characters are present the same time print the information of the ASCII character with higher ASCII vakue first.  
Input is terminated by end of file.  

# Sample Input  
AAABBC  
122333  

# Sample Output  
67 1  
66 2  
65 3  

49 1  
50 2  
51 3  

# 題意
將input的數字和字元轉成 **ASCII code** 編號後，編號由大排到小，output為字元和數字出現的頻率且按照頻率由小到大  
**Note**: 因為output的格式是先頻率由小到大，再排ASCII 編號由大到小，還有一個地方要注意，每一組輸入的輸出要用"行"隔開，由於python的print會自動幫你換行，所以不能直接在每一組答案後面加上\n(因為會有空兩行，不符合格是要求)，所以我是在印print之前加入\n，第一組資料的輸出不要印\n`.  

# Code
**Python**
```ruby
def ascii(content):  #將數字和字元轉成ASCII編號，存在lsit中
    mylist=[]
    for i in content:
        num=ord(i)
        mylist.append(num)
    return mylist
    
def frequency(content_list):
    mydict={}
    for item in content_list:
        if mydict.__contains__(item):  #檢查元素是否在字典裡?有，則+1;否則，增新在字典並把value設1
            mydict[item]+=1
        else:
            mydict[item]=1
    return mydict

cnt=0  #計算第幾組測資(輸入)
while True:
    input_str=input()
    cnt+=1
    if not input_str:
        break
    try:
        mylist=ascii(input_str)
        mylist.sort(reverse=True) #將list由大到小排序
        mydict=frequency(mylist)
        new_dict=sorted(mydict.items(), key=lambda x:x[1])  #將frequency由小到大排序
        if(cnt!=1):  #若為第一組測資，前面不要空行
            print('')
        for k in new_dict:
            print(k[0],k[1])
    except ValueError:
        print('輸入錯誤')
```
