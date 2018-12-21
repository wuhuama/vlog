<template>
    <div class="page1">
        <fieldset>
            <legend>组件1</legend>
            <p><span>单价：</span><span>{{price}}</span> <button @click="downPrice">降价1元</button></p>
            <p>数量: {{count}} </p>
            <button @click="toPage2Data">点击传给组件二</button>

            <div class="from2">{{msg}}</div>
        </fieldset>
        
    </div>
</template>
<script>
// 引入公共的bug，来做为中间传达的工具
import bus from  '../eventBus.js'
export default {
    props:{
        price:{
            type:String,
            default:''
        },
    },
    data(){
        return{
            msg: '',
            count:10
        }
    },
    mounted () {
        // 用$on事件来接收参数
        bus.$on('sendPage1Data', (data) => {
            this.msg = data;
            console.info(data)
        })
    },
    methods:{
        downPrice(){
            this.$emit('downPricea')
        },
        toPage2Data () {
            bus.$emit('sendPage2Data','我是组件一的数据')
        }
    },
    watch:{
       price(newPrice){
          bus.$emit('priceChange',newPrice,this.count) 
       } 
    }
}
</script>
<style scoped>
fieldset{
    border-color: red;
}
.from2{color:blue}
</style>
