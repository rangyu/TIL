# SemanticUI 파일 업로드 버튼 만들기

**예제 코드**
: https://codepen.io/rangyu/pen/rbMRKw

## HTML

```html
<div class="wrap">
  <section>
    <p>Type 1</p>
    <input type="file" (change)="fileEvent($event)" class="fileupload" id="fileUploadButton1" />
    <label for="fileUploadButton1" class="ui button">Upload</label>
  </section>
  
  <section>
    <p>Type 2</p>
   	<div class="ui action input">
      <input type="text" readonly />
      <input type="file" (change)="fileEvent($event)" class="fileupload" id="fileUploadButton2" />
      <label for="fileUploadButton2" class="ui button">Upload</label>
    </div>
  </section>
</div>
```

## CSS

```css
.wrap {
  margin: 2rem;
}
section {
  margin-bottom: 3rem;
}
.fileupload {
	width: 0;
	height: 0;
	opacity: 0;
	overflow: hidden;
	position: absolute;
	z-index: -1;
}
```

## JavaScript

```javascript
$('input:file.fileupload').on('change', function(e) {
 var name = e.target.files[0].name;          $(e.target).siblings('input:text').val(name);
});
```
