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
        <span class="mg-lf" >货币：</span>
        <Select v-model="model3" style="width:100px" >
            <Option v-for="item in cycleList" :value="item.value" :key="item.value">{{item.value}}</Option>
        </Select>
        <Button type="primary" style="margin-left:10px">查询</Button>
        <div v-if="off=='钻石'">
        <Table 
            :columns="columns" 
            :data="data">
            </Table>
            <Page :total="total" on-change="handlePage"></Page>
         </div>
         <div v-if="off=='金币'">
            <Table 
            :columns="columnsW" 
            :data="dataW">
            </Table>
            <Page :total="totalW" on-change="handlePageW"></Page>
        </div>
    </div>
</template>

<script>
import {currency} from './defined.js'
import {currencyW} from './defined.js'
export default {
        data (){
            return {
                model1: '全服',
                model2: '全渠道',
                model3: '金币',
                off: '金币',
                columns: currency,
                data: [],
                columnsW: currencyW,
                dataW:[],
                total: 0,
                totalW: 0,
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
                        value: '金币',
                        lable: '金币'
                    },
                    {
                        value: '钻石',
                        lable: '钻石'
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
        handlePageW (index){

        }
    }
}
</script>

<style scoped>
    .mg-lf{
        margin-left: 10px;
    }
</style>
