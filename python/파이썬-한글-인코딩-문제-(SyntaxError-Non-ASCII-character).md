# 파이썬 한글 인코딩 문제 (SyntaxError: Non-ASCII character)

```
SyntaxError: Non-ASCII character 
```

파이썬 2.7에서 기본 인코딩이 ASCII이기 때문 한글 인식이 안된다. 만약 소스 코드에 한글이 있으면 위와 같은 신택스 에러가 나온다. 

이를 해결하기 위해서 최상단에 다음과 같은 주석을 추가한다.

```
# -*- coding: utf-8 -*- 
```

(아니면 그냥 파이썬 3을 쓰자...)