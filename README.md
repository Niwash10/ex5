# Ex.05 Design a Website for Server Side Processing
## Date:26-09-2025

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
volume = l*b*h
<br> l --> length
<br> b --> breath
<br> h --> height

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
~~~

math.html

<!DOCTYPE html>
<html>
<head>
    <title>Volume of a Rectangle</title>
    <style>
        body {
            color: orange;
            text-align: center;
            margin-top: 7px;
            margin-bottom: 6px;
            padding-top: 20px;
        }
        h1 {
            color: rgb(255, 0, 179);
            text-align: center;
        }
        .edge {
            margin: 0 auto;
            width: 400px;
            border: 1px solid #ccc;
            padding: 20px;
            border-radius: 8px;
            background: #f9f9f9;
        }
        .formelt {
            margin-bottom: 12px;
        }
    </style>
</head>
<body>
    <div class="edge">
        <div class="box">
            <h1>Volume of a Rectangle</h1>
            <form method="POST">
                {% csrf_token %}
                <div class="formelt">
                    Length : <input type="text" name="length" value="{{ l }}"> (in)
                </div>
                <div class="formelt">
                    Breadth : <input type="text" name="breadth" value="{{ b }}"> (in)
                </div>
                <div class="formelt">
                    Height : <input type="text" name="height" value="{{ h }}"> (in)
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate">
                </div>
                <div class="formelt">
                    Volume : <input type="text" name="volume" value="{{ volume }}"> (in<sup>3</sup>)
                </div>
            </form>
        </div>
    </div>
</body>
</html>
<html>
<head>

views.py

from django.shortcuts import render

def rectvolume(request):
    context = {}
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length', '0')
        b = request.POST.get('breadth', '0')
        h = request.POST.get('height', '0')
        print('request-', request)
        print('Length=', l)
        print('Breadth=', b)
        print('Height=', h)
        try:
            volume = int(l) * int(b) * int(h)
        except ValueError:
            volume = 0
        context['volume'] = volume
        context['l'] = l
        context['b'] = b
        context['h'] = h
        print('Volume-', volume)
    return render(request, 'mathapp/math.html', context)	

    urls.py

    from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('volumeofrectangle/', views.rectvolume, name="volumeofrectangle"),
    path('', views.rectvolume, name="volumeofrectangleroot"),
]
~~~

## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-10-05 142908.png>)


## HOMEPAGE:
![alt text](<Screenshot 2025-10-05 142937.png>)


## RESULT:
The program for performing server side processing is completed successfully.
