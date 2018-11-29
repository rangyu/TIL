
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
