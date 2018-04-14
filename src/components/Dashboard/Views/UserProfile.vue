<template>
    <div class="row">
      <div class="col-lg-4 col-md-5">
        <user-card :info="doctor">

        </user-card>
        <!--<members-card>-->

        <!--</members-card>-->

        <div class="form-row">
          <div class="col">
            <select v-model="state" class="form-control" @change="drawMap()">
              <option value="" disabled selected>Select your state</option>
              <option value="AK">Alaska</option>
              <option value="AL">Alabama</option>
              <option value="AR">Arkansas</option>
              <option value="AZ">Arizona</option>
              <option value="CA">California</option>
              <option value="CO">Colorado</option>
              <option value="CT">Connecticut</option>
              <option value="DC">District of Columbia</option>
              <option value="DE">Delaware</option>
              <option value="FL">Florida</option>
              <option value="GA">Georgia</option>
              <option value="HI">Hawaii</option>
              <option value="IA">Iowa</option>
              <option value="ID">Idaho</option>
              <option value="IL">Illinois</option>
              <option value="IN">Indiana</option>
              <option value="KS">Kansas</option>
              <option value="KY">Kentucky</option>
              <option value="LA">Louisiana</option>
              <option value="MA">Massachusetts</option>
              <option value="MD">Maryland</option>
              <option value="ME">Maine</option>
              <option value="MI">Michigan</option>
              <option value="MN">Minnesota</option>
              <option value="MO">Missouri</option>
              <option value="MS">Mississippi</option>
              <option value="MT">Montana</option>
              <option value="NC">North Carolina</option>
              <option value="ND">North Dakota</option>
              <option value="NE">Nebraska</option>
              <option value="NH">New Hampshire</option>
              <option value="NJ">New Jersey</option>
              <option value="NM">New Mexico</option>
              <option value="NV">Nevada</option>
              <option value="NY">New York</option>
              <option value="OH">Ohio</option>
              <option value="OK">Oklahoma</option>
              <option value="OR">Oregon</option>
              <option value="PA">Pennsylvania</option>
              <option value="PR">Puerto Rico</option>
              <option value="RI">Rhode Island</option>
              <option value="SC">South Carolina</option>
              <option value="SD">South Dakota</option>
              <option value="TN">Tennessee</option>
              <option value="TX">Texas</option>
              <option value="UT">Utah</option>
              <option value="VA">Virginia</option>
              <option value="VT">Vermont</option>
              <option value="WA">Washington</option>
              <option value="WI">Wisconsin</option>
              <option value="WV">West Virginia</option>
              <option value="WY">Wyoming</option>
            </select>
          </div>
          <div class="col">
            <input type="text" class="form-control" v-model="city" @blur="drawMap()">
          </div>
          <div class="col">
            <input type="number" class="form-control" v-model="limit" placeholder="Limit" @blur="drawMap()">
          </div>
        </div>


        <div class="card">
          <div class="header">
            <h4 class="title">{{title}}</h4>
          </div>
          <div class="content">
            <ul class="list-unstyled team-members">
              <li>
                <div class="row" v-for="member in data">
                  <div class="col-xs-3">
                    <div class="avatar">
                      <img src="static/img/person-male.png" alt="Circle Image" class="img-circle img-no-padding img-responsive">
                    </div>
                  </div>
                  <div class="col-xs-6">
                    <a class="btn btn-success" @click="fillCard(member)">
                      {{capitalizeFirstLetter(member['nppes_provider_first_name'].toLowerCase()) + ' ' + capitalizeFirstLetter(member['nppes_provider_last_org_name'].toLowerCase())}}
                    </a>
                    <!--<span :class="getStatusClass(member.status)">-->
                <!--<small>{{member.status}}</small>-->
              <!--</span>-->
                  </div>

                  <div class="col-xs-3 text-right">
                    <button class="btn btn-sm btn-success btn-icon">
                      <i class="fa fa-envelope"></i>
                    </button>
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>


      </div>
      <div class="col-lg-8 col-md-7">
        <div class="card">
          <div class="header">
            <h4 class="title">Doctor Map</h4>
          </div>
          <div class="content">
            <form>
              <!--<div class="row">-->
              <!--<div class="col-md-5">-->
              <!--<fg-input type="text"-->
              <!--label="Company"-->
              <!--:disabled="true"-->
              <!--placeholder="Paper dashboard"-->
              <!--v-model="user.company">-->
              <!--</fg-input>-->
              <!--</div>-->
              <!--<div class="col-md-3">-->

              <!--<fg-input type="text"-->
              <!--label="Username"-->
              <!--placeholder="Username"-->
              <!--v-model="user.username">-->
              <!--</fg-input>-->
              <!--</div>-->
              <!--<div class="col-md-4">-->
              <!--<fg-input type="email"-->
              <!--label="Username"-->
              <!--placeholder="Email"-->
              <!--v-model="user.email">-->
              <!--</fg-input>-->
              <!--</div>-->
              <!--</div>-->

              <!--<div class="row">-->
              <!--<div class="col-md-6">-->
              <!--<fg-input type="text"-->
              <!--label="First Name"-->
              <!--placeholder="First Name"-->
              <!--v-model="user.firstName">-->
              <!--</fg-input>-->
              <!--</div>-->
              <!--<div class="col-md-6">-->
              <!--<fg-input type="text"-->
              <!--label="Last Name"-->
              <!--placeholder="Last Name"-->
              <!--v-model="user.lastName">-->
              <!--</fg-input>-->
              <!--</div>-->
              <!--</div>-->

              <!--<div class="row">-->
              <!--<div class="col-md-12">-->
              <!--<fg-input type="text"-->
              <!--label="Address"-->
              <!--placeholder="Home Address"-->
              <!--v-model="user.address">-->
              <!--</fg-input>-->
              <!--</div>-->
              <!--</div>-->

              <!--<div class="row">-->
              <!--<div class="col-md-4">-->
              <!--<fg-input type="text"-->
              <!--label="City"-->
              <!--placeholder="City"-->
              <!--v-model="user.city">-->
              <!--</fg-input>-->
              <!--</div>-->
              <!--<div class="col-md-4">-->
              <!--<fg-input type="text"-->
              <!--label="Country"-->
              <!--placeholder="Country"-->
              <!--v-model="user.country">-->
              <!--</fg-input>-->
              <!--</div>-->
              <!--<div class="col-md-4">-->
              <!--<fg-input type="number"-->
              <!--label="Postal Code"-->
              <!--placeholder="ZIP Code"-->
              <!--v-model="user.postalCode">-->
              <!--</fg-input>-->
              <!--</div>-->
              <!--</div>-->

              <!--<div class="row">-->
              <!--<div class="col-md-12">-->
              <!--<div class="form-group">-->
              <!--<label>About Me</label>-->
              <!--<textarea rows="5" class="form-control border-input"-->
              <!--placeholder="Here can be your description"-->
              <!--v-model="user.aboutMe">-->

              <!--</textarea>-->
              <!--</div>-->
              <!--</div>-->
              <!--</div>-->
              <!--<div class="text-center">-->
              <!--<button type="submit" class="btn btn-info btn-fill btn-wd" @click.prevent="updateProfile">-->
              <!--Update Profile-->
              <!--</button>-->
              <!--</div>-->
              <!--<div class="clearfix"></div>-->
            </form>
            <div id="chart_div" style="width: 900px; height: 500px;"></div>
          </div>
        </div>
      </div>
    </div>
</template>
<script type="text/javascript">
  /* eslint-disable no-trailing-spaces */
  import DoctorMap from './UserProfile/DoctorMap.vue'
  import UserCard from './UserProfile/UserCard.vue'
  import MembersCard from './UserProfile/MembersCard.vue'
  import axios from 'axios'

  export default {
    components: {
      DoctorMap,
      UserCard,
      MembersCard
    },
    data () {
      return {
        title: 'Doctor List',
        doctor: {},
        state: 'LA',
        city: 'Lafayette',
        limit: 10,
        data: []
      }
    },
    methods: {
      fillCard (value) {
        this.doctor = value
      },
      capitalizeFirstLetter (string) {
        return string.charAt(0).toUpperCase() + string.slice(1)
      },
      drawMap () {
        let endpoint = 'https://data.cms.gov/resource/x77v-hecv.json?'
        if (this.state !== '') {
          endpoint += 'nppes_provider_state=' + this.state
        }
        if (this.city !== '') {
          endpoint += '&nppes_provider_city=' + this.city.toUpperCase()
        }
        endpoint += '&$limit=' + this.limit
        console.log(endpoint)
        var self = this
        axios.get(endpoint)
          .then(function (response) {
            console.log(response)
            self.data = response.data
          })
      },
      getPrepData () {
        let endpoint = 'https://data.cms.gov/resource/sbka-mk55.json'
        var res = []
        var self = this
        res.push(['City', 'Total Number Doctor', 'Total Number of Claim'])

        axios.get(endpoint)
          .then(function (response) {
            var data = response.data
            for (var i = 0; i < data.length; i++) {
//              if (i >= 10) break
              var city = data[i]['nppes_provider_city']
              city = self.capitalizeFirstLetter(city.toLowerCase())
              var temp = [city, parseInt(data[i]['count_nppes_provider_last_org_name']), parseInt(data[i]['sum_total_claim_count'])]
              res.push(temp)
            }
          })
        return res
      }
    },
    created () {
      this.drawMap()

      google.charts.load('current', {
        'packages': ['geochart'],
        // Note: you will need to get a mapsApiKey for your project.
        // See: https://developers.google.com/chart/interactive/docs/basic_load_libs#load-settings
        'mapsApiKey': 'AIzaSyD-9tSrke72PouQMnMX-a7eZSW0jkFMBWY'
      })
      google.charts.setOnLoadCallback(drawMarkersMap)

      var prepData = this.getPrepData()
      console.log(prepData)

      var st = [
        ['Country', 'Population', 'Area Percentage'],
        ['Turtle creek', 1, 13],
        ['Stinson beach', 1, 16],
        ['Hapeville', 1, 22]
      ]

      console.log(st)

      function drawMarkersMap () {
        var data = google.visualization.arrayToDataTable(prepData)

        var options = {
          region: 'US',
          displayMode: 'markers',
          colorAxis: {colors: ['green', 'blue']}
        }

        var chart = new google.visualization.GeoChart(document.getElementById('chart_div'))
        chart.draw(data, options)
      }
    }
  }

</script>
<style>

</style>
