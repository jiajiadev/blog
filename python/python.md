# Python Programming

##python中单引号(')、双引号（")和三引号（""")
  1.三种引号都表示字符串<br>
  2.单引号和双引号都表示单行的字符串<br>
  3.三个双引号表示的字符串可以分行写，主要用在某个函数或者类的功能描述文档。 <br>
  如： <br>
     s1="hello,python" <br>
  如果写成多行，就要使用 /n <br>
      s2="hello,<br>
     /npython" <br>
  但三引号可以直接换行写： <br>
     s1="""hello,<br>
     python"""
     
--------------------------------------------------------------------------
##list的基本操作
1.创建list:列表是由[ ]定义的
```
>>>list=['a','b','c','d']
```
2.访问list:列表索引下标从0开始，0是第一个元素，-1是最后一个元素,依次地，-2是倒数第二个元素；也可通过切片操作访问列表
```
>>>list[0]
'a'
>>>list[-1]
'd'
>>>list[1:3]
['b','c']
>>>list[:1]
['a']
```
3.更新list：
* 可以通过append( )方法添加元素到列表的末尾
* 通过insert( )插入一个新元素或更新原来位置的元素
* 直接通过指定索引来更新元素
```
>>>list.append("I am new here")
>>>list
['a','b','c','d','I am new here']
>>>list.insert(1,'Hello')
>>>list
['a','Hello','b','c','d','I am new here']
>>>list[2]='yes'
>>>list
['a','Hello','yes','c','d','I am new here']
```
4.删除list的元素
* 用del语句删除已知索引的元素
* 用remove( )方法直接删除元素
* 用pop( )方法来删除并返回一个特定对象
```
>>>del list[1]
>>>list
['a','yes','c','d','I am new here']
>>>list.remove('yes')
>>>list
['a','c','d','I am new here']
>>>list.pop(1)
'c'
>>>list
['a','d','I am new here']
```
##dict的基本操作
1.字典的创建：
```
>>>dict={1:'A',2:'B',3:'C'}
>>>dict
{1:'A',2:'B',3:'C'}
```
2.字典的修改：
```
>>>dict[4]='D' #添加
>>>dict
{1:'A',2:'B',3:'C',4:'D'}
>>>dict[1]='Q' #更新
>>>dict
{1:'Q',2:'B',3:'C',4:'D'} 
```
3.字典的删除：
```
>>>del dict[1]   #删除键为1的条目
>>>dict
{2:'B',3:'C',4:'D'}
>>>dict.clear( )   #删除dict的所有条目
>>>del dict     #删除整个字典
```
4.字典的遍历：
* 通过key 遍历
```
>>>dict={1:'A',2:'B',3:'C'}
>>>for k in dict:
       print "dict[%s]="% k,dict[k]
dict[1]=A
dict[2]=B
dict[3]=C
```
* 调用items( )实现字典的遍历
```
>>>dict={1:'A',2:'B',3:'C'}
>>>print dict.items()
[(1,'A'),(2,'B'),(3,'C')]
>>>for (k,v) in dict.items():
       print "dict[%s]="% k,v
dict[1]=A
dict[2]=B
dict[3]=C
```
5.输出key、value的列表：
```
>>>print dict.keys()
[1,2,3]
>>>print dict.values()
['A','B','C']
```

## Get Public IP 
Get host public IP address when it is behind firewall or NAT.
```
>>>import ipgetter
>>> myip = ipgetter.myip()

## Pip

1. Install
```
pip install package_name
```

2. Upgrade
```
pip install package_name --upgrade
```

2.1 Upgrade on Mac OS

```
pip install package_name --upgrade --user
```



