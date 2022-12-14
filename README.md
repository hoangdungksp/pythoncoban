# Kinh nghiệm

OrderedDict : giống dict nhưng nhớ thứ tự key insert vào

{'a': 1, 'c': 3, 'b': 2, 'e': 5, 'd': 4}

OrderedDict([('a', 1), ('b', 2), ('c', 3), ('d', 4), ('e', 5)])

# Filter a list
filter(gia_tri_can_loai_bo, list)

```
function test() {
  console.log("notice the blank line before this function?");
}
```
# Date and Time
Kiem tra rat nhieu thu lien quan den calendar isleap(), weekday()...read more
```python
  import calendar
  from datetime import datetime
  #read more https://docs.python.org/3/library/calendar.html
```

# Errors and Exceptions
Kiem tra loi voi multi exceptions,
```python
  try:
    print(a/b)
  except ZeroDivisionError as e:
    print("Loi:", e)
  except ValueError as er:
    print("Loi:", er)
```
# Class
__sub__, khai bao __xyz__ la overide lại phương thức đã có sẳn
```python
  class Points(object):
    def __init__(self, x, y, z):
        self.x = x
        self.y = y
        self.z = z
    def __sub__(self, no)
      ...
```
# Built-Ins
Dung re.sub de tim va replace
Dùng eval() de chuyen string to int va operator
```python
  import re
  x=1
  lst = 'x**3'
  result = re.sub(r'x', str(x), lst)
  print(eval('2**3')) //8
```

Dùng zipped() để nối list lại với nhau tương tứng từng phần tử
```
>>> A = [1,2,3]
>>> B = [6,5,4]
>>> C = [7,8,9]
>>> X = [A] + [B] + [C]
>>> print zip(*X)
[(1, 6, 7), (2, 5, 8), (3, 4, 9)]
```
Dùng any(), all() check điều kiện
```python
  print(all([x>0 for x in lst]) and any([str(x)==str(x)[::-1] for x in lst]))
```
Dùng sorted()
```python
  # Read more -> https://docs.python.org/3/howto/sorting.html
```

# Python Functionals
map() and lambda function
Dùng map() có thể map kiểu dữ liệu, map(lambda x: x**2, function)
```python
  print (list(map(len, ['Tina', 'Raj', 'Tom'])))  
  #[4, 3, 3] 
  
  ##########################
  sum = lambda a, b, c: a + b + c
  sum(1, 2, 3) 
  #6
  
  ##########################
  cube = lambda x: x**3

  def fibonacci(n):
      # return a list of fibonacci numbers
      fibo = []
      for i in range(n):
          fibo.append(i)

      for i in range(2, len(fibo)):
          fibo[i] = fibo[i-1] + fibo[i-2]

      return fibo

  if __name__ == '__main__':
      n = int(input())
      print(list(map(cube, fibonacci(n))))
```
map() and filter()
```python
  l = list(range(10))
  l = list(map(lambda x: x*x, l))
  #[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
  
  l = list(filter(lambda x: x>10 and x<80, l))
  print(l)
  #[16, 25, 36, 49, 64]
```
reduce() đưa vào list và tính giá trị theo hàm lambda
```python
  reduce(lambda x, y : x + y,[1,2,3])
  #6
  
  reduce(lambda x, y : x + y, [1,2,3], -3)
  #3
```  
# Regex and Parsing

## Regex
Học kỹ lookaround 
```
(?=) nếu có ngay sau x thì sẽ lấy x ====> ví dụ x(?=ABC)  "xABC x1 x2" kqua lấy x của (xABC)
(?!) nếu khác ngay sau x thì sẽ lấy x ====> ví dụ x(?!ABC)  "xABC x1 x2" kqua lấy x của (x1, x2)

(?<=) nếu có ngay phía trước x thì lấy x ===> ví dụ (?<=ABC)x  "ABCx 1x 2x" kqua lấy x của (ABCx)
(?<!) nếu có ngay phía trước x thì lấy x ===> ví dụ (?<!ABC)x  "ABCx 1x 2x" kqua lấy x của (1x, 2x)

(?:) ko gộp group ví dụ (25)1\1 và  (?:25)1\1 cho 25125
```
Đọc thêm function Regex Python ở đây https://quickref.me/regex#regex-in-python


## HTML Parser
```python
from html.parser import HTMLParser

#Parse tag HTML
class MyHTMLParser(HTMLParser):
    def handle_starttag(self, tag, attrs):
        print "Found a start tag  :", tag
    def handle_endtag(self, tag):
        print "Found an end tag   :", tag
    def handle_startendtag(self, tag, attrs):
        print "Found an empty tag :", tag
        
# Parse comments and data
class MyHTMLParser(HTMLParser):
    def handle_comment(self, data):
          print "Comment  :", data
          
class MyHTMLParser(HTMLParser):
    def handle_data(self, data):
        print "Data     :", data       
```
# Closures and Decorators
Closures là gì? là iner function có quyền truy cập biến của function outter
```python
  def outter_func(name):
    def inner_func():
      return "Hello " + name
    return inner_func

  greet = outter_func('Jason')
  print(greet()) # Hello Jason
```
Decorator là gì? là bạn có thể tạo func mới để decor cho function có sẳn
Read more https://viblo.asia/p/function-decorator-trong-python-gDVK2QDe5Lj
```python
  def this_is_decorator(a_func):
    def wrap_func(name):
      print('dong thu 1')
      a_func(name)
      print('dong thu 2')
    return wrap_func

  @this_is_decorator
  def add_more_greet(name):
    print("Helo " + name)
  add_more_greet('Jason')
  
# dong thu 1
# Helo Jason
# dong thu 2

```

```python
  # Sort nested list by index
  x = [
   ['4', '21', '1', '14', '2008-10-24 15:42:58'], 
   ['3', '22', '4', '2somename', '2008-10-24 15:22:03'], 
   ['5', '21', '3', '19', '2008-10-24 15:45:45'], 
   ['6', '21', '1', '1somename', '2008-10-24 15:45:49'], 
   ['7', '22', '3', '2somename', '2008-10-24 15:45:51']
  ]

  from operator import itemgetter
  x.sort(key=itemgetter(2)) # sorted theo vi tri so 2
  x
  
  sorted(x, key=lambda x:int(x[2]) #Luu y ep kieu du lieu cho gia tri can sorted
  x
  
  # yield: su dung cho iterables
  def person_lister(f):
    def inner(people):
        # complete the function
        people.sort(key=itemgetter(2))
        for person in people:
            yield f(person)
    return inner
```

# Numpy (Dong x Cot)
Giống với list chỉ có điều là mỗi elememnt trong array phải giống kiểu (same type)

## numpy.shape
- Use shape to get array dimensions
- Use shape to change array dimensions
```python
  my__1D_array = numpy.array([1, 2, 3, 4, 5])
  print my_1D_array.shape     #(5,) -> 1 row and 5 columns

  import numpy

  change_array = numpy.array([1,2,3,4,5,6])
  change_array.shape = (3, 2)
  print change_array      

  #Output
  [[1 2]
  [3 4]
  [5 6]]
```
## numpy.reshape 
- Dùng để tạo mới shape cho array mà không thay đổi giá trị

## numpy.transpose
- Tạo mới và xoay array

## flatten
- Làm phẳng numpy array thanh 1 dimension
```python
  arr = numpy.arry(a_list)
  arr.flatten()
```
## concatenated : ghép lại, nối lại
- Dùng để dép numpy.array lại với nhau
- Nếu numpy.array nhiều hơn 1 dimension thì chọn axis cần ghép lại
```python
  import numpy

  array_1 = numpy.array([1,2,3])
  array_2 = numpy.array([4,5,6])
  array_3 = numpy.array([7,8,9])

  print numpy.concatenate((array_1, array_2, array_3))    

  #Output
  [1 2 3 4 5 6 7 8 9]
```
```python
  # Nhiều hơn 1 dimension
  import numpy

  array_1 = numpy.array([[1,2,3],[0,0,0]])
  array_2 = numpy.array([[0,0,0],[7,8,9]])

  print numpy.concatenate((array_1, array_2), axis = 1)   

  #Output
  [[1 2 3 0 0 0]
   [0 0 0 7 8 9]]   
```
## zeros and ones
## numpy.identity and numpy.eye 

```python
  print numpy.identity(3)
  #Output
  [[ 1.  0.  0.]
   [ 0.  1.  0.]
   [ 0.  0.  1.]]
 
   print numpy.eye(8, 7, k = 1)
   #Output
  [[ 0.  1.  0.  0.  0.  0.  0.]
   [ 0.  0.  1.  0.  0.  0.  0.]
   [ 0.  0.  0.  1.  0.  0.  0.]
   [ 0.  0.  0.  0.  1.  0.  0.]
   [ 0.  0.  0.  0.  0.  1.  0.]
   [ 0.  0.  0.  0.  0.  0.  1.]
   [ 0.  0.  0.  0.  0.  0.  0.]
   [ 0.  0.  0.  0.  0.  0.  0.]]
```

## Function Operator element-wise
```python
  import numpy

  a = numpy.array([1,2,3,4], float)
  b = numpy.array([5,6,7,8], float)

  print a + b                     #[  6.   8.  10.  12.]
  print numpy.add(a, b)           #[  6.   8.  10.  12.]

  print a - b                     #[-4. -4. -4. -4.]
  print numpy.subtract(a, b)      #[-4. -4. -4. -4.]

  print a * b                     #[  5.  12.  21.  32.]
  print numpy.multiply(a, b)      #[  5.  12.  21.  32.]

  print a / b (python3 a//b)      #[ 0.2         0.33333333  0.42857143  0.5       ]
  print numpy.divide(a, b)        #[ 0.2         0.33333333  0.42857143  0.5       ]

  print a % b                     #[ 1.  2.  3.  4.]
  print numpy.mod(a, b)           #[ 1.  2.  3.  4.]

  print a**b                      #[  1.00000000e+00   6.40000000e+01   2.18700000e+03   6.55360000e+04]
  print numpy.power(a, b)         #[  1.00000000e+00   6.40000000e+01   2.18700000e+03   6.55360000e+04
```

## numpy.floor, numpy.ceil, numpy.rint
- floor: làm lấy giá trị thấp nhất của i <= x
```python
  my_array = numpy.array([1.1, 2.2, 3.3, 4.4, 5.5, 6.6, 7.7, 8.8, 9.9])
  print numpy.floor(my_array)         #[ 1.  2.  3.  4.  5.  6.  7.  8.  9.]
```
- ceil: làm lấy giá trị lớn nhất của i >= x
```python
  my_array = numpy.array([1.1, 2.2, 3.3, 4.4, 5.5, 6.6, 7.7, 8.8, 9.9])
  print numpy.ceil(my_array)          #[  2.   3.   4.   5.   6.   7.   8.   9.  10.]
```
- rint: làm tròn 5.5 -> 6
```python
  my_array = numpy.array([1.1, 2.2, 3.3, 4.4, 5.5, 6.6, 7.7, 8.8, 9.9])
  print numpy.rint(my_array)          #[  1.   2.   3.   4.   6.   7.   8.   9.  10.]
```

## numpy.sum and numpy.prod
```python
  my_array = numpy.array([ [1, 2], [3, 4] ])

  print numpy.sum(my_array, axis = 0)         #Output : [4 6]
  print numpy.sum(my_array, axis = 1)         #Output : [3 7]
  print numpy.sum(my_array, axis = None)      #Output : 10
  print numpy.sum(my_array)                   #Output : 10
  
  #prod is product 
  my_array = numpy.array([ [1, 2], [3, 4] ])

  print numpy.prod(my_array, axis = 0)            #Output : [3 8]
  print numpy.prod(my_array, axis = 1)            #Output : [ 2 12]
  print numpy.prod(my_array, axis = None)         #Output : 24
  print numpy.prod(my_array)                      #Output : 24
```
## min and max
```python
  my_array = numpy.array([[2, 5], 
                          [3, 7],
                          [1, 3],
                          [4, 0]])

  print numpy.min(my_array, axis = 0)         #Output : [1 0]
  print numpy.min(my_array, axis = 1)         #Output : [2 3 1 0]
  print numpy.min(my_array, axis = None)      #Output : 0
  print numpy.min(my_array)                   #Output : 0
```

```python
  my_array = numpy.array([[2, 5], 
                        [3, 7],
                        [1, 3],
                        [4, 0]])

  print numpy.max(my_array, axis = 0)         #Output : [4 7]
  print numpy.max(my_array, axis = 1)         #Output : [5 7 3 4]
  print numpy.max(my_array, axis = None)      #Output : 7
  print numpy.max(my_array)                   #Output : 7
```
## numpy.dot dot product and numpy.cross cross product
- Dot product cua 2 vector sẽ tạo vector mới bất kì 
- Cross product của 2 vector sẽ tạo ra vector mới vuông góc với 2 vector kia

## inner product and outer product
```python
  x = [x1,
       x2,
       x3]
  y = [y1,
       y2,
       y3]   
  iner product = scalar
  x^T.y = [x1, x2. x3]. [y1] = x1y1 + x2y2 + x3y3
                        [y2]
                        [y3]   
  outer product = matrix
  x.y^T = [x1] .[y1, y2 y3] = [[x1,y1 x2y2 x3y3], [x2,y1 x2y2 x2y3], [x3,y1 x3y2 x3y3]]
          [x2]
          [x3]
                    
```
## poly, roots, polyint, polyer, polyval, polyfit
https://www.mathsisfun.com/algebra/polynomials.html

## linalg.det,  linalg.eig, linalg.inv
https://www.mathsisfun.com/algebra/matrix-determinant.html
https://www.mathsisfun.com/algebra/eigenvalue.html
