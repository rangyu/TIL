#  Mailchimp 파이썬 API 사용하기

파이썬 기반의 Mailchimp API를 사용하는 법에 대해 알아보자. 

## 설치하기

이 글에서는 `charlesthk/python-mailchimp` 라이브러리를 사용하였다. (MailChimp API v3 기반)

pip를 이용해서 설치한다. 

```
pip install mailchimp3
```


## 초기화하기

- YOUR_API_KEY : 메일침프 API 키
- YOUR_USERNAME : 메일침프 계정 아이디 

```python
from mailchimp3 import MailChimp

client = MailChimp(mc_api='YOUR_API_KEY', mc_user='YOUR_USERNAME')
```

## 회원 목록 가져오기

```python
list_id = 'YOUR_LIST_ID'
members = client.lists.members.all(list_id, get_all=True, fields="members.email_address,members.id")
```

## 회원 추가하기 or 갱신하기

메일침프에서는 멤버의 키 값으로 email을 사용한다. `client.lists.members.create_or_update()`함수 를 사용하면 해당 이메일 주소가 리스트에 없다면 create하고 중복된다면 최신 값으로 update할 수 있다. 

다음과 같이 사용할 수 있다. 이 함수를 사용하려면 data 속성에 `status_if_new`값이 포함되어야 한다. 

```python
import hashlib

member_email = 'tester@email.com'
subscriber_hash = hashlib.md5(member_email.encode('utf-8')).hexdigest()

client.lists.members.create_or_update(list_id=list_id, subscriber_hash=subscriber_hash, data={
    'email_address': member_email,
    'status_if_new': 'subscribed',
    'merge_fields': {
        'NAME': '홍길동',
        'BIRTHDAY': '05/21',
    }
})
```
`subscriber_hash`에는 멤버 이메일 주소의 md5 해시값을 넣는다. 

## API 구조
```
MailChimp
+- Root
+- Authorized Apps
+- Automations
|  +- Actions
|  +- Emails
|  |  +- Actions
|  |  +- Queues
|  +- Removed Subscribers
+- Batch Operations
+- Batch Webhooks
+- Campaign Folders
+- Campaigns
|  +- Actions
|  +- Content
|  +- Feedback
|  +- Send Checklist
+- Conversations
|  +- Messages
+- Stores
|  +- Carts
|  |  +- Lines
|  +- Customers
|  +- Orders
|  |  +- Lines
|  +- Products
|     +- Images
|     +- Variants
|  +- Promo Rules
|     +- Promo Codes
+- File Manager Files
+- File Manager Folders
+- Lists
|  +- Abuse Reports
|  +- Activity
|  +- Clients
|  +- Growth History
|  +- Interest Categories
|  |  +- Interests
|  +- Members
|  |  +- Activity
|  |  +- Goals
|  |  +- Notes
|  +- Merge Fields
|  +- Segments
|  |  +- Segment Members
|  +- Signup Forms
|  +- Twitter Lead Generation Carts
|  +- Webhooks
+- Ping
+- Reports
|  +- Campaign Abuse
|  +- Campaign Advice
|  +- Campaign Open reports
|  +- Click Reports
|  |  +- Members
|  +- Domain Performance
|  +- EepURL Reports
|  +- Email Activity
|  +- Google Analytics
|  +- Location
|  +- Sent To
|  +- Sub-Reports
|  +- Unsubscribes
+- Seach Campaigns
+- Search Members
+- Template Folders
+- Templates
   +- Default Content
```

자세한 가이드는 아래 깃허브 공식문서를 참고하자.

- 깃허브 문서 : https://github.com/charlesthk/python-mailchimp
