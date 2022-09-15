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
