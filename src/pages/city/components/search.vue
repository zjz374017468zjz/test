<template>
    <div>
        <div class="search">
             <input type="text" v-model="keyword"  placeholder="请选择城市名或拼音" class="searchInput" />
        </div>
        <div class="searchContent" v-show="keyword" ref = "searBox">
            <ul>
                <li class="searchItem border-bottom" v-for ="item of list" :key="item.id" @click="handleCityClick(item.name)">{{item.name}}</li>
                <li class="searchItem border-bottom" v-show="hasNoData">没有找到匹配数据</li>
            </ul>
        </div>
    </div>
</template>

<script type="text/javascript">
import Bscroll from 'better-scroll'
    export default {
        name:"CitySearch",
        props: {
            cities :Object
        },
        data(){
            return{
                keyword:'',
                list:[],
                timer:null
            }
        },
        methods:{
            handleCityClick(city){
                this.$store.commit('changeCity', city)
                this.$router.push('/')
            }
        },
        computed:{
            hasNoData(){
                return !this.list.length
            }
        },
        watch:{
            keyword(){
                if(this.timer){
                    clearTimeout(this.timer)
                }
                if(!this.keyword){
                    this.list=[]
                    return
                }
                this.timer = setTimeout(()=>{
                    const result = []
                    for(let i in this.cities){
                        this.cities[i].forEach((value)=>{
                            if(value.spell.indexOf(this.keyword)>-1 || value.name.indexOf(this.keyword) > -1){
                                result.push(value)
                            }
                        })
                    }
                    this.list= result;
                },100)
            }
        },
        mounted(){
            this.scroll = new Bscroll(this.$refs.searBox)
        }
    }
</script>

<style lang="stylus" scoped>
    @import '~sty/varibles.styl'
    .search
        height:0.72rem
        background:$bgColor
        padding:0 0.1rem
        .searchInput
            width:100%
            height:0.62rem
            line-height: 0.62;
            background:#fff
            border-radius:0.06rem
            font-size:0.28rem
            text-align:center
            color:#999
            display: block
            padding:0 0.10rem
    .searchContent
        overflow: hidden
        position: absolute
        top:1.58rem
        left:0
        right:0
        bottom:0
        background:#eee
        z-index:2
        .searchItem
            line-height:0.62rem
            padding-left:0.20rem
            background:#fff;
            color:#666;
            
            
</style>