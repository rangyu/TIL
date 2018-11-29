# 파이썬 한글 인코딩 문제 (SyntaxError: Non-ASCII character)

파이썬 2.7에서 기본 인코딩이 ASCII이기 때문 한글 인식이 안된다. 

## 에러 메시지

만약 소스 코드에 한글이 있으면 이를 인식하지 못하고 다음과 같은 Syntax 에러가 뜬다.

```
SyntaxError: Non-ASCII character 
```

## 해결법

최상단에 다음과 같은 주석을 추가하면 인코딩을 UTF-8로 변경할 수 있다.
(참고 : http://python.org/dev/peps/pep-0263/)

```
# -*- coding: utf-8 -*- 
```

(아니면 그냥 파이썬 3을 쓰자.)