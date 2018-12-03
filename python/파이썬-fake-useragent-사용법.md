# 파이썬 fake-useragent 사용법

UserAgent 값을 랜덤으로 생성하는 법을 알아보자.

## 설치하기

먼저 pip를 사용해서 fake-useragent 패키지를 설치한다.

```
pip install fake-useragent
```

## 완성된 코드

```python
import selenium.webdriver as webdriver	
from selenium.webdriver.chrome.options import Options
from fake_useragent import UserAgent

# 랜덤으로 생성한 UserAgent 값을 출력한다
ua = UserAgent(verify_ssl=False)
userAgent = ua.random
print(userAgent)

# 생성한 UserAgent 값을 옵션에 추가한다 
options = Options()	
options.add_argument(f'user-agent={userAgent}')
```