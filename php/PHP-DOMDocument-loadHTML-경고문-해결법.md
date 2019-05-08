# PHP-DOMDocument-loadHTML-경고문-해결법

## 문제 

php에서 올바르지 않은 HTML 문서를 로딩할 때 다음과 같은 경고문이 뜨는 경우가 있다.

```
Warning: DOMDocument::loadHTML(): Unexpected end tag
```

## 해결법

해당 경고를 무시하려면 `loadHTML()` 함수가 불려지기 전 다음과 같이 해당 경고를 무시하게끔 설정할 수 있다.

```
libxml_use_internal_errors(true);
```

* 공식 매뉴얼 : https://www.php.net/manual/en/function.libxml-use-internal-errors.php

* 해결법 출처 : https://codeday.me/ko/qa/20190325/149807.html 