<template>
  <div class="card card-user">
    <div class="image">
      <img src="static/img/background.jpg" alt="...">
    </div>
    <div class="content">
      <div class="author">
        <img class="avatar border-white" src="static/img/faces/face-2.jpg" alt="...">
        <h4 class="title">{{ info['nppes_provider_first_name'] + ' ' + info['nppes_provider_last_org_name'] }}
          <br>
          <a href="#">
            <small>@{{ info['npi'] }}</small>
          </a>
        </h4>
      </div>
      <p class="description text-center">
        {{ info['nppes_provider_city'] + ', ' + info['nppes_provider_state'] }}
        <br>Drug name: {{ info['drug_name'] }}
        <br>Description: {{ info['specialty_desc'] }}
      </p>
    </div>
    <hr>
    <div class="text-center">
      <div class="row">
        <div :class="getClasses(0)">
          <h5>{{info.total_claim_count}}
            <br>
            <small>Total Claim</small>
          </h5>
        </div>

        <div :class="getClasses(1)">
          <h5>{{info.total_day_supply}}
            <br>
            <small>Total daily supply</small>
          </h5>
        </div>

        <div :class="getClasses(2)">
          <h5>{{info.total_drug_cost}}
            <br>
            <small>Drug cost $</small>
          </h5>
        </div>

      </div>
    </div>
  </div>
</template>
<script>
  export default {
    props: ['info'],
    data () {
      return {
        details: [
          {
            title: '12',
            subTitle: 'Files'
          },
          {
            title: '2GB',
            subTitle: 'Used'
          },
          {
            title: '24,6$',
            subTitle: 'Spent'
          }
        ]
      }
    },
    methods: {
      getClasses (index) {
        var remainder = index % 3
        if (remainder === 0) {
          return 'col-md-3 col-md-offset-1'
        } else if (remainder === 2) {
          return 'col-md-4'
        } else {
          return 'col-md-3'
        }
      }
    }
  }

</script>
<style>
  
</style>
