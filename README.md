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
