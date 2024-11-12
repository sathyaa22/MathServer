# Ex.05 Design a Website for Server Side Processing
## Date:

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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

### html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1 align="center">Calculating Power of a Lamp</h1>
    <form action="{% url 'Result' %}" method="post">
        {% csrf_token %}
       
        <label for="">Intensity : </label>
        <input type="text" name="intensity-input">

        <br>

        <label for="">Resistance : </label>
        <input type="text" name="resistance-input">

        <br>

        <button type="submit">Calculate</button>

    </form>  
</body>
</html>
```
### views.py
```
from django.shortcuts import render
def home(request):
    return render(request,'index.html')
def Power(request):
    if request.method == 'POST':
        intensity_value = int(request.POST.get('intensity-input'))
        resistance_value = int(request.POST.get('resistance-input'))
        power = (intensity_value**2)*(resistance_value)
        return render(request,'Result.html',{'output':power})
```

### urls.py
```
from django.contrib import admin
from django.urls import path
from myapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('',views.home,name='home'),
    path('result',views.Power,name='Result')
]
```

## SERVER SIDE PROCESSING:

![image](https://github.com/user-attachments/assets/9158c1de-3034-49e9-b9a8-da938a8f040a)

## HOMEPAGE:

![image](https://github.com/user-attachments/assets/08f19612-6fb5-4286-a94a-43ac81bf3c2b)

![image](https://github.com/user-attachments/assets/61a22b0d-2f44-463b-9ef3-c49eca72d767)


## RESULT:
The program for performing server side processing is completed successfully.
