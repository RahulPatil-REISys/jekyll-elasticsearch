---
layout: post
title:  "Welcome to Jekyll!"
date:   2013-02-19 21:28:15 +0700
categories: [jekyll]
---
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js"></script>
<script src="https://code.highcharts.com/highcharts.js"></script>
<script src="https://code.highcharts.com/modules/variable-pie.js"></script>
<script src="https://code.highcharts.com/modules/exporting.js"></script>
<script src="https://code.highcharts.com/modules/export-data.js"></script>
<script src="https://code.highcharts.com/modules/accessibility.js"></script>


<div id="container" style="min-width: 310px; height: 400px; margin: 0 auto">
</div>

<figure class="highcharts-figure">
  <div id="container1"></div>
  <p class="highcharts-description">
    Variable radius pie charts can be used to visualize a
    second dimension in a pie chart. In this chart, the more
    densely populated countries are drawn further out, while the
    slice width is determined by the size of the country.
  </p>
</figure>

<script>

  $.ajax({url: "https://qa1.reisystems.in:9001/api/v1/blogs?blog=welcome1-to-jekyll", 
  success: function(result) {
    console.log(result.blogs[0]._source.xcategories)
    console.log(typeof result.blogs[0]._source.xcategories)
    console.log(JSON.parse(result.blogs[0]._source.xcategories))
    
    console.log(result.blogs[0]._source.yseries)

    $('#container').highcharts({
            title: {
                text: 'Monthly Average Temperature',
                x: -20 //center
            },
            xAxis: {
                categories: JSON.parse(result.blogs[0]._source.xcategories)
            },
            yAxis: {
                title: {
                    text: 'Temperature (°C)'
                },
                plotLines: [{
                    value: 0,
                    width: 1,
                    color: '#808080'
                }]
            },
            tooltip: {
                valueSuffix: '°C'
            },
            legend: {
                layout: 'vertical',
                align: 'right',
                verticalAlign: 'middle',
                borderWidth: 0
            },
            series: JSON.parse(result.blogs[0]._source.yseries)
        });

  },error:function(err){
      console.log(err);
  }});
        


        Highcharts.chart('container1', {
          chart: {
            type: 'variablepie'
          },
          title: {
            text: 'Countries compared by population density and total area.'
          },
          tooltip: {
            headerFormat: '',
            pointFormat: '<span style="color:{point.color}">\u25CF</span> <b> {point.name}</b><br/>' +
              'Area (square km): <b>{point.y}</b><br/>' +
              'Population density (people per square km): <b>{point.z}</b><br/>'
          },
          series: [{
            minPointSize: 10,
            innerSize: '20%',
            zMin: 0,
            name: 'countries',
            data: [{
              name: 'Spain',
              y: 505370,
              z: 92.9
            }, {
              name: 'France',
              y: 551500,
              z: 118.7
            }, {
              name: 'Poland',
              y: 312685,
              z: 124.6
            }, {
              name: 'Czech Republic',
              y: 78867,
              z: 137.5
            }, {
              name: 'Italy',
              y: 301340,
              z: 201.8
            }, {
              name: 'Switzerland',
              y: 41277,
              z: 214.5
            }, {
              name: 'Germany',
              y: 357022,
              z: 235.6
            }]
          }]
        });

</script>