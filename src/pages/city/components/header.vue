<template>
    <div class="header">
         城市选择
        <router-link to="/">
            <div class="back">back</div>
        </router-link>
    </div>
</template>

<script type="text/javascript">
    export default {
        name:"CityHeader"
    }
</script>

<style lang="stylus" scoped>
    @import '~sty/varibles.styl'
    .header
        height:0.86rem
        background:$bgColor
        color:#fff
        text-align:center
        line-height:0.86rem
        position: relative
        .back
            display:block
            font-size:0.24rem
            color:#fff
            position: absolute
            top:0
            left:0.30rem
</style>