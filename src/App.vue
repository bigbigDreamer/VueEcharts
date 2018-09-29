<template>
  <b-row>
    <b-col fluid cols="8">
      <b-card>
        <div id="app" :style="{width:100 + '%' ,height:400 + 'px'}">
        </div>
      </b-card>
    </b-col>
    <b-col fluid cols="4">
      <b-card>
        <b-img :src="require('./assets/logo.png')">
        </b-img>
        <b-button-group class="mx-1">
          <b-btn @click="updateData({
            Java: 65,
            JavaScript: 55,
            Python: 150,
            Ruby: 52,
            Html:52,
            Css: 59,
          })">Java
          </b-btn>
          <b-btn>JavaScript</b-btn>
          <b-btn>Python</b-btn>
        </b-button-group>
        <hr>
        <b-button-group class="mx-1">
          <b-btn>Ruby</b-btn>
          <b-btn>Html</b-btn>
          <b-btn>Css</b-btn>
        </b-button-group>
      </b-card>
    </b-col>
  </b-row>
</template>

<script>
  import {mapState, mapActions} from 'vuex'

  export default {
    name: 'App',
    mounted() {
      let myChart = this.$echarts.init(document.getElementById('app'));
      let options = ({
        title: {
          text: '工大编程语言使用分析柱状图'
        },
        tooltip: {},
        xAxis: {
          data: ['Java', 'JavaScript', 'Python', 'Ruby', 'Html', 'Css']
        },
        yAxis: {},
        series: [{
          name: '使用量',
          type: 'bar',
          data: [this.Java, this.JavaScript, this.Python, this.Ruby, this.Html, this.Css]
        }]
      });
      myChart.setOption(options);
    },
    computed: {
      ...mapState([
        'Java',
        'JavaScript',
        'Python',
        'Ruby',
        'Html',
        'Css',
      ])
    },
    methods: {
      ...mapActions([
        'updateData'
      ])
    },
    watch: {
      Css: function () {
        let myChart = this.$echarts.init(document.getElementById('app'));
        let options = ({
          title: {
            text: '工大编程语言使用分析柱状图'
          },
          tooltip: {},
          xAxis: {
            data: ['Java', 'JavaScript', 'Python', 'Ruby', 'Html', 'Css']
          },
          yAxis: {},
          series: [{
            name: '使用量',
            type: 'bar',
            data: [this.Java, this.JavaScript, this.Python, this.Ruby, this.Html, this.Css]
          }]
        });
        myChart.setOption(options);
      }
    },
    data() {
      return {}
    }
  }
</script>

<style>

</style>
