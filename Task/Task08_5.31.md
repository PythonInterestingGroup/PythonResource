## Task
##### 1. 廖雪峰函数式编程中 **返回函数** 和 **匿名函数** 部分
##### 2. 理解下面两段代码输出的值为何不同  

```python
def count_v1():
	fs = []
	for i in range(1,4):
		def f():
			return i * i
		fs.append(f)
	return fs
	
f1,f2,f3 = count_v1()
print("f1:",f1(),"f2:",f2(),"f3:",f3())

	
def count_v2():
	def f(j):
		def g():
			return j*j
		return g
	fs = []
	for i in range(1,4):
		fs.append(f(i))
	return fs

f4,f5,f6 = count_v2()
print("f4:",f4(),"f5:",f5(),"f6:",f6())
```  
如果上面的不是特别明白，可以看下下面的代码

```python
def test_closure_1():
	f = []
	i = 1
	
	def func():
		return i * i
	
	f.append(func)
	i += 1
	f.append(func)
	i += 1
	f.append(func)

	return f
func1,func2,func3 = test_closure_1()
print("func1:",func1(),"func2:",func2(),"func3:",func3())


def test_closure_2():
	f = []
	i = 1
	
	def func(i):
		def g():
			return i * i
		return g
	
	f.append(func(i))
	i += 1
	f.append(func(i))
	i += 1
	f.append(func(i))
	return f
	
func4,func5,func6 = test_closure_2()
print("func4:",func4(),"func5:",func5(),"func6:",func6()) 
```  

##### 3. lamdba表达式，上面代码中哪些部分可以用lambda替换，替换之