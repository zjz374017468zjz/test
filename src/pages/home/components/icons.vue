<template>
    <div class="icons">
        
        <swiper :options="swiperOption">
            <swiper-slide v-for = "(page , index) of pages" :key="index">
                <div class="icon" v-for="item of page" :key="item.id">
                    <img :src="item.imgUrl" alt="" />
                    <span>{{item.desc}}</span>
                </div>
            </swiper-slide>
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
</template>

<script>
export default {
  name: 'Icons',
  props:{
    list:Array
  },
  data(){
    return{
        swiperOption: {
            pagination: '.swiper-pagination',
            // loop: true
        },
    }
  },
  computed: {
    pages () {
        const pages = [];
        this.list.forEach((item, index) => {
            const page = Math.floor( index/8 );
            if (!pages[page]){
                pages[page] = [];
            }
            pages[page].push(item);
        })
        return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
    // @import '~sty/varibles.styl'
    

    .icons >>> .swiper-pagination-bullet-active
        background:rgba(0,175,190,.8)
    .icons >>> .swiper-pagination-bullets
        bottom:0.10rem
        
    .icons >>> .swiper-pagination-bullet
        width: 6px;
        height: 6px;
        
    .icons
        overflow:hidden
        .icon
            width:25%
            float:left
            padding-top:0.10rem
            .icon 
            img
                display: block
                width:1.1rem
                height:1.1rem
                margin:0 auto
            .icon 
            span
                display:block
                font-size:0.28
                color:#333
                text-align:center
                margin-top:0.10rem
                
</style>
