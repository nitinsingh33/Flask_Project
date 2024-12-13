### **What is Flask?**

Flask is a lightweight, easy-to-use web framework written in Python. It is widely used for developing web applications and APIs due to its simplicity and flexibility.

#### Key Features:
1. **Lightweight and Modular**: Minimal setup, you can add components as needed.
2. **Routing**: Maps URLs to specific functions in your code.
3. **Templating**: Uses Jinja2 for dynamic HTML rendering.
4. **Extensions**: Integrates easily with libraries for forms, databases, and authentication.
5. **Development Server**: Built-in server with debugging tools.
6. **WSGI Compatibility**: Based on Werkzeug, a WSGI toolkit.

---


### **Key Concepts**

1. **Routing**:
   Define URL paths using `@app.route()`. You can also use variables in the URL.
   ```python
   @app.route('/user/<username>')
   def show_user_profile(username):
       return f'User: {username}'
   ```

2. **HTTP Methods**:
   Flask supports `GET`, `POST`, `PUT`, `DELETE`, etc.
   ```python
   @app.route('/submit', methods=['POST'])
   def submit():
       return 'Form Submitted'
   ```

3. **Templates**:
   Flask uses Jinja2 for templating. Create an HTML file in the `templates/` directory.
   ```html
   <!-- templates/index.html -->
   <html>
   <body>
       <h1>Hello, {{ name }}!</h1>
   </body>
   </html>
   ```
   ```python
   from flask import render_template

   @app.route('/greet/<name>')
   def greet(name):
       return render_template('index.html', name=name)
   ```

4. **Static Files**:
   Store static files (CSS, JS, images) in a `static/` directory.
   ```html
   <link rel="stylesheet" type="text/css" href="{{ url_for('static', filename='style.css') }}">
   ```

5. **Database Integration**:
   Use libraries like `SQLAlchemy` for database management.

---




 

