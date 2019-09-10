<template>
    <div class="list">
        <div class="item" v-for="item of letters" :key="item" @click="alpClick" @touchstart="handleTouchStart" @touchmove="handleTouchMove" @touchend="handleTouchEnd" :ref='item'>{{item}}</div>
    </div>
</template>

<script type="text/javascript">
    export default {
        name:"CityAlphabet",
        props:{
            cities: Object
        },
        computed:{
            letters(){
                const letters = [];
                for (let i in this.cities){
                    letters.push(i)
                }
                return letters
            }
        },
        data(){
            return{
                touchStatus:false,
                startY : 0,
                timer:null
            }
        },
        undated(){
            this.startY = this.$refs["A"][0].offsetTop
        },
        methods:{
            alpClick (e){
                this.$emit('change', e.target.innerText);
            },
            handleTouchStart(){
                this.touchStatus=true
            },
            handleTouchMove(e){
                if(this.touchStatus){
                   if(this.timer){
                    clearTimeout(this.timer)
                   }
                   this.timer = setTimeout(() => {
                       const touchY = e.touches[0].clientY -79
                        const index = Math.floor((touchY-this.startY)/20)
                        if(index>= 0 && index<this.letters.length){
                            this.$emit('change' , this.letters[index])
                        } 
                    },16)   
                }
            },
            handleTouchEnd(){
                this.touchStatus=false
            }
        }
    }
</script>

<style lang="stylus" scoped>
    @import '~sty/varibles.styl'
    .list
        position: absolute
        display:flex
        flex-direction:column
        justify-content:center
        width:0.40rem
        text-align:center
        top:1.58rem
        right:0
        bottom:0
        .item
            font-size:0.24rem
            color:$bgColor
            line-height:0.4rem
</style>