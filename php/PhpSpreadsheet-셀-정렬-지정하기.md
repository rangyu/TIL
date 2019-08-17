# PhpSpreadsheet 셀 정렬 지정하기

```php
require_once '../vendor/autoload.php';
use PhpOffice\PhpSpreadsheet\Spreadsheet;

// 스프레드시트 생성
$spreadsheet = new Spreadsheet();
$sheet = $spreadsheet->getActiveSheet();

//(중략)

// 가로 정렬 => 가운데(HORIZONTAL_CENTER)
$sheet->getStyle($cellName)->getAlignment()->setHorizontal(\PhpOffice\PhpSpreadsheet\Style\Alignment::HORIZONTAL_CENTER);

// 세로 정렬 => 가운데(VERTICAL_CENTER)
$sheet->getStyle($cellName)->getAlignment()->setVertical(\PhpOffice\PhpSpreadsheet\Style\Alignment::VERTICAL_CENTER);
```