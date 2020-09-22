# helloApp Review

## 시작

1. App 생성

```shell
python manage.py startapp helloApp
```

터미널에 입력하면 디렉토리와 기본 파이썬 파일이 생긴다.



2. url 만들기

urls.py에서 path 생성

```python
from django.contrib import admin
from django.urls import path, include
from helloApp import views


urlpatterns = [
    path('index/', views.index),
]
```

`import`해야할 것 하고, 처음에는 `index/` url을 넣어준다.

`views.index`에서 `index`는 view에서 만들어줘야하는 함수.

이제 view로 이동



3. view

view에서 함수를 만들어

```python
from django.shortcuts import render, HttpResponse
from .models import *

# Create your views here.

def index(request):
    #return HttpResponse('<div align=center>섭이와 함께하는 Django WEB Framework</div>')
    return render(request, 'hello/index.html')

```

`HttpResponse` : print와 같은 거

`render` :  html 보여준다



4. templates

html이 있는 곳. 직접 디렉토리 만들어야 하고 스펠링, 대소문자 잘 지켜야 함

```html
<body>
    <center>Naver</center>

    <div align='right'>
        <form method="post" action="{% url 'login' %}">

            {% csrf_token %}

        <label>아이디</label> <input type='text' name="id"/>
        <label>패스워드</label> <input type='password' name="pwd"/>
        <input type="submit" value="LOGIN">
        </form>
    </div>
</body>
```

login 화면을 만들었다.

post 방식일 경우 url에 id, pwd가 노출되기 때문에 `{% csrf_token %}`을 써줘야 한다.

