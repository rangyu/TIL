# 이미 Git 원격 저장소에 올라간 파일을 gitignore 적용하기

한번 Git 원격 저장소에 올라간 파일은 뒤늦게 gitignore 설정해도 제대로 적용되지 않는다. 이미 올라간 파일(예를 들면 .DS_Store 파일 등)을 gitignore에 다시 반영하려면 gitignore 파일을 수정한 뒤 캐싱된 파일을 삭제하면 된다. 

```
git rm --cached .DS_Store
git commit -m 'untrack .DS_Store'
```

``--cached`` 옵션을 사용하면 로컬 저장소 내 파일은 남아 있고 원격 저장소의 파일만 삭제된다. (만약 로컬과 원격 저장소 모두 해당파일을 삭제하려면 ``--cached`` 옵션을 생략하면 된다.) 

