<template>
    <div class="commend">
        <h2 class="com_tit">热销推荐</h2>
        <ul>
            <li class="com_item" v-for="item of list" :key="item.id">
                <img class="com_img" :src="item.imgUrl" />
                <div class="com_text">
                    <p class="p1">{{item.title}}</p>
                    <p class="p2">{{item.desc}}</p>
                    <button class="item-button">查看详情</button>
                </div>
            </li>           
        </ul>
    </div>
</template>

<script>
export default {
    name: 'commend',
    props:{
        list: Array
    }
}
</script>

<style lang="stylus" scoped>
    @import '~sty/varibles.styl'
    .com_tit
        height:0.80rem
        line-height:0.80rem
        background:#eee
        text-indent:0.20rem
        margin-top:0.20rem
        margin-bottom:0.10rem
    .com_item
        overflow:hidden
        display:flex
       
        .com_img
            width:1.7rem
            height:1.7rem
            padding: .1rem
        .com_text
            min-width: 0
            padding: .1rem
            flex:1
            .p1
                line-height: .54rem
                font-size: .32rem
                ellipsis()
            .p2
                line-height: .4rem
                color: #ccc
                ellipsis()
            .item-button
                height:0.44rem
                line-height: .44rem
                margin-top: .16rem
                background: #ff9300
                padding: 0 .2rem
                border-radius: .06rem
                color: #fff
                font-size:0.26rem
</style>
