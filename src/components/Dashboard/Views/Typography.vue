<template>
  <div id='columnchart_values' style='width: 900px height: 300px'></div>
</template>
<script>
  import axios from 'axios'

  export default {
    data () {
      return {
        dataSource: [
          'https://data.medicaid.gov/resource/au58-3g3e.json?$select=sum(number_of_prescriptions)&$where=upper(product_fda_list_name)="OXYCONTIN" OR upper(product_fda_list_name)="VICODIN"',
          'https://data.medicaid.gov/resource/jzhb-tr7x.json?$select=sum(number_of_prescriptions)&$where=upper(product_fda_list_name)="OXYCONTIN" OR upper(product_fda_list_name)="VICODIN"',
          'https://data.medicaid.gov/resource/hcg7-jjb2.json?$select=sum(number_of_prescriptions)&$where=upper(product_fda_list_name)="OXYCONTIN" OR upper(product_fda_list_name)="VICODIN"',
          'https://data.medicaid.gov/resource/qpz6-74iw.json?$select=sum(number_of_prescriptions)&$where=upper(product_fda_list_name)="OXYCONTIN" OR upper(product_fda_list_name)="VICODIN"',
          'https://data.medicaid.gov/resource/m4ab-dkvc.json?$select=sum(number_of_prescriptions)&$where=upper(product_fda_list_name)="OXYCONTIN" OR upper(product_fda_list_name)="VICODIN"'
        ],
        dataColor: [
          '#b87333',
          'silver',
          'gold',
          '#e5e4e2',
          'purple'
        ],
        res1: [],
        res2: []
      }
    },
    methods: {
      getPrepData () {
        var res = []
        res.push(['Year', 'Number of Perscriptions', {role: 'style'}, 'Number of Deaths', {role: 'style'}])
        res.push(['2011', 896303, 'purple', 219774, 'blue'])
        res.push(['2012', 359447, 'purple', 2622, 'blue'])
        res.push(['2013', 394620, 'purple', 18321, 'blue'])
        res.push(['2014', 441772, 'purple', 34033, 'blue'])
        res.push(['2015', 748849, 'purple', 627354, 'blue'])

        return res
      },
      getPrepData2 () {
        var res = []
        var self = this
        res.push(['Year', 'Number of Perscriptions', { role: 'style' }, 'Number of Deaths', { role: 'style' }])
        for (var i = 0; i < self.dataSource.length; i++) {
          var tmp
          axios.get(self.dataSource[i])
            .then(function (value1) {
              var item = value1.data
              console.log(i)
              tmp = [parseInt(item[0]['sum_number_of_prescriptions'])]
              res.push(tmp)
            })
        }
        return res
      },
      drawGraph () {
        google.charts.load('current', {packages: ['corechart']})
        google.charts.setOnLoadCallback(drawChart)

        var prepData = this.getPrepData()

        console.log(prepData)
        function drawChart () {
          var data = google.visualization.arrayToDataTable(prepData)

          var view = new google.visualization.DataView(data)
          view.setColumns([0, 1,
            {
              calc: 'stringify',
              sourceColumn: 1,
              type: 'string',
              role: 'annotation'
            }, 2, 3, {
              calc: 'stringify',
              sourceColumn: 3,
              type: 'string',
              role: 'annotation'
            }, 4])

          var options = {
            title: 'Number of Opioid VS Treatment Prescriptions 2011-2015 (US)',
            width: 900,
            height: 600,
            bar: {groupWidth: '95%'},
            legend: {position: 'none'}
          }
          var chart = new google.visualization.ColumnChart(document.getElementById('columnchart_values'))
          chart.draw(view, options)
        }
      }
    },

    created () {
      this.drawGraph()
    }
  }
</script>
