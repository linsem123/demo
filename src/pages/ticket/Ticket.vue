<template>
    <div>
        <ticket-header></ticket-header>
        <ticket-choose :kindlist="kindlist"></ticket-choose>
    </div>
</template>
<script>
import TicketHeader from './components/Header'
import TicketChoose from './components/Choose'
import axios from 'axios'
export default {
    name:'Ticket',
    data:function(){
        return{
            kindlist:[]
        }
    },
    components:{
        TicketHeader,
        TicketChoose
    },
    methods:{
        getKind(){
            axios.get("/api/kind.json").then(this.getKindSucc)
        },
        getKindSucc(res){
            res=res.data
            if(res.ret&&res.data){
                this.kindlist=res.data
            }
        }
    },
    mounted(){
        this.getKind()
    }
}
</script>
<style lang="stylus">

</style>

