# 파이썬 Flask 시작하기 (Hello, World!)

Flask은 파이썬 기반의 웹 프레임워크이다. 이 글에서는 Flask를 시작하는 방법에 대해 알아보겠다. 

## Flask 설치하기

pip를 사용해서 Flask를 설치한다.

```bash
pip install Flask
```

## hello.py 만들기

hello.py 파일을 만들고 다음과 같이 작성한다.

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello, World!'
```

## Hello, World! 

터미널에서 다음과 같이 `hello.py`를 실행한다.

```
FLASK_APP=hello.py flask run
```

이제 `http://127.0.0.1:5000/`에 접속하면 `Hello, World!`라는 글씨를 볼 수 있다.

```
 * Serving Flask app "hello.py"
 * Environment: production
   WARNING: Do not use the development server in a production environment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```