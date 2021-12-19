---
layout: post
title:  "Welcome to Jekyll!"
date:   2013-02-19 21:28:15 +0700
categories: [jekyll]
---
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js"></script>
<script src="http://code.highcharts.com/highcharts.js"></script>
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

<script type="text/javascript">

        $('#container').highcharts({
            title: {
                text: 'Monthly Average Temperature',
                x: -20 //center
            },
            subtitle: {
                text: 'Source: WorldClimate.com',
                x: -20
            },
            xAxis: {
                categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun',
                    'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
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
            series: [{
                name: 'Tokyo',
                data: [7.0, 6.9, 9.5, 14.5, 18.2, 21.5, 25.2, 26.5, 23.3, 18.3, 13.9, 9.6]
            }, {
                name: 'New York',
                data: [-0.2, 0.8, 5.7, 11.3, 17.0, 22.0, 24.8, 24.1, 20.1, 14.1, 8.6, 2.5]
            }, {
                name: 'Berlin',
                data: [-0.9, 0.6, 3.5, 8.4, 13.5, 17.0, 18.6, 17.9, 14.3, 9.0, 3.9, 1.0]
            }, {
                name: 'London',
                data: [3.9, 4.2, 5.7, 8.5, 11.9, 15.2, 17.0, 16.6, 14.2, 10.3, 6.6, 4.8]
            }]
        });

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