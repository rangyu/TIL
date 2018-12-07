# 파이썬 Random 난수 생성

파이썬의 난수 생성을 위한 Random 라이브러리에 대해 알아보자. 

## random

0과 1 사이의 임의의 float 값을 생성한다.

```python
import random

f = random() # 0~1 사이의 실수
print(f) 
# 예시 출력 : 0.74036690927287964
```

## randint

arg1과 arg2 사이의 임의의 int 값을 생성한다.

```python
from random import randint
 
i = randint(1, 99)  # 1~99 사이의 정수
print(i)
```

## uniform

arg1과 arg2 사이의 임의의 float 값을 생성한다.

```python
from random import uniform
 
f = uniform(0.4, 8.4)  # 0.4~8.4 사이의 실수
print(f)
```

## randrange

arg1과 (arg2 - 1) 사이의 임의의 int 값을 생성한다.

```python
from random import randrange

i = random.randrange(1,7) # 1~6 사이의 정수 (7은 포함하지 x)
print(i)
```

arg1과 (arg2 - 1) 사이의 임의의 int 값을 생성하되, arg1부터 arg3만큼씩 증가하는 숫자만 포함한다.

```python
from random import randrange

i1 = random.randrange(2, 20, 2) # 2~20 사이의 정수 (2부터 2씩 증가하는 숫자만 포함한다)
i2 = random.randrange(3, 30, 3) # 3~30 사이의 정수 (3부터 3씩 증가하는 숫자만 포함한다)
print(i1)
print(i2)
```