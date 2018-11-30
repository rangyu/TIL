# Highchart로 그라데이션 막대 그래프 만들기 

Hightchart 그라이데이션 막대그래프 예제. 베이스컬러 기준으로 칼럼의 색상이 점점 더 밝은 색으로 바꾼다.

[데모 보러가기](./Highchart로-그라데이션-막대-그래프-만들기/demo.html)

```javascript
 Highcharts.getOptions().plotOptions.column.colors = (function() {
        var colors = [],
            base = Highcharts.getOptions().colors[0],
            i;

        for (i = 0; i < sampleValues.length ; i += 1) {
            colors.push(Highcharts.Color(base).brighten((i - 2) / (sampleValues.length * 4)).get());
        }
        return colors;
    }());
```



## 완성된 코드

```javascript
var sampleValues = [49, 27, 10, 95, 154, 73, 292, 129, 148, 93, 102, 180, 103, 65, 78, 134, 27];

    Highcharts.getOptions().plotOptions.column.colors = (function() {
        var colors = [],
            base = Highcharts.getOptions().colors[0],
            i;

        for (i = 0; i < sampleValues.length ; i += 1) {
            colors.push(Highcharts.Color(base).brighten((i - 2) / (sampleValues.length * 4)).get());
        }
        return colors;
    }());

    Highcharts.chart( 'chart', {
        chart: {
            type: 'column'
        },
        title: {
            text: ''
        },
        subtitle: {
            text: ''
        },
        xAxis: {
            categories: [
                '1',
                '2',
                '3',
                '4',
                '5',
                '6',
                '7',
                '8',
                '9',
                '10'
            ],
            crosshair: true
        },
        yAxis: {
            min: 0,
            title: {
                text: ''
            }
        },
        legend: {
            enabled: false
        },
        exporting: {
            enabled: false
        },
        credits: {
            enabled: false
        },
        tooltip: {
            headerFormat: '<span style="font-size:10px">{point.key}</span><table>',
            pointFormat: '<tr><td style="color:{series.color};padding:0">{series.name}: </td>' +
                '<td style="padding:0"><b>{point.y:.1f}</b></td></tr>',
            footerFormat: '</table>',
            shared: true,
            useHTML: true
        },
        plotOptions: {
            column: {
                colorByPoint: true,
                pointPadding: 0,
                borderWidth: 0,
                groupPadding: 0,
            },
        },
        series: [{
            name: 'Value',
            data: sampleValues
        }]
    });
```