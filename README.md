# Ex.05 Design a Website for Server Side Processing
# Date:04-10-2025
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
min.html:

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Bulb Power Calculator</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #89f7fe, #66a6ff);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .container {
            background: #ffffff;
            padding: 30px 40px;
            border-radius: 15px;
            box-shadow: 0px 6px 15px rgba(0,0,0,0.2);
            text-align: center;
            width: 350px;
        }

        h1 {
            color: #2c3e50;
            font-size: 22px;
            margin-bottom: 20px;
        }

        label {
            display: block;
            text-align: left;
            font-weight: 600;
            margin-bottom: 5px;
            color: #333;
        }

        input {
            width: 100%;
            padding: 10px;
            border: 1px solid #bbb;
            border-radius: 8px;
            margin-bottom: 15px;
            font-size: 14px;
        }

        button {
            background: #3498db;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 8px;
            font-size: 15px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s ease;
        }

        button:hover {
            background: #2980b9;
        }

        .result {
            margin-top: 20px;
            padding: 10px;
            background: #ecf0f1;
            border-radius: 8px;
            font-size: 16px;
            color: #2c3e50;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Bulb Power Calculator</h1>
        <form method="post">
            {% csrf_token %}
            <label for="intensity">Current (I in Amps)</label>
            <input type="text" id="intensity" name="intensity" required>

            <label for="resistance">Resistance (R in Ohms)</label>
            <input type="text" id="resistance" name="resistance" required>

            <button type="submit">Calculate</button>
        </form>

        {% if power != None %}
        <div class="result">
            Power (P) = {{ power }} W
        </div>
        {% endif %}
    </div>
</body>
</html>

views.py:

from django.shortcuts import render

def power_calculator(request):
    power = None
    if request.method == 'POST':
        print("POST METHOD IS USED")
        intensity=request.POST.get('intensity','0')
        resistance=request.POST.get('resistance','0')
        print('request=',request)
        print('intensity=',intensity)
        print('resistance=',resistance)
  
        intensity = request.POST.get('intensity')
        resistance = request.POST.get('resistance')
        if intensity and resistance:
            try:
                I = float(intensity)
                R = float(resistance)
                power = I**2 * R
                print('power=',power)
            except ValueError:
                power = "Invalid input. Please enter numeric values."
    return render(request, 'app/min.html', {'power': power})

    urls.py:

    from django.urls import path
from app.views import power_calculator

urlpatterns = [
    path('', power_calculator, name='power_calculator'),
]

```
# SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-10-04 223952.png>)
# HOMEPAGE:
![alt text](<Screenshot 2025-10-04 223902.png>)
# RESULT:
The program for performing server side processing is completed successfully.
