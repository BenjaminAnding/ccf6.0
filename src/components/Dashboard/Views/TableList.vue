<template>
    <div>
      <div class="row">
        <div class="col">
          <div id="regions_div" style="width: 900px; height: 500px;"></div>
        </div>
        <div class="col">
          <div id="regions_div2" style="width: 900px; height: 500px;"></div>
        </div>
        <div class="col">
          <div id="regions_div3" style="width: 900px; height: 500px;"></div>
        </div>
      </div>
    </div>
  
</template>

<script type="text/javascript">
export default{
  created () {
    google.charts.load('current', {
      'packages': ['geochart'],
      // Note: you will need to get a mapsApiKey for your project.
      // See: https://developers.google.com/chart/interactive/docs/basic_load_libs#load-settings
      'mapsApiKey': 'AIzaSyC_9CcFHn6Vi_o5oDQhvzexjf2HG01mpxM'
    })

    google.charts.setOnLoadCallback(drawRegionsMap)

    function drawRegionsMap () {
      var data = google.visualization.arrayToDataTable([
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
      ])

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
      var data = google.visualization.arrayToDataTable([
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
      ])

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
      var data = google.visualization.arrayToDataTable([
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
      ])

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
