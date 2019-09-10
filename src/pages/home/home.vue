<template>
<div>
    <home-header></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <home-icons :list="iconList"></home-icons>
    <home-commend :list="recommendList"></home-commend>
    <home-weekend :list="weekendList"></home-weekend>
</div>
</template>

<script>
import HomeHeader from './components/header'
import HomeSwiper from './components/swiper'
import HomeIcons from './components/icons'
import HomeCommend from './components/commend'
import HomeWeekend from './components/weekend'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
      HomeHeader,
      HomeSwiper,
      HomeIcons,
      HomeCommend,
      HomeWeekend
  },
  data(){
    return {      
      swiperList: [],
      iconList:[],
      recommendList:[],
      weekendList:[]     
    }
  },
  methods:{
      getHomeInfo (){
          axios.get('/static/index.json')
            .then(this.getHomeInfoSucc)
      },
      getHomeInfoSucc(res){
          var res = res.data;
          console.log(res)
          if(res.ret && res.data){
              const data = res.data;
              this.swiperList = data.swiperList
              this.iconList = data.iconList
              this.recommendList = data.recommendList
              this.weekendList = data.weekendList
          }
      }
  },
  mounted (){
      this.getHomeInfo()
  }
}
</script>

<style>

</style>
