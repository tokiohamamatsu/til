# chart.jsで値を表示するプラグイン

```js
var bardataLabelPlugin = {
    afterDatasetsDraw: function(chart) {
        var ctx = chart.ctx;
        chart.data.datasets.forEach(function(dataset, data) {
            var meta = chart.getDatasetMeta(data);
            if (!meta.hidden) {
                meta.data.forEach(function(element, value) {                                                       
                    var dataString = dataset.data[value].toString();     
                    ctx.fillStyle = "black";       
                    var fontSize = 14;             
                    var fontStyle = "normal";      
                    var fontFamily = "serif";      
                    ctx.font = Chart.helpers.fontString(fontSize, fontStyle, fontFamily);                                                     
                    ctx.textAlign = 'center'; 
                    ctx.textBaseline = 'middle';                                                        
                    var padding = 10;                  
                    var position = element.tooltipPosition();
                    ctx.fillText(dataString, position.x, position.y - (fontSize / 2));
                });
            }
        });
    }
}
```

上記をChart.jsのpluginsに設定する

```js
                var bar = document.getElementById("barChart");
                var BarChart = new Chart(bar,  {
                    type: 'bar',
                    data: {
                    },
                    options: {
                    },
                    plugins:[bardataLabelPlugin]
                });
```

### 参考
[Chart\.jsでの数値表示プラグイン＜Chart\.js＜Javascript＜木暮仁](http://www.kogures.com/hitoshi/javascript/chartjs/datalabel.html)