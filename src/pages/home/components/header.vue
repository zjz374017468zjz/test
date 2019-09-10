<template>
    <div class="header">
        <div class="header_left">back</div>
        <div class="header_input">搜索</div>
        
        <div class="header_right"><router-link to="/city">{{this.$store.state.city}}</router-link></div>
        
    </div>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style lang="stylus" scoped>
    @import '~sty/varibles.styl'
    .header
        height:0.86rem
        background:$bgColor
        display:flex
        color:#fff;
        .header_left
            float:left
            font-size:0.20rem
            color:#fff
            width:10%
            text-align:center
            line-height:0.86rem
        .header_input
            flex:1
            background:#fff
            border-radius:0.10rem
            height:0.62rem
            line-height:0.62rem
            color:#999
            padding-left:0.20rem
            margin-top:0.12rem
        .header_right
            float:right
            font-size:0.20rem
            color:#fff
            min-width:10%
            text-align:center
            padding:0 0.10rem
            line-height:0.86rem
            
            
</style>
