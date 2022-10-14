# Setup Flask

## Create Virtual env
```
$ mkdir myblog
$ cd myblog
$ python3 -m venv myenv
$ virtualenv myenv
$ source myenv/bin/activate
```
## Install flask
```
(myenv) $ pip3 install flask
(myenv) $ mkdir app
```
## app/__init__.py
```
from flask import Flask
from app import routes

app = Flask(__name__)
```
## app/routes.py
```
from app import app 

@app.route('/')
@app.route('/index')

def index():
     return "Hello, World!"
```
## myblog.py
```
from app import app
```
file myblog.py nằm trong cây thư mục như thế này
```
myblog/
   myenv/
   app/
     __init__.py
     routes.py
   myblog.py
```

Trước khi chạy cần set
```
(myenv) $ export FLASK_APP=myblog.py
(myenv) $ flask run
```
Set mặc định 
```
(myenv) $ pip3 install python-dotenv
          
```
