<template>
    <div>
        <span class="mg-lf">游戏选择：</span>
        <Select v-model="model1" style="width:100px">
            <Option v-for="item in gameList" :value="item.value" :key="item.value">{{item.value}}</Option>
        </Select>
        <span class="mg-lf">渠道选择：</span>
        <Select v-model="model2" style="width:100px">
            <Option v-for="item in channelList" :value="item.value" :key="item.value">{{item.value}}</Option>
        </Select>
        <span class="mg-lf">日期选择：</span>
        <DatePicker type="daterange" 
            placement="bottom-start" 
            placeholder="Select date" 
            style="width: 200px; "
            :options="options1"
            @on-change="handleDate">
        </DatePicker>
        <span class="mg-lf" >场景选择：</span>
        <Select v-model="model3" style="width:100px" >
            <Option v-for="item in cycleList" :value="item.value" :key="item.value">{{item.value}}</Option>
        </Select>
        <Button type="primary" style="margin-left:10px" @click="handleSearch">查询</Button>
        <Table 
         :columns="columns" 
         :data="data">
         </Table>
         <Page :total="total" on-change="handlePage"></Page>
    </div>
</template>

<script>
import {payScene} from './defined.js'
export default {
        data (){
            return {
                model1: '全服',
                model2: '全渠道',
                model3: '全部',
                columns: payScene,
                data: [],
                total: 0,
                gameList: [
                    {
                        value: '捕鱼',
                        label: '捕鱼'
                    },
                    {
                        value: '斗地主',
                        label: '斗地主'
                    },
                    {
                        value: '全服',
                        lable: '全服'
                    }
                ],
                channelList: [
                    {
                        value: 'oppo',
                        label: 'oppo'
                    },
                    {
                        value: '全渠道',
                        label: '全渠道'
                    }
                ],
                cycleList: [
                    {
                        value: '月卡',
                        lable: '月卡'
                    },
                    {
                        value: '首冲',
                        lable: '首冲'
                    },
                    {
                        value: '商城',
                        lable: '商城'
                    },
                    {
                        value: '破产提示',
                        lable: '破产提示'
                    },
                    {
                        value: '大厅',
                        lable: '大厅'
                    },
                    {
                        value: '战斗',
                        lable: '战斗'
                    },
                    {
                        value: 'vip',
                        lable: 'vip'
                    },
                    {
                        value: '全部',
                        lable: '全部'
                    },
                ],
                options1: {
                    disabledDate (date) {
                        return date&&date.valueOf()>=Date.now();
                    },
                    shortcuts :[
                        {
                            text : '今天',
                            value () {
                                const start = new Date();
                                const end = new Date();
                                return [start,end]
                            }
                        },
                        {
                            text : '昨天',
                            value () {
                                const start = new Date();
                                const end = new Date();
                                start.setTime(start.getTime()-3600*1000*24)
                                return [start,end]
                            }
                        },
                        {
                            text : '近7日',
                            value () {
                                const start = new Date();
                                const end = new Date();
                                start.setTime(start.getTime()-3600*1000*24*7)
                                return [start,end]
                            }
                        },
                        {
                            text : '近30日',
                            value () {
                                const start = new Date();
                                const end = new Date();
                                start.setTime(start.getTime()-3600*1000*24*30)
                                return [start,end]
                            }
                        }
                    ]
                },
            }
    },
    methods: {
        handleDate (date){

        },
        handlePage (index){
            
        },
        handleSearch (){
            
        }
    }
}
</script>

<style scoped>
    .mg-lf{
        margin-left: 10px;
    }
</style>
