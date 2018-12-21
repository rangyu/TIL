# 우분투에서 .htaccess 적용 안될 때 해결책

`.htaccess` 파일을 만들었는데도 정상적으로 적용이 안될 때의 해결책을 알아보자. (Ubuntu 기준)

## rewrite 모듈 체크하기

먼저 아파치의 `rewrite` 모듈이 활성화 되어 있는지 확인해본다. 만약 php라면 다음과 같이 현재 활성화된 아파치 모듈 목록을 확인해볼 수 있다. 

```php 
<?php
    print_r(apache_get_modules());
?>
```

출력된 목록에 `mod_rewrite` 값이 있다면 활성화된 것이다. 

```
Array ( [0] => core [1] => mod_so [2] => mod_watchdog [3] => http_core [4] => mod_log_config [5] => mod_logio [6] => mod_version [7] => mod_unixd [8] => mod_access_compat [9] => mod_alias [10] => mod_auth_basic [11] => mod_authn_core [12] => mod_authn_file [13] => mod_authz_core [14] => mod_authz_host [15] => mod_authz_user [16] => mod_autoindex [17] => mod_deflate [18] => mod_dir [19] => mod_env [20] => mod_filter [21] => mod_mime [22] => prefork [23] => mod_negotiation [24] => mod_php5 [25] => mod_reqtimeout [26] => mod_rewrite [27] => mod_setenvif [28] => mod_socache_shmcb [29] => mod_ssl [30] => mod_status )
```

만약 mod_rewrite가 없다면 다음과 같이 활성화 하자.

## 아파치 설치 경로 찾기

다음과 같이 아파치 설치 경로 확인하자.

```bash
apache2 -V | egrep "(HTTPD\_ROOT|SERVER\_CONFIG\_FILE)"
```

예를 들어 다음과 같이 결과가 나왔다면, 아파치 설치 경로는 `/etc/apache2`, 환경설정 파일 `apache2.conf`이라는 뜻이다. 

```bash
 -D HTTPD_ROOT="/etc/apache2"
 -D SERVER_CONFIG_FILE="apache2.conf"
```


## rewrite 모듈 활성화하기 


아파치 디렉토리 안에는 `mods-available`, `mods-enabled`라는 디렉토리가 있다. `mods-available`는 설치된 모듈들, `mods-enabled`에는 현재 활성화된 모듈들의 링크가 들어있다. 

`rewrite` 모듈을 활성화하려면, `mods-available` 디렉토리 안의 `rewrite.load` 모듈의 링크를 `mods-enabled` 디렉토리 안에 넣어주면 된다. 

다음과 같이 심볼릭 링크를 생성한다.

```bash
sudo ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/rewrite.load
```

이후 아파치를 재시작하면 된다. 

```bash
sudo service apache2 restart
```


## 더 간단한 방법

위와 같이 직접 링크를 생성하지 않고도 더 간단한 방법도 있다. 

```bash
sudo a2enmod rewrite
```

위와 같은 명령어를 입력하면 된다. 그러면 자동으로 `rewrite` 모듈이 활성화된다. 


