<!DOCTYPE html>
<html>
<head>
	 <meta charset="utf-8">
    <title>全国主要城市空气质量</title>
    <!-- 引入echarts.js -->
    <script src="https://cdn.bootcss.com/echarts/3.8.5/echarts.min.js"></script>
    <script src="china.js"></script>

    <script src="http://cdn.static.runoob.com/libs/jquery/1.10.2/jquery.min.js"></script>
</head>
<body>
	  <div id="sexAndAge" style='height:652px; padding:16px 0px;'></div>

    <div id="map" style='height:652px; padding:16px 0px; '></div>
<script type="text/javascript">
var uploadedDataURL = "/FinalData.json";

$.getJSON(uploadedDataURL, function (data) {
    myChart.setOption(option = {
        title: {
            text: 'Beijing AQI'
        },
        tooltip: {
            trigger: 'axis'
        },
        xAxis: {
            data: data.map(function (item) {
                return item[1];
            })
        },
        yAxis: {
            splitLine: {
                show: false
            }
        },
        toolbox: {
            left: 'center',
            feature: {
                dataZoom: {
                    yAxisIndex: 'none'
                },
                restore: {},
                saveAsImage: {}
            }
        },
        dataZoom: [{
            startValue: '2014-06-01'
        }, {
            type: 'inside'
        }],
        visualMap: {
            top: 10,
            right: 10,
            pieces: [{
                gt: 0,
                lte: 50,
                color: '#096'
            }, {
                gt: 50,
                lte: 100,
                color: '#ffde33'
            }, {
                gt: 100,
                lte: 150,
                color: '#ff9933'
            }, {
                gt: 150,
                lte: 200,
                color: '#cc0033'
            }, {
                gt: 200,
                lte: 300,
                color: '#660099'
            }, {
                gt: 300,
                color: '#7e0023'
            }],
            outOfRange: {
                color: '#999'
            }
        },
        series: {
            name: 'Beijing AQI',
            type: 'line',
            data: data.map(function (item) {
                return item[3];
            }),
            markLine: {
                silent: true,
                data: [{
                    yAxis: 50
                }, {
                    yAxis: 100
                }, {
                    yAxis: 150
                }, {
                    yAxis: 200
                }, {
                    yAxis: 300
                }]
            }
        }
    });
});


</body>
</html>
