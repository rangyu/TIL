# PhpSpreadsheet을 이용한 엑셀 파일 읽기

(예전 PHPExcel는 현재 더이상 개발되지 않음. 대신 PhpSpreadsheet를 사용할 것. / PHP 버전 5.6 이상만 가능.)

- PhpSpreadsheet 깃허브 저장소 주소 : https://github.com/PHPOffice/PhpSpreadsheet
- PhpSpreadsheet 공식 문서 : https://phpspreadsheet.readthedocs.io/en/latest/


---

## PhpSpreadsheet 시작하기

composer를 사용해서 프로젝트 폴더 내 PhpSpreadsheet 라이브러리를 설치한다.

```
composer require phpoffice/phpspreadsheet
```

프로젝트 상단에 `vender/autoload.php` 파일을 불러온다.

```php
<?php
require 'vendor/autoload.php';
```

사용하고자 하는 PhpSpreadsheet 라이브러리를 선언한다. 

```php
use PhpOffice\PhpSpreadsheet\Spreadsheet;
use PhpOffice\PhpSpreadsheet\Writer\Xlsx;
```
---

## Hello World 만들기

```php
<?php
require 'vendor/autoload.php';

use PhpOffice\PhpSpreadsheet\Spreadsheet;
use PhpOffice\PhpSpreadsheet\Writer\Xlsx;

$spreadsheet = new Spreadsheet();
$sheet = $spreadsheet->getActiveSheet();
$sheet->setCellValue('A1', 'Hello World !');

$writer = new Xlsx($spreadsheet);
$writer->save('hello world.xlsx');
```
(출처 : https://phpspreadsheet.readthedocs.io/en/latest/)

---

## Form에서 POST로 넘긴 엑셀 파일 읽기

```php
<?php
require_once '../vendor/autoload.php';

use PhpOffice\PhpSpreadsheet\Spreadsheet;
use PhpOffice\PhpSpreadsheet\Reader\Csv;
use PhpOffice\PhpSpreadsheet\Reader\Xlsx;
use PhpOffice\PhpSpreadsheet\Reader\Xls;

$file_mimes = array('text/x-comma-separated-values', 'text/comma-separated-values', 'application/octet-stream', 'application/vnd.ms-excel', 'application/x-csv', 'text/x-csv', 'text/csv', 'application/csv', 'application/excel', 'application/vnd.msexcel', 'text/plain', 'application/vnd.openxmlformats-officedocument.spreadsheetml.sheet');

// 유효한 엑셀 파일인지 확인
if(isset($_FILES['formData']['name']) && in_array($_FILES['formData']['type'], $file_mimes)) {

    $arr_file = explode('.', $_FILES['formData']['name']);
    $extension = end($arr_file);

    // 확장자에 맞는 라이브러리로 파일 읽기
    if('csv' == $extension) {
      $reader = new \PhpOffice\PhpSpreadsheet\Reader\Csv();
    } else if('xlsx' == $extension) {
      $reader = new \PhpOffice\PhpSpreadsheet\Reader\Xlsx();
    } else if('xls' == $extension) {
      $reader = new \PhpOffice\PhpSpreadsheet\Reader\Xls();
    } else {
      echo 'error';
      return;
    }

    $spreadsheet = $reader->load($_FILES['formData']['tmp_name']);
    $sheetData = $spreadsheet->getActiveSheet()->toArray();

    // 엑셀 데이터 출력하기
    print_r($sheetData);
  
  }else {
    echo 'error';
  }

?>
```
