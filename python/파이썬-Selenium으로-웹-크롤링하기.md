# 파이썬 Selenium으로 웹 크롤링하기

파이썬 Selenium을 사용해서 인스타그램의 태그 개수를 가져오는 크롤러를 만들어보자. 

## 필요한 파일 설치하기

### 1. Selenium  설치하기

파이썬 request를 사용하면 인스타그램 태그 개수를 제대로 읽히지 않는다. 왜냐하면 페이지 내용이 뜨기 전에 인스타그램 로딩 페이지가 읽히기 때문. 따라서 Selenium를 사용해서 크롬창을 띄운 뒤 내용이 나온 페이지를 크롤링한다. 

pip를 이용해서 Selenium를 설치한다. (만약 파이썬 버전 2.7이라면 pip를 먼저 수동으로 설치해야 한다.)

```
pip install selenium
```

### 2. BeautifulSoup 설치하기

인스타그램 태그 개수 값은 ``<span class="g47SY"></span>`` 안에 표시된다. BeautifulSoup는 사용하면 웹페이지를 쉽게 파싱하고 원하는 값을 가져올 수 있다.

```
pip install beautifulsoup4
```

## 크롬창을 띄우지 않는 옵션 넣기
Selenium의 웹 드라이버를 사용하면 크롬창이 새로 뜬 다음 해당 페이지를 크롤링한다. 이때 크롬창을 띄우지 않고 크롤링하길 원한다면 다음과 같은 옵션을 추가하면 된다.

```Python
# 크롬창을 띄우지 않는 옵션을 넣는다
options = webdriver.ChromeOptions()
options.add_argument('headless')
options.add_argument('disable-gpu')
driver = webdriver.Chrome('/Applications/chromedriver', chrome_options=options)
```

## 완성된 코드

```Python
# -*- coding: utf-8 -*- 

from bs4 import BeautifulSoup
import selenium.webdriver as webdriver

# 인스타그램 태그 페이지
url = 'https://www.instagram.com/explore/tags/mytag/'

# 크롬창을 띄우지 않는 옵션을 넣는다
options = webdriver.ChromeOptions()
options.add_argument('headless')
options.add_argument('disable-gpu')
driver = webdriver.Chrome('/Applications/chromedriver', chrome_options=options)

# url에 접근한다
driver.get(url)

# 크롤링한 웹페이지를 파싱한다.
soup = BeautifulSoup(driver.page_source, "html.parser")
tag = soup.find("span",{"class": "g47SY"})
count = tag.text
print(count)
```
