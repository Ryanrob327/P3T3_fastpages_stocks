---
toc: true
layout: post
description: A minimal example of using markdown with fastpages.
categories: [test]
title: Graph Test
---
<html>
<head>
  <script type="text/javascript">
  window.onload = function () {
    var chart = new CanvasJS.Chart("chartContainer",
    {

      title:{text: "Amount of sh Ryan gives"},
       data: [
      {
        type: "line",

        dataPoints: [
        { x: new Date(2022, 00, 1), y: 600 },
        { x: new Date(2022, 01, 1), y: 550 },
        { x: new Date(2022, 02, 1), y: 500 },
        { x: new Date(2022, 03, 1), y: 450 },
        { x: new Date(2022, 04, 1), y: 400 },
        { x: new Date(2022, 05, 1), y: 350 },
        { x: new Date(2022, 06, 1), y: 300 },
        { x: new Date(2022, 07, 1), y: 250 },
        { x: new Date(2022, 08, 1), y: 200 },
        { x: new Date(2022, 09, 1), y: 150 },
        { x: new Date(2022, 10, 1), y: 100 },
        { x: new Date(2022, 11, 1), y: 50 }
        ]
      }
      ]
    });

    chart.render();
  }
  </script>
 <script type="text/javascript" src="https://canvasjs.com/assets/script/canvasjs.min.js"></script></head>
<body>
  <div id="chartContainer" style="height: 500px; width: 100%;">
  </div>
</body>
</html>
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
  $.getJSON("https://canvasjs.com/data/docs/btcusd2018.json", function(data) { //https://canvasjs.com/data docs/btcusd2018.json
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