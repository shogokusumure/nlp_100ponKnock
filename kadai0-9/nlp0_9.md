

```python
txt = 'stressed'
reversed_txt= list(reversed(txt))
str_txt = ''.join(reversed_txt)
print(str_txt)
```

    desserts



```python
txt = 'パタトクカシーー'
listed_txt = list(txt)
ans = listed_txt[0] + listed_txt[2] + listed_txt[4] + listed_txt[6]

print(ans)
```

    パトカー



```python
txt1 = 'パトカー'
txt2 = 'タクシー'
listed_txt1 = list(txt1)
listed_txt2 = list(txt2)

len1 = len(listed_txt1)
len2 = len(listed_txt2)

if abs(len1-len2) > 1:
    print('テキストの長さがあいません')
else:
    ans = ''
    for i in range(len1):
        ans +=  listed_txt1[i] + listed_txt2[i]
    print(ans)
```

    パタトクカシーー



```python
txt = 'Now I need a drink, alcoholic of course, after the heavy lectures involving quantum mechanics.'
# 句読点消し
txt = txt.replace(',','')
txt = txt.replace('.','')

word_list = txt.split(' ')
ans = []
for i in word_list:
    ans.append(len(i))

print(ans)
```

    [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5, 8, 9, 7, 9]



```python
txt = 'Hi He Lied Because Boron Could Not Oxidize Fluorine. New Nations Might Also Sign Peace Security Clause. Arthur King Can.'
# 句読点消し
txt = txt.replace(',','')
txt = txt.replace('.','')

single_list = [1,5,6,7,8,9,15,16]

word_list = txt.split(' ')
ans = {}
for i,name in enumerate(word_list):
    if i + 1 in single_list:
        ans[name[:1]] = i
        continue
    ans[name[:2]] = i

print(ans)
```

    {'H': 0, 'He': 1, 'Li': 2, 'Be': 3, 'B': 4, 'C': 5, 'N': 6, 'O': 7, 'F': 8, 'Ne': 9, 'Na': 10, 'Mi': 11, 'Al': 12, 'Si': 13, 'P': 14, 'S': 15, 'Cl': 16, 'Ar': 17, 'Ki': 18, 'Ca': 19}



```python
def createNgram(str, mode):
    ans = []
    if mode == 'moji':
        devidedTxt = list(str)
        length = len(devidedTxt)
        for i in range(length - 1):
            ans.append(devidedTxt[i] + devidedTxt[i + 1])
    elif mode == 'word':
        str = txt.replace(',','')
        str = txt.replace('.','')
        
        devidedTxt = str.split(' ')
        length = len(devidedTxt)
        for i in range(length - 1):
            ans.append(devidedTxt[i] + ' ' + devidedTxt[i + 1])
    else:
        return '無効なモードです'    
    return ans

txt = 'I am an NLPer'
print(createNgram(txt,'moji'))
print(createNgram(txt,'word'))
```

    ['I ', ' a', 'am', 'm ', ' a', 'an', 'n ', ' N', 'NL', 'LP', 'Pe', 'er']
    ['I am', 'am an', 'an NLPer']


## 06. 集合
"paraparaparadise"と"paragraph"に含まれる文字bi-gramの集合を，それぞれ, XとYとして求め，XとYの和集合，積集合，差集合を求めよ．さらに，'se'というbi-gramがXおよびYに含まれるかどうかを調べよ


```python
txt1 = 'paraparaparadise'
txt2 = 'paragraph'

list1 = set(createNgram(txt1,'moji'))
list2 = set(createNgram(txt2,'moji'))

print(list1 | list2)
print(set(list1 & list2))
print(list1 - list2)

list(list1)
print('se' in list1)
list(list2)
print('se' in list2)
```

    {'se', 'ap', 'pa', 'ag', 'ra', 'ph', 'ar', 'gr', 'is', 'ad', 'di'}
    {'ra', 'ar', 'pa', 'ap'}
    {'se', 'is', 'ad', 'di'}
    True
    False



```python
def makeSentence(x,y,z):
    return str(x)+'時の'+str(y)+'は'+str(z)

makeSentence(12, '気温', 22.4)
```




    '12時の気温は22.4'




```python
def cipher(str):
    str_list = list(str)
    
    ans = ''
    for i in str_list:
        if i.islower():
            ans += chr(219-ord(i))
        else:
            ans += i
            
    return ans

print (cipher('I have a Pen.'))
print (cipher(cipher('I have a Pen.')))
```

    I szev z Pvm.
    I have a Pen.



```python
txt = "I couldn't believe that I could actually understand what I was reading : the phenomenal power of the human mind ."
import random

def shuffleTxt(str):
    word_list = str.split(' ')
    ans = ''
    for var in word_list:
        if len(var) > 3:
            head = var[:1]
            body = var[1:-1]
            foot = var[-1:]        
            body_list = list(body)
            random.shuffle(body_list)
        
            shuffled = head + ''.join(body_list) + foot
        else:
            shuffled = var
        
        ans += shuffled + ' ' 
        
    return ans
    
shuffleTxt(txt)
```




    "I cdnlo'ut bleeive that I cuold alluctay uratednsnd waht I was rniaedg : the poennamehl pwoer of the hamun mnid . "


