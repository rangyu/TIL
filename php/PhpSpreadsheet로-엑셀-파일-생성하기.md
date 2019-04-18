# PhpSpreadsheet로 엑셀 파일 생성하기


## 설치하기

composer로 PhpSpreadsheet 설치하기

```
composer require phpoffice/phpspreadsheet
```

---

## 엑셀 파일 생성하기

```php
<?php

  require_once '../vendor/autoload.php';

  $datas = array(
    array('name' => '아이언맨', 'phone' => '010-1234-5678', 'gender' => '남자'),
    array('name' => '캡틴마블', 'phone' => '010-3344-5566', 'gender' => '여자')
  );
  
  $cells = array(
      'A' => array(15, 'name', '이름'),
      'B' => array(20, 'phone',  '연락처'),
      'C' => array(20, 'gender', '성별')
  );

  use PhpOffice\PhpSpreadsheet\Spreadsheet;
  use PhpOffice\PhpSpreadsheet\Writer\Xlsx;

  $spreadsheet = new Spreadsheet();
  $sheet = $spreadsheet->getActiveSheet();

  foreach ($cells as $key => $val) {
      $cellName = $key.'1';
      $sheet->getColumnDimension($key)->setWidth($val[0]);
      $sheet->getRowDimension('1')->setRowHeight(25);
      $sheet->setCellValue($cellName, $val[2]);
      $sheet->getStyle($cellName)->getFont()->setBold(true);
      $sheet->getStyle($cellName)->getAlignment()->setHorizontal(\PhpOffice\PhpSpreadsheet\Style\Alignment::HORIZONTAL_CENTER);
      $sheet->getStyle($cellName)->getAlignment()->setVertical(\PhpOffice\PhpSpreadsheet\Style\Alignment::VERTICAL_CENTER);
  }

  for ($i = 2; $row = array_shift($datas); $i++) {
      foreach ($cells as $key => $val) {
          $sheet->setCellValue($key.$i, $row[$val[1]]);
      }
  }

  $filename = 'excel';
  header('Content-Type: application/vnd.openxmlformats-officedocument.spreadsheetml.sheet');
  header('Content-Disposition: attachment; filename="'.$filename.'.xlsx"');
  $writer = new Xlsx($spreadsheet);
  $writer->save('php://output');

?>
```