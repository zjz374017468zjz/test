<template>
    <div class="weekend">
        <h2 class="title">热销推荐</h2>
        <ul>
            <li class="com_item" v-for="item of list" :key="item.id">
                <div class="item-img-wrapper">
                    <img class="item-img" :src="item.imgUrl" />
                </div>
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                </div>
            </li>           
        </ul>
    </div>
</template>

<script>
export default {
    name: 'weekend',
    props:{
        list:Array
    }
    
}
</script>

<style lang="stylus" scoped>
    @import '~sty/varibles.styl'
    .title
        margin-top:0.10rem
        line-height: .8rem
        background: #eee
        text-indent: .2rem
    .item-img-wrapper
        overflow: hidden
        height: 0
        padding-bottom: 37.09%
    .item-img
        width: 100%
    .item-info
        padding: .1rem
    .item-title
        line-height: .54rem
        font-size: .32rem
        ellipsis()
    .item-desc
        line-height: .4rem
        color: #ccc
        ellipsis()
</style>
