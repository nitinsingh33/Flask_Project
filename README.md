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




 
    tasks.append({'task': task, 'completed': False})
    return redirect(url_for('index'))

@app.route('/complete/<int:task_id>')
def complete_task(task_id):
    if 0 <= task_id < len(tasks):
        tasks[task_id]['completed'] = True
    return redirect(url_for('index'))

if __name__ == '__main__':
    app.run(debug=True)
```

**2. templates/index.html**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
    <title>To-Do List</title>
</head>
<body>
    <h1>To-Do List</h1>
    <form action="/add" method="post">
        <input type="text" name="task" placeholder="New Task" required>
        <button type="submit">Add</button>
    </form>
    <ul>
        {% for task in tasks %}
        <li style="text-decoration: {{ 'line-through' if task.completed else 'none' }};">
            {{ task.task }}
            {% if not task.completed %}
            <a href="{{ url_for('complete_task', task_id=loop.index0) }}">Mark as Completed</a>
            {% endif %}
        </li>
        {% endfor %}
    </ul>
</body>
</html>
```

**3. static/style.css**
```css
body {
    font-family: Arial, sans-serif;
    margin: 20px;
    line-height: 1.6;
}

h1 {
    color: #333;
}

form {
    margin-bottom: 20px;
}

ul {
    list-style-type: none;
    padding: 0;
}
```

#### **Run and Test**:
1. Start the server:
   ```bash
   python app.py
   ```
2. Open `http://127.0.0.1:5000` in your browser.

---

### **Upload to GitHub**
1. Create a GitHub repository.
2. Initialize Git in your project folder:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin <repository-URL>
   git push -u origin main
   ```

Let me know if you need help with any part of this!
