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
  
  # yield: su dung cho iterables
  def person_lister(f):
    def inner(people):
        # complete the function
        people.sort(key=itemgetter(2))
        for person in people:
            yield f(person)
    return inner
```

