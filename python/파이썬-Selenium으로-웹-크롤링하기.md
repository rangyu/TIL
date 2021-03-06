# 파이썬 Selenium으로 웹 크롤링하기

파이썬 Selenium을 사용해서 인스타그램의 태그 개수를 가져오는 크롤러를 만들어보자. 

## Selenium 설치하기

파이썬 request를 사용하면 인스타그램 태그 개수를 제대로 읽히지 않는다. 왜냐하면 페이지 내용이 뜨기 전에 인스타그램 로딩 페이지가 읽히기 때문. 따라서 Selenium를 사용해서 크롬창을 띄운 뒤 내용이 나온 페이지를 크롤링한다.

아래와 같이 pip를 사용해서 Selenium를 설치한다. (만약 파이썬 버전 2.7이라면 pip를 먼저 수동으로 설치해야 한다.) 

```
pip install selenium
```

## 크롬드라이버 설치하기

Selenium은 기본적으로 파이어폭스 드라이버가 설치되어 있다. 만약 크롬 브라우저를 사용하고 싶다면 먼저 크롬 드라이버를 설치해야 한다. 
- 크롬 드라이버 다운로드 받기 : https://sites.google.com/a/chromium.org/chromedriver/downloads	

다음과 같이 크롬 드라이버를 사용한다.
 ```Python	
# 크롬 드라이버를 사용한다	
driver = webdriver.Chrome('/Applications/chromedriver')	
```
``/Applications/chromedriver`` 부분에는 크롬 드라이버를 설치한 경로를 입력한다.

 

## 크롬창을 띄우지 않는 옵션 넣기 (headless)	

Selenium의 웹 드라이버를 사용하면 크롬창이 새로 뜬 다음 해당 페이지를 크롤링한다. 만약 크롬 창을 띄우지 않길 원한다면 ``headless`` 옵션을 추가하면 된다.

 ```Python	
# 크롬창을 띄우지 않는 옵션을 넣는다	
options = webdriver.ChromeOptions()	
options.add_argument('headless')	
options.add_argument('disable-gpu')	
driver = webdriver.Chrome('/Applications/chromedriver', options=options)
```
## 내용이 뜰 때까지 기다리기
인스타그램은 먼저 로고 이미지가 뜬 다음 내용 페이지로 바뀐다. 제대로 내용을 크롤링하려면 로딩이 완료될 때까지 기다려야 한다.

``implicitly_wait(sec)``를 사용하면 내용이 충분히 뜰 때까지 혹은 최대 지정한 시간(초)까지 기다린다. 

```Python	
# 암시적으로 최대 5초간 기다린다
driver.implicitly_wait(5)
```

(참고) 이때, ``implicitly_wait()`` 함수는 오직 세션 당 1회만 실행된다.  만약 반복해서 시간 지연을 하고 싶다면 ``implicitly_wait()``말고 ``time.sleep()`` 함수를 사용하자.

```Python
import time

# 5초간 대기한다
time.sleep(5)
```

## URL 페이지 정보를 가져온다

아래와 같이 해당 URL의 페이지에 접속할 수 있다.

```Python
# url에 접속한다
driver.get(url)
```

인스타그램의 태그 게시물 개수는 ``<span ="g47SY">``안에 표시된다. ``find_element_by_class_name()`` 함수를 사용하면 클래스 ``name``으로 값을 가져올 수 있다.  

```Python
# 게시물 개수를 가져온다
totalCount = driver.find_element_by_class_name('g47SY').text 
print("총 게시물 수:", totalCount)
```

## 완성된 코드	

완성된 코드는 다음과 같다.

 ```Python
import selenium.webdriver as webdriver	

# 검색할 태그명
tag = 'your-tag-name'

# 인스타그램 태그 페이지 URL	
url = 'https://www.instagram.com/explore/tags/' + tag 

# 크롬창을 띄우지 않는 옵션을 넣는다	
options = webdriver.ChromeOptions()	
options.add_argument('headless')	
options.add_argument('disable-gpu')	
driver = webdriver.Chrome('/Applications/chromedriver', options=options)	

# 암시적으로 최대 5초간 기다린다
driver.implicitly_wait(5)

# url에 접근한다
driver.get(url)

# 게시물 개수 정보를 가져온다
totalCount = driver.find_element_by_class_name('g47SY').text 

# 게시물 개수를 출력한다
print("totalCount :", totalCount)	

# 열어둔 webdriver를 종료한다 
# (종료하지 않고 반복 실행하면 메모리 누수의 원인이 된다)
driver.quit()
 ```