# Bash로 문자열 출력하기

`hello.sh` 파일 만들기

```bash
#!/usr/bin/env bash

echo "hello world"
printf "hello world"
printf "%s %s %d" hello world 1234
```

터미널에서 실행하기

```
bash hello.sh
```

---

### 출력 결과

```
hello world
hello worldhello world 1234
```

`echo`는 문자열 끝에서 줄바꿈이 추가되고, `printf`는 줄바꿈 없이 그대로 이어져서 출력된다.
