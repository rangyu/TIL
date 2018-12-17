# 파이썬 JSON 예쁘게 출력하기 (pprint)

print로 JSON 타입을 출력하면 한줄로 나와서 보기가 불편하다. 이럴 때 pprint를 사용하면 알아서 Depth가 적용되어서 출력되기 때문에 훨씬 보기가 편하다. 

다음과 같이 사용하면 된다.

```python
import pprint

pprint.pprint(data)
```