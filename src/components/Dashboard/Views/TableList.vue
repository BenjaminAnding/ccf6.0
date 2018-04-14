<template>
    <div>
      <button class="btn btn-danger" @click="type = !type">Toggle Graph Type</button>
      <div class="row">
        <div class="col graph" v-show="type">
          <h1 class="title">Interactive Prescription Statistic Data Graph 2013</h1>
          <div id="regions_div" style="width: 900px; height: 500px;"></div>
        </div>
        <div class="col graph" v-show="type">
          <h1 class="title">Interactive Prescription Statistic Data Graph 2014</h1>
          <div id="regions_div2" style="width: 900px; height: 500px;"></div>
        </div>
        <div class="col graph" v-show="type">
          <h1 class="title">Interactive Prescription Statistic Data Graph 2015</h1>
          <div id="regions_div3" style="width: 900px; height: 500px;"></div>
        </div>
        <!--<div class="col graph" v-show="type">-->
          <!--<h1 class="title">Interactive Prescription Statistic Data Graph 2015</h1>-->
          <!--<div id="curve_chart" style="width: 900px!important; height: 500px!important;"></div>-->
        <!--</div>-->


          <select multiple class="form-control" v-model="choosen">
            <option value="" disabled selected>Select your state</option>
            <option value="US-AK">Alaska</option>
            <option value="US-AL">Alabama</option>
            <option value="US-AR">Arkansas</option>
            <option value="US-AZ">Arizona</option>
            <option value="US-CA">California</option>
            <option value="US-CO">Colorado</option>
            <option value="US-CT">Connecticut</option>
            <option value="US-DC">District of Columbia</option>
            <option value="US-DE">Delaware</option>
            <option value="US-FL">Florida</option>
            <option value="US-GA">Georgia</option>
            <option value="US-HI">Hawaii</option>
            <option value="US-IA">Iowa</option>
            <option value="US-ID">Idaho</option>
            <option value="US-IL">Illinois</option>
            <option value="US-IN">Indiana</option>
            <option value="US-KS">Kansas</option>
            <option value="US-KY">Kentucky</option>
            <option value="US-LA">Louisiana</option>
            <option value="US-MA">Massachusetts</option>
            <option value="US-MD">Maryland</option>
            <option value="US-ME">Maine</option>
            <option value="US-MI">Michigan</option>
            <option value="US-MN">Minnesota</option>
            <option value="US-MO">Missouri</option>
            <option value="US-MS">Mississippi</option>
            <option value="US-MT">Montana</option>
            <option value="US-NC">North Carolina</option>
            <option value="US-ND">North Dakota</option>
            <option value="US-NE">Nebraska</option>
            <option value="US-NH">New Hampshire</option>
            <option value="US-NJ">New Jersey</option>
            <option value="US-NM">New Mexico</option>
            <option value="US-NV">Nevada</option>
            <option value="US-NY">New York</option>
            <option value="US-OH">Ohio</option>
            <option value="US-OK">Oklahoma</option>
            <option value="US-OR">Oregon</option>
            <option value="US-PA">Pennsylvania</option>
            <option value="US-PR">Puerto Rico</option>
            <option value="US-RI">Rhode Island</option>
            <option value="US-SC">South Carolina</option>
            <option value="US-SD">South Dakota</option>
            <option value="US-TN">Tennessee</option>
            <option value="US-TX">Texas</option>
            <option value="US-UT">Utah</option>
            <option value="US-VA">Virginia</option>
            <option value="US-VT">Vermont</option>
            <option value="US-WA">Washington</option>
            <option value="US-WI">Wisconsin</option>
            <option value="US-WV">West Virginia</option>
            <option value="US-WY">Wyoming</option>
          </select>
        <button class="btn btn-danger" @click="graph()">Graph</button>
        <div class="row">
          <div class="col graph">
            <h1 class="title">Interactive Prescription Statistic Data Graph 2015</h1>
            <div id="curve_chart" style="width: 900px!important; height: 500px!important;"></div>
          </div>
        </div>
      </div>

    </div>
  
</template>

<script type="text/javascript">
export default{
  data () {
    return {
      choosen: [],
      type: true,
      data2015: [
        ['State', 'Average Opioid Claim'],
        ['test', 55],
        ['test', 20],
        ['US-AL', 51.9],
        ['US-AK', 29.7],
        ['US-AZ', 35.5],
        ['US-AR', 45],
        ['US-CA', 31],
        ['US-CO', 30.7],
        ['US-CT', 33.9],
        ['US-DE', 39.8],
        ['US-DC', 25.3],
        ['US-FL', 53.2],
        ['US-GA', 48.2],
        ['US-HI', 27.2],
        ['US-ID', 36.5],
        ['US-IL', 34.7],
        ['US-IN', 40.3],
        ['US-IA', 36.5],
        ['US-KS', 36.4],
        ['US-KY', 43.6],
        ['US-LA', 50.2],
        ['US-ME', 31.4],
        ['US-MT', 35.2],
        ['US-NE', 35],
        ['US-NV', 36.1],
        ['US-NH', 31.7],
        ['US-NJ', 36.1],
        ['US-NM', 30],
        ['US-NY', 31],
        ['US-NC', 41.7],
        ['US-ND', 40.6],
        ['US-OH', 35.7],
        ['US-OK', 53.5],
        ['US-OR', 31.3],
        ['US-MD', 35.7],
        ['US-MA', 27.3],
        ['US-MI', 38.1],
        ['US-MN', 30.6],
        ['US-MS', 46.2],
        ['US-MO', 42.2],
        ['US-PA', 36.2],
        ['US-RI', 28.1],
        ['US-SC', 40.7],
        ['US-SD', 40.9],
        ['US-TN', 42.3],
        ['US-TX', 45.3],
        ['US-UT', 33],
        ['US-VT', 30.5],
        ['US-VA', 34.4],
        ['US-WA', 30.7],
        ['US-WV', 39.4],
        ['US-WI', 35],
        ['US-WY', 29.2]
      ],
      data2014: [
        ['State', 'Average Opioid Claim'],
        ['test', 55],
        ['test', 20],
        ['US-AL', 51.3],
        ['US-AK', 30.4],
        ['US-AZ', 34.7],
        ['US-AR', 44.2],
        ['US-CA', 30.7],
        ['US-CO', 30.1],
        ['US-CT', 34],
        ['US-DE', 40],
        ['US-DC', 27.2],
        ['US-FL', 48.8],
        ['US-GA', 47],
        ['US-HI', 26.5],
        ['US-ID', 37.5],
        ['US-IL', 34.9],
        ['US-IN', 39.6],
        ['US-IA', 36.5],
        ['US-KS', 36.3],
        ['US-KY', 43.4],
        ['US-LA', 47.6],
        ['US-ME', 31.7],
        ['US-MT', 33.9],
        ['US-NE', 35.2],
        ['US-NV', 35.2],
        ['US-NH', 32.4],
        ['US-NJ', 35.5],
        ['US-NM', 30.3],
        ['US-NY', 30.6],
        ['US-NC', 41.3],
        ['US-ND', 40.6],
        ['US-OH', 35.6],
        ['US-OK', 50.3],
        ['US-OR', 31.3],
        ['US-MD', 35],
        ['US-MA', 27.2],
        ['US-MI', 38],
        ['US-MN', 31],
        ['US-MS', 43.7],
        ['US-MO', 42.2],
        ['US-PA', 36.2],
        ['US-RI', 26.9],
        ['US-SC', 40.3],
        ['US-SD', 38.7],
        ['US-TN', 43.7],
        ['US-TX', 43],
        ['US-UT', 32.1],
        ['US-VT', 30],
        ['US-VA', 31],
        ['US-WA', 31.2],
        ['US-WV', 38.2],
        ['US-WI', 35.6],
        ['US-WY', 29.8]
      ],
      data2013: [
        ['State', 'Average Opioid Claim'],
        ['test', 55],
        ['test', 20],
        ['US-AL', 47.25],
        ['US-AK', 27.2],
        ['US-AZ', 32.1],
        ['US-AR', 44.3],
        ['US-CA', 30.8],
        ['US-CO', 31],
        ['US-CT', 34.3],
        ['US-DE', 38.9],
        ['US-DC', 27.5],
        ['US-FL', 46.4],
        ['US-GA', 45.2],
        ['US-HI', 26.5],
        ['US-ID', 37.7],
        ['US-IL', 35.3],
        ['US-IN', 39.1],
        ['US-IA', 36.1],
        ['US-KS', 36],
        ['US-KY', 43],
        ['US-LA', 45.9],
        ['US-ME', 30.7],
        ['US-MT', 35],
        ['US-NE', 34.3],
        ['US-NV', 33],
        ['US-NH', 32.9],
        ['US-NJ', 35.9],
        ['US-NM', 29.8],
        ['US-NY', 30.2],
        ['US-NC', 40.3],
        ['US-ND', 40.3],
        ['US-OH', 36.5],
        ['US-OK', 46.6],
        ['US-OR', 31.3],
        ['US-MD', 32.2],
        ['US-MA', 27],
        ['US-MI', 38.3],
        ['US-MN', 30.9],
        ['US-MS', 41.8],
        ['US-MO', 41.4],
        ['US-PA', 36.7],
        ['US-RI', 28.2],
        ['US-SC', 38.8],
        ['US-SD', 40.6],
        ['US-TN', 43.4],
        ['US-TX', 42.4],
        ['US-UT', 30.3],
        ['US-VT', 29.8],
        ['US-VA', 34.1],
        ['US-WA', 30.3],
        ['US-WV', 37.9],
        ['US-WI', 34.6],
        ['US-WY', 27.7]
      ]
    }
  },
  methods: {
    graph () {
      console.log(this.choosen)
      for (var i = 0; i < this.choosen.length; i++) {
        console.log(this.choosen[i])
      }
      google.charts.setOnLoadCallback(drawChartCurve)
      var datacurve = this.prepareData()
//    console.log(datacurve)
      function drawChartCurve () {
        var data = google.visualization.arrayToDataTable(datacurve)

        var options = {
          title: 'Company Performance',
          curveType: 'function',
          legend: { position: 'bottom' }
        }

        var chart = new google.visualization.LineChart(document.getElementById('curve_chart'))

        chart.draw(data, options)
      }
    },
    prepareData () {
      var res = []
      var temp = []
      temp.push('Year')
      for (var i = 3; i < this.data2015.length; i++) {
        var item = this.data2015[i]
//        console.log(item)
        if (this.choosen.includes(item[0])) {
          temp.push(item[0])
        }
      }
      res.push(temp)

      temp = ['2013']
      for (i = 3; i < this.data2013.length; i++) {
        item = this.data2013[i]
        if (this.choosen.includes(item[0])) {
          temp.push(item[1])
        }
      }
      res.push(temp)

      temp = ['2014']
      for (i = 3; i < this.data2014.length; i++) {
        item = this.data2014[i]
        if (this.choosen.includes(item[0])) {
          temp.push(item[1])
        }
      }
      res.push(temp)

      temp = ['2015']
      for (i = 3; i < this.data2015.length; i++) {
        item = this.data2015[i]
        if (this.choosen.includes(item[0])) {
          temp.push(item[1])
        }
      }
      res.push(temp)
      return res
    }
  },
  created () {
    google.charts.load('current', {
      'packages': ['geochart', 'corechart'],
      // Note: you will need to get a mapsApiKey for your project.
      // See: https://developers.google.com/chart/interactive/docs/basic_load_libs#load-settings
      'mapsApiKey': 'AIzaSyC_9CcFHn6Vi_o5oDQhvzexjf2HG01mpxM'
    })
    var self = this

    google.charts.setOnLoadCallback(drawRegionsMap)

    function drawRegionsMap () {
      var data = google.visualization.arrayToDataTable(self.data2013)

      var options = {
        region: 'US',
        displayMode: 'regions',
        colorAxis: {colors: ['white', '#e31b23']},
        resolution: 'provinces'
      }

      var chart = new google.visualization.GeoChart(document.getElementById('regions_div'))
      chart.draw(data, options)
    }

    google.charts.setOnLoadCallback(drawRegionsMap2)
    function drawRegionsMap2 () {
      var data = google.visualization.arrayToDataTable(self.data2014)

      var options = {
        region: 'US',
        displayMode: 'regions',
        colorAxis: {colors: ['white', '#e31b23']},
        resolution: 'provinces'
      }

      var chart = new google.visualization.GeoChart(document.getElementById('regions_div2'))
      chart.draw(data, options)
    }

    google.charts.setOnLoadCallback(drawRegionsMap3)
    function drawRegionsMap3 () {
      var data = google.visualization.arrayToDataTable(self.data2015)

      var options = {
        region: 'US',
        displayMode: 'regions',
        colorAxis: {colors: ['white', '#e31b23']},
        resolution: 'provinces'
      }

      var chart = new google.visualization.GeoChart(document.getElementById('regions_div3'))
      chart.draw(data, options)
    }
  }
}

</script>
