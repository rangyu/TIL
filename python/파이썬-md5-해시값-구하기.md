# 파이썬 md5 해시값 구하기 

다음은 파이썬에서 md5 해시값을 구하는 코드이다.

## md5 해시값 구하기 

```python
import hashlib

string = "md5로 변환할 문자열"
md5hash = hashlib.md5(string.encode('utf-8')).hexdigest()
print(md5hash)
```

출력하면 다음과 같이 md5 해시값으로 변환된 것을 볼 수 있다.

```
fbf2760cb0f1e945db5855baeaed33d6
```