<template>
    <div :id="uuid" :style="style" :width="width">MyEcharts</div>
</template>

<script>
import * as echarts from 'echarts';
const idGen =() =>{
    return new Date().getTime();
}
export default {
    props:{
        width:{
            type:String,
            default:'600px'
        },
        height:{
            type:String,
            default:'400px'
        },
        options:{
            type:Object,
            default:null
        }
    },
    data(){
        return{
            uuid:null,
            myChart:null,
        }
    },
    watch:{
        width(){
            if(this.myChart){
                this.myChart.resize({
                    animation:{
                        duration:300
                    }
                });
            }
        },
        options(){
            if(this.myChart){
                this.myChart.setOption(this.options,{
                    notMerge:true
                });
            }
        }
    },
    created(){
        this.uuid = idGen();
    },
    computed:{
        style(){
            return{
                width:this.width,
                height:this.height
            }
        }
    },
    mounted(){

        // 基于准备好的dom，初始化echarts实例
        this.myChart = echarts.init(document.getElementById(this.uuid));
        //配置options
        
        // 绘制图表
        this.myChart.setOption(this.options);
        
    },
}
</script>
