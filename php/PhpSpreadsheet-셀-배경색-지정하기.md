# PhpSpreadsheet 셀 배경색 지정하기

```php
require_once '../vendor/autoload.php';
use PhpOffice\PhpSpreadsheet\Spreadsheet;

// 스프레드시트 생성
$spreadsheet = new Spreadsheet();
$sheet = $spreadsheet->getActiveSheet();

//(중략)

// 특정 셀의 스타일 지정 (셀 A1:A10의 배경색을 #FFDA44로 바꾼다)
$sheet->getStyle('A1:A10')->getFill()->setFillType(\PhpOffice\PhpSpreadsheet\Style\Fill::FILL_SOLID)->getStartColor()->setARGB('FFFFDA44');
```

자세한 것은 공식문서를 참고할 것.
https://phpspreadsheet.readthedocs.io/en/latest/topics/accessing-cells/
