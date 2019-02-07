# 파이썬 html 들여쓰기 자동으로 넣기

html4print를 사용하면 손쉽게 html 소스코드를 자동 들여쓰기 할 수 있다. 

- 출처 : https://pypi.org/project/html5print/

---

pip를 사용해서 설치한다.

```python
pip install html5print
```

다음과 같이 사용하면 된다. (숫자 4는 들여쓰기할 때 스페이스 간격을 뜻한다.)

```python

from html5print import HTMLBeautifier

html = HTMLBeautifier.beautify(str, 4)
print(html)

```

