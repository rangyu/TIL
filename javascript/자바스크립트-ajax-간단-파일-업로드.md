# 자바스크립트 ajax 간단 파일 업로드

## 자바스크립트

```javascript
$('input:file').on('change', function(e) {
  var file = this.files[0];
  uploadFile(file);
});

function uploadFile(file){
  if(window.FormData === undefined){
      alert('현재 지원하지 않는 브라우저입니다. 최신 버전의 브라우저로 업데이트해주세요.');
      return;
  }
  var formData = new FormData();
  formData.append('formData', file);
  $.ajax({
      url: '../upload.php',
      type: 'POST',
      data: formData,
      processData: false,
      contentType: false,
      success: function(result){
        // ...
      }
  });
}
```

## PHP

```php
  echo $_FILES['formData']['name'];
  echo $_FILES['formData']['type'];
```