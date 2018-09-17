### Numpy

Numpy는 파이썬이 계산과학분야에 이용될때 핵심 역할을 하는 라이브러리입니다. Numpy는 고성능의 다차원 배열 객체와 이를 다룰 도구를 제공합니다. 만약 MATLAB에 익숙한 분이라면 Numpy 학습을 시작하는데 있어 이 튜토리얼이 유용할 것입니다.

[Numpy 메뉴얼](http://aikorea.org/cs231n/python-numpy-tutorial/#numpy-arrays)

```python
import numpy as np

a = np.array([1, 2, 3]) 
print (type(a))
print (a.shape)            
print (a[0], a[1], a[2])   
a[0] = 5                 
print (a)                  

b = np.array([[1,2,3],[4,5,6]])  
print (b.shape)                     
print (b[0, 0], b[0, 1], b[1, 0])  
```
