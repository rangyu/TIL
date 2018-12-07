# 파이썬 BeautifulSoup으로 HTML 파싱하기

파이썬 BeautifulSoup 라이브러리를 활용하면 손쉽게 Html을 파싱할 수 있다.

## 설치하기

pip로 BeautifulSoup를 설치하자.

```bash
pip install beautifulsoup4
```

## BeautifulSoup 사용하기 

코드 상단에 다음과 같이 BeautifulSoup 라이브러리를 import를 해준다. 

```python
from bs4 import BeautifulSoup
```

```python;
soup = BeautifulSoup( html , 'html.parser')
```
