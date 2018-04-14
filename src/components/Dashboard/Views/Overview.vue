<template>
  <div id="app">
  <!--Stats cards-->
    <div class="row">
      <div class="col-lg-3 col-sm-3" v-for="stats in statsCards">
        <stats-card>
          <div class="icon-big text-center" :class="`icon-${stats.type}`" slot="header">
            <i :class="stats.icon"></i>
          </div>
          <div class="numbers" slot="content">
            <p>{{stats.title}}</p>
            <p><strong>{{stats.value}}</strong></p>
          </div>
          <div class="stats" slot="footer">
            <i :class="stats.footerIcon"></i> {{stats.footerText}}
          </div>
        </stats-card>
      </div>
    </div>

    <!--Charts-->
    <div class="row">
      <main>


        <div v-if="loading">
          Loading.....
        </div>
        <div class="wrapper">
          <div class="row">
            <div v-for="article in news" :key="article.source" v-show="article.urlToImage != null ">
              <!--<div class="col-md-4 cards">-->
                <!--<img :src="article.urlToImage" class="img-responsive">-->
                <!--<div>-->
                  <!--<p><a :href="article.url">{{ article.title }}</a></p>-->
                  <!--<a></a>-->

                <!--</div>-->
              <!--</div>-->

              <div class="card col-sm-4 col-xs-offset-0" style="max-height: 40rem;">
                <img class="" :src="article.urlToImage" alt="Card image cap" style="width: 286px; height: 180px">
                <div class="card-body">
                  <h5 class="card-title"><a :href="article.url">{{ article.title | truncate(50) }}</a></h5>

                  <!--<p class="card-text"></p>-->
                  <!--<a href="#" class="btn btn-primary">Go somewhere</a>-->
                </div>
              </div>
            </div>
          </div>
        </div>
      </main>
    </div>

      <div class="container">
        <h4 class="uppercase">Comments</h4>
        <div class="review" v-for="review in reviews">
          <p>{{ review.content }}</p>
          <div class="row">
            <div class="columns medium-7">
              <h5>{{ review.reviewer }}</h5>
            </div>
            <div class="columns medium-5">
              <h5 class="pull-right">{{ review.time }}</h5>
            </div>
          </div>
        </div>
        <div class="review-form">
          <h5>add new comment.</h5>
          <form @submit.prevent="addReview">
            <label>
              Comment
              <textarea v-model="review.content" cols="30" rows="5"></textarea>
            </label>
            <div></div>
            <label>
              Name
              <input v-model="review.reviewer" type="text">
            </label>
            <div></div>
            <button :disabled="!review.reviewer || !review.content" type="submit" class="button expanded">Submit</button>
          </form>
        </div>

      <div class="col-md-6 col-xs-12">
        <chart-card :chart-data="preferencesChart.data"  chart-type="Pie">
          <h4 class="title" slot="title">Email Statistics</h4>
          <span slot="subTitle"> Last campaign performance</span>
          <span slot="footer">
            <i class="ti-timer"></i> Campaign set 2 days ago</span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Open
            <i class="fa fa-circle text-danger"></i> Bounce
            <i class="fa fa-circle text-warning"></i> Unsubscribe
          </div>
        </chart-card>
      </div>

      <div class="col-md-6 col-xs-12">
        <chart-card :chart-data="activityChart.data" :chart-options="activityChart.options">
          <h4 class="title" slot="title">2015 Sales</h4>
          <span slot="subTitle"> All products including Taxes</span>
          <span slot="footer">
            <i class="ti-check"></i> Data information certified</span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Tesla Model S
            <i class="fa fa-circle text-warning"></i> BMW 5 Series
          </div>
        </chart-card>
      </div>
    </div>


  </div>
</template>
<script>
  import StatsCard from 'components/UIComponents/Cards/StatsCard.vue'
  import ChartCard from 'components/UIComponents/Cards/ChartCard.vue'
  import axios from 'axios'
  export default {
    nameA: 'app',
    nameB: 'reviews',
    components: {
      StatsCard,
      ChartCard
    },
    data () {
      return {
        mockReviews: [],
        review: {
          content: '',
          reviewer: ''
        },
        news: [],
        loading: false,
        statsCards: [
          {
            type: 'warning',
            icon: 'ti-server',
            title: 'Opioid Prescriptions',
            value: '105 Million',
            footerText: 'Updated now',
            footerIcon: 'ti-reload'
          },
          {
            type: 'success',
            icon: 'ti-wallet',
            title: 'Funds Raised',
            value: '$1,345',
            footerText: 'Last day',
            footerIcon: 'ti-calendar'
          },
          {
            type: 'danger',
            icon: 'ti-pulse',
            title: 'Opium Death',
            value: '23',
            footerText: 'In the last hour',
            footerIcon: 'ti-timer'
          },
          {
            type: 'info',
            icon: 'ti-twitter-alt',
            title: 'Topics',
            value: '+45',
            footerText: 'Updated now',
            footerIcon: 'ti-reload'
          }
        ],
        usersChart: {
          data: {
            labels: ['9:00AM', '12:00AM', '3:00PM', '6:00PM', '9:00PM', '12:00PM', '3:00AM', '6:00AM'],
            series: [
                          [287, 385, 490, 562, 594, 626, 698, 895, 952],
                          [67, 152, 193, 240, 387, 435, 535, 642, 744],
                          [23, 113, 67, 108, 190, 239, 307, 410, 410]
            ]
          },
          options: {
            low: 0,
            high: 1000,
            showArea: true,
            height: '245px',
            axisX: {
              showGrid: false
            },
            lineSmooth: this.$Chartist.Interpolation.simple({
              divisor: 3
            }),
            showLine: true,
            showPoint: false
          }
        },
        activityChart: {
          data: {
            labels: ['Jan', 'Feb', 'Mar', 'Apr', 'Mai', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
            series: [
                          [542, 543, 520, 680, 653, 753, 326, 434, 568, 610, 756, 895],
                          [230, 293, 380, 480, 503, 553, 600, 664, 698, 710, 736, 795]
            ]
          },
          options: {
            seriesBarDistance: 10,
            axisX: {
              showGrid: false
            },
            height: '245px'
          }
        },
        preferencesChart: {
          data: {
            labels: ['62%', '32%', '6%'],
            series: [62, 32, 6]
          },
          options: {}
        }

      }
    },
    methods: {
      getNews: function () {
        this.loading = true
        var self = this
        axios.get('https://newsapi.org//v2/everything?q=Opiods&sortBy=popularity&apiKey=f0031e54e7844ca8a085972f3a24115b')
                  .then((response) => {
                    self.loading = false
                    self.news = response.data.articles
                    console.log(response.data)
                  }, () => {
                    this.loading = false
                  })
      },
      addReview () {
        if (!this.review.reviewer || !this.review.content) {
          return
        }
        let review = {
          content: this.review.content,
          reviewer: this.review.reviewer,
          time: new Date().toLocaleDateString()
        }
        this.mockReviews.unshift(review)
      }
    },
    created: function () {
      this.getNews()
    },
    computed: {
      reviews () {
        return this.mockReviews.filter(review => {
          return review
        })
      }
    }
  }
</script>
<style>

</style>
