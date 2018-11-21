<template>
    <div>
        <statisTile :cycle="cycle" :channel="false">
            <div>
                <div ref="dom" style="width:88%;height:500px;"></div>
                <Table 
                :columns="columns1" 
                :data="data1">
                </Table>
            </div>
        </statisTile>
        
    </div>
    
</template>

<script>
import echarts from 'echarts'
import statisTile from "./tempalte/statisTile";
import {online} from './defined.js'
export default {
    components:{statisTile},
    data (){
        return {
            columns1:online,
            data1: [],
            cycle: false,
            options :{
                title: {
                    text: '在线在玩'
                },
                tooltip: {
                    trigger: 'axis'
                },
                legend: {
                    data:['邮件营销','联盟广告','视频广告','直接访问','搜索引擎']
                },
                grid: {
                    left: '3%',
                    right: '4%',
                    bottom: '3%',
                    containLabel: true
                },
                toolbox: {
                    feature: {
                        saveAsImage: {}
                    }
                },
                xAxis: {
                    type: 'category',
                    boundaryGap: false,
                    data: ['周一','周二','周三','周四','周五','周六','周日']
                },
                yAxis: {
                    type: 'value'
                },
                series: [
                    {
                        name:'邮件营销',
                        type:'line',
                        stack: '总量',
                        data:[120, 132, 101, 134, 90, 230, 210]
                    },
                    {
                        name:'联盟广告',
                        type:'line',
                        stack: '总量',
                        data:[220, 182, 191, 234, 290, 330, 310]
                    },
                    {
                        name:'视频广告',
                        type:'line',
                        stack: '总量',
                        data:[150, 232, 201, 154, 190, 330, 410]
                    },
                    {
                        name:'直接访问',
                        type:'line',
                        stack: '总量',
                        data:[320, 332, 301, 334, 390, 330, 320]
                    },
                    {
                        name:'搜索引擎',
                        type:'line',
                        stack: '总量',
                        data:[820, 932, 901, 934, 1290, 1330, 1320]
                    }
                ]
            }
        }
    },
    methods: {
        resize () {
            let dom = this.$refs.dom;
            this.dom = echarts.init(dom);
        },
        drawEcharts (){
            this.dom.setOption(this.options);
        }
    },
    mounted (){
        this.resize();
        this.drawEcharts();
        console.log(this.$refs.dom)
    }
}
</script>

<style scoped>

</style>
