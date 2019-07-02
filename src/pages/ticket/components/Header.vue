<template>
    <div>
        <div class="ticket-header border-bottom">
            <router-link tag="div" to="/" class="header-left">
                <div class="iconfont back-icon">&#xe63f;</div>
            </router-link>
            <div class="header-middle">
                <input 
                type="text" 
                class="header-input" 
                placeholder="输入城市或景点" 
                v-model="inputMsg"
                @focus="handleFocusShow"
                @blur="handleBlurShow"/>
                <span 
                class="iconfont delete-icon" 
                v-show="inputMsg"
                @click="hadleClickDelete"> &#xe625; </span>
            </div>
            <div class="header-right" @click="handleClickSeach">搜索</div>
        </div>   
        <div class="show-list" v-show="showFlag&&!inputMsg">
            <div class="history border-bottom" v-show="historySearch.length!=0">
                <div class="history-head">
                    <div class="title">搜索历史</div>
                    <div class="delete-info" @touchstart.prevent="handleTouchDelete">
                        <span class="iconfont delete-icon"> &#xe62e; </span>
                        删除
                    </div>
                </div>
                <div class="history-list border-bottom">
                    <div class="history-item" v-for="(item,index) of historySearch" :key="index">
                        {{item.keyWord}}
                    </div>
                </div>
            </div>
            <div class="no-list" v-show="!inputMsg">搜索身边的景点</div>
            
        </div>
        <div class="search-list" v-show="showFlag&&inputMsg">
            123
        </div>
    </div>
</template>

<script>
export default {
    name:'TicketHeader',
    data:function(){
        return{
            inputMsg:'',
            showFlag:false,
            historySearch:[]
        }
    },
    methods:{
        handleFocusShow(){
            if(this.inputMsg == ''){
                this.showFlag=!this.showFlag
            }
        },
        handleBlurShow(){
            this.showFlag=!this.showFlag
        },
        hadleClickDelete(){
             this.inputMsg=''
             this.showFlag=false
             console.log(this.showFlag)
        },
        handleClickSeach(){
            if(this.inputMsg!==''){
                let storage=window.localStorage   
                if(storage.getItem('searchWord')==null){
                    this.historySearch.unshift({keyWord:this.inputMsg})
                    storage.setItem('searchWord',JSON.stringify(this.historySearch))
                }else{
                    if(!JSON.parse(storage.getItem('searchWord')).find(v => v.keyWord === this.inputMsg)){
                        if( this.historySearch.length >= 6){
                                this.historySearch.pop()                            
                            }
                            this.historySearch.unshift({keyWord:this.inputMsg})
                            storage.setItem('searchWord',JSON.stringify(this.historySearch))
                    }
                }
            }
        },
        handleTouchDelete(){
            window.localStorage.clear()
            this.historySearch=[]
        }
    },
    created(){
        //获取localstorage
        let storage=window.localStorage
        if(storage.getItem('searchWord')!==null){
            this.historySearch=JSON.parse(storage.getItem('searchWord'))
        } 
    },
    computed:{

    }
}

</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.ticket-header
    line-height :$headerHeight
    display:flex
    .header-left
        float :left
        width : .64rem
        .back-icon
            font-size : .4rem
            text-align :center
    .header-middle
        flex : 1
        .header-input
            width :100%
            height :.5rem
            padding : 0 .6rem 0 .2rem
            text-align :center
            font-size: .28rem
            border: .02rem solid #eee
            border-radius : .5rem
            background : #f2f2f2
            box-sizing:border-box
            -moz-box-sizing:border-box; /* Firefox */
            -webkit-box-sizing:border-box; /* Safari */
        .delete-icon
            position :absolute
            top :0
            right :1.24rem
    .header-right
        float :right
        width :.64rem
        font-size:.3rem
        color :#212121
        margin :0 0.2rem
.show-list
    position :absolute
    z-index :2
    left:0
    right :0
    margin-top:.02rem
    background :#fff
    display:flex
    flex-direction:column
    border :.02rem solid #eee
    box-shadow :0 .02rem .06rem .02rem #c7ced4
    .history
        flex:1
        height :.64rem
        line-height :.64rem
        .history-head
            overflow hidden
            background :#f0f5f6
            .title
                float :left
                margin-left:.2rem
                color :#888
            .delete-info
                float :right
                color : #00afc7
                margin-right :.2rem
        .history-list
            overflow hidden
            .history-item
                border: .02rem solid #ccc
                float :left
                padding :0 .1rem
                margin :.1rem
    .no-list
        flex :1
        height :$headerHeight
        line-height :$headerHeight
        border :.02rem solid #eee
        margin : .2rem .6rem
        text-align :center
</style>
