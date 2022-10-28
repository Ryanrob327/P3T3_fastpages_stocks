---
toc: true
layout: post
description: A minimal example of using markdown with fastpages.
categories: [markdown]
title: Graph Test
---
<!DOCTYPE HTML>
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