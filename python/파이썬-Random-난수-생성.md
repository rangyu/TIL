# 파이썬 Random 난수 생성

파이썬 난수 생성 라이브러리에 대해 알아보자. 

## random

0부터 1사이의 임의의 float를 생성한다.

```
import random

f = random() # 0~1 사이의 임의의 실수
print(i) 
# 예시 출력 : 0.74036690927287964
```

## randint

```
from random import randint
 
i = randint(1, 99)  # 1부터 99 사이의 임의의 정수
print(i)
```

## uniform

```
from random import uniform
 
f = uniform(0.4, 8.4)  # 0.4~8.4 사이의 임의의 실수
print(f)
```

# randrange

```
from random import randrange

i = random.randrange(1,7) # 1~6 사이의 임의의 정수 (7은 포함하지 x)
print(i)
```