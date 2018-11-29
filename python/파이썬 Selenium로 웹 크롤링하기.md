# 파이썬 Selenium으로 웹 크롤링하기

## 웹 크롤링하려는 페이지
인스타그램 태그 개수를 가져오고자 한다.

## 왜 Selenium을 사용했는가?
인스타그램의 경우 먼저 로딩 이미지가 있는 페이지가 뜬 후 내용이 뜬다. request를 사용하면 로딩 페이지가 읽히기 때문에 Selenium를 사용해서 크롬창을 띄운 뒤 내용이 나온 페이지를 크롤링한다. 

## 설치하기

### Selenium
```
pip install selenium
```

### BeautifulSoup
```
pip install beautifulsoup4
```

## 완성된 코드

```Python
# -*- coding: utf-8 -*- 

# parser.py
from bs4 import BeautifulSoup
import selenium.webdriver as webdriver

# 인스타그램 페이지
url = 'https://www.instagram.com/explore/tags/%EC%B1%84%EC%86%8C%EC%8A%B5%EA%B4%80%EC%B1%8C%EB%A6%B0%EC%A7%80/'

# 크롬창을 띄우지 않는 옵션을 넣는다
options = webdriver.ChromeOptions()
options.add_argument('headless')
options.add_argument('disable-gpu')
driver = webdriver.Chrome('/Applications/chromedriver', chrome_options=options)

# url에 접근한다
driver.get(url)

# 크롤링한 웹페이지를 파싱한다.
soup = BeautifulSoup(driver.page_source, "html.parser")
tag = soup.find("span",{"class": "g47SY "})
count = tag.text
print(count)
```
