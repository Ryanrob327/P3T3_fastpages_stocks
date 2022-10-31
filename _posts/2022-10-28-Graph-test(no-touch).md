---
toc: true
layout: default
description: A minimal example of using markdown with fastpages.
categories: [test]
title: Graph Test
---
<html>
<head>
<script type="text/javascript" src="https://canvasjs.com/assets/script/jquery-1.11.1.min.js"></script>
<script type="text/javascript" src="https://canvasjs.com/assets/script/canvasjs.stock.min.js"></script>
<script type="text/javascript">
window.onload = function () {
  var dps1 = [], dps2= [];
  var stockChart = new CanvasJS.StockChart("chartContainer",{
    theme: "light2",
    exportEnabled: true,
    title:{
      text:"StockChart with Date-Time Axis"
    },
    subtitles: [{
      text: "GME Price (in USD)"
    }],
    charts: [{
      axisX: {
        crosshair: {
          enabled: true,
          snapToDataPoint: true
        }
      },
      axisY: {
        prefix: "$"
      },
      data: [{
        type: "candlestick",
        yValueFormatString: "$#,###.##",
        dataPoints : dps1
      }]
    }],
    navigator: {
      data: [{
        dataPoints: dps2
      }],
      slider: {
        minimum: new Date(2021, 01, 01),
        maximum: new Date(2021, 12, 01)
      }
    }
  });
  $.getJSON("http://127.0.0.1:5000/api/GME/", function(data) { //https://canvasjs.com/data docs/btcusd2018.json
    for(var i = 0; i < data.length; i++){
      dps1.push({x: new Date(data[i].date), y: [Number(data[i].open), Number(data[i].high), Number(data[i].low), Number(data[i].close)]});
      dps2.push({x: new Date(data[i].date), y: Number(data[i].close)});
    }
    stockChart.render();
  });
}
</script>
</head>
<body>
<div id="chartContainer" style="height: 450px; width: 100%;"></div>
</body>
</html>