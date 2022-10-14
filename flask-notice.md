# route
redirect có thể redirect func và truyền arg vào 
```python
  from flask import Flask, redirect, url_for
  
  @app.route("/<name>")
  def user(name):
      return f"Hello {name}"

  @app.route("/admin")
  def admin():
      return redirect(url_for("user", name="Admin!"))
```
# templates
- Tạo thư mục templates 
- Thêm các file base.html, index.html, page.html.....
- Gọi render_template("index.html")
```python

  @app.route("/")
  def home():
      return render_template("index.html", name="Jason", r2=['a', '12312', 'a test string co ban'])
```
# POST, GET form
- Tạo login.html và tạo form html bên trong nó
```html
  {% extends "base.html" %}
  {% block title %} Login {% endblock %}
  {% block content %}
  <form action="#" method="POST">
      <p>Name:</p>
      <p><input type="text" name="nm" id="nm" /></p>
      <p><input type="submit" value="Create" /></p>
  </form>
  {% endblock %}
```
- Gọi route("/login")
```python
  @app.route("/login", methods = ["POST", "GET"])
  def login():
      if request.method == "POST":
          username = request.form["nm"]
          return redirect(url_for("user", username=username))
      else:
          return render_template("login.html")

  @app.route("/<username>")
  def user(username):
      return f"{username}"
```
