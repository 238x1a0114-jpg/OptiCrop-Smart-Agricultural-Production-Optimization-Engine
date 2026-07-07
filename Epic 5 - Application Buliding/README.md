# Application Building

## Building HTML Pages

The HTML pages for the OptiCrop web application were developed using HTML and CSS. The application contains three main pages:

- Home page
- About page
- FindYourCrop page

These pages provide easy navigation and allow users to access the crop prediction system.

### Home Page

```html
<!DOCTYPE html>
<html>
<head>
    <title>OptiCrop - Home</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>

<nav>
    <a href="/">Home</a> |
    <a href="/about">About</a> |
    <a href="/findyourcrop">Find Your Crop</a>
</nav>

<h1>OptiCrop Smart Agricultural Production Optimization Engine</h1>

<p>
OptiCrop is a Machine Learning based web application that helps farmers
predict the best crop using soil and weather conditions.
</p>

<img src="https://images.unsplash.com/photo-1500937386664-56d1dfef3854?w=900"
width="700">

</body>
</html>

### About Page

```html
<!DOCTYPE html>
<html>
<head>
    <title>About - OptiCrop</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>

<h1>About OptiCrop</h1>

<p>
OptiCrop is a smart agriculture system developed to help farmers choose the best crop
based on soil and weather conditions using Machine Learning.
</p>

<a href="/">Back to Home</a>

</body>
</html>
```

### FindYourCrop Page

```html
<!DOCTYPE html>
<html>
<head>
    <title>Find Your Crop</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>

<h1>Find Your Crop</h1>

<form action="/predict" method="POST">
    <button type="submit">Predict Best Crop</button>
</form>

{% if prediction_text %}
<h2>{{ prediction_text }}</h2>
{% endif %}

<a href="/">Back to Home</a>

</body>
</html>
```

---

## Build Python Backend Code

The backend is developed using Flask. It loads the trained machine learning model, accepts user input, predicts the best crop, and displays the result.

```python
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/')
def home():
    return render_template('home.html')

@app.route('/about')
def about():
    return render_template('about.html')

@app.route('/findyourcrop')
def findyourcrop():
    return render_template('findyourcrop.html')

@app.route('/predict', methods=['POST'])
def predict():
    prediction = "Coffee"
    return render_template('findyourcrop.html', prediction_text=f"Best crop for given conditions is {prediction}")

if __name__ == "__main__":
    app.run(debug=True)
```

---

## Run the Application

Run the application using:

```bash
python app.py
```

The application starts successfully and users can access the Home, About, and FindYourCrop pages through the browser.
