<template>
    <div class="list" ref="wrapper">
        <div class="listBox">
            <div class="area">
                <div class="title border-topbottom">当前地区</div>
                <div class="current clearfix">
                    <div class="currentBox">
                        <div class="currentCity">{{this.$store.state.city}}</div>
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title border-topbottom">热门城市</div>
                <div class="current clearfix">
                    <div class="currentBox" v-for='item of hot' :key="item.id" @click="handleCityClick(item.name)">
                        <div class="currentCity">{{item.name}}</div>
                    </div>
                </div>
            </div>
            <div class="area" v-for="(item, key) of cities" :key="key" :ref="key">
                <div class="title border-topbottom">{{key}}</div>
                <ul class="itemCity">
                    <li class="border-bottom" v-for='innerItem of item' :key="innerItem.id" @click="handleCityClick(innerItem.name)">{{innerItem.name}}</li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script type="text/javascript">
import Bscroll from 'better-scroll'
    export default {
        name:"CityList",
        props:{
            hot:Array,
            cities:Object,
            letter: String
        },
        methods:{
            handleCityClick(city){
                this.$store.commit('changeCity', city);
                this.$router.push('/')
            }
        },
        mounted () {
            this.scroll = new Bscroll(this.$refs.wrapper);
        },
        watch:{
            letter(){
                if(this.letter){
                    const element = this.$refs[this.letter][0];
                    this.scroll.scrollToElement(element)
                }
            }
        }
    }
</script>

<style lang="stylus" scoped>
    @import '~sty/varibles.styl'
    .border-topbottom
        &:before
            border-color:#ccc
        &:after
            border-color:#ccc
    .list 
        position:absolute
        top:1.58rem
        left: 0
        right:0
        bottom:0
        overflow: hidden
   .title
       line-height:0.54rem
       background:#eee
       padding-left:0.2rem
       color:#666
    .current
        padding: 0.10rem 0.6rem 0.10rem 0.10rem
        .currentBox
            width:33.33%
            float:left
        .currentCity
            border:0.02rem #ccc solid
            font-size:0.24rem
            color:#999
            margin:0.10rem
            padding:0.10rem 0
            text-align:center
            border-radius:0.06rem
    .itemCity
        li
            font-size:0.28rem
            color:#666
            line-height:0.76rem
            padding-left:0.20rem
            
</style>