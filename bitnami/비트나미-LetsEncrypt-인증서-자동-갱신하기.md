# 비트나미 Let's Encrypt 인증서 자동 갱신하기

(이전글 [비트나미 워드프레스에 Let’s Encrypt 인증서 설치하기](./비트나미-워드프레스에-Letsencrypt-인증서-설치하기.md)에서 이어지는 내용임)

Let's Encrypt 인증서는 유효 기간이 90일까지로, 해당 인증서를 지속적으로 이용하기 위해서는 그전에 인증서를 갱신해야 한다. 매번 수동으로 인증하는 것으로 번거롭기 때문에, 이 글에서는 crontab을 사용하여 비트나미 워드프레스에서 Let's Encrypt 인증서를 자동 갱신하는 방법에 대해 알아보겠다. 

## Let's Encrypt 인증서 갱신하기

Lego 클라이언트를 사용하여 Let's Encrypt 인증서를 갱신하는 방법은 다음과 같다. 

```bash
sudo /opt/bitnami/ctlscript.sh stop
sudo lego --email="EMAIL-ADDRESS" --domains="DOMAIN" --path="/etc/lego" renew
sudo /opt/bitnami/ctlscript.sh start
```


