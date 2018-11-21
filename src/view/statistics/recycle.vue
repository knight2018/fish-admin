<template>
    <div>
        <span class="mg-lf">游戏选择：</span>
        <Select v-model="model1" style="width:100px">
            <Option v-for="item in gameList" :value="item.value" :key="item.value">{{item.value}}</Option>
        </Select>
        <span class="mg-lf">活动选择：</span>
        <Select v-model="model2" style="width:150px">
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
        <Button type="primary" style="margin-left:10px">查询</Button>
        <Table 
         :columns="columns" 
         :data="data">
         </Table>
         <Page :total="total" on-change="handlePage"></Page>
    </div>
</template>

<script>
import {recycle} from './defined.js'
export default {
        data (){
            return {
                model1: '全服',
                model2: '7天登陆活动',
                columns: recycle,
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
                        value: '7天登陆活动',
                        label: '7天登陆活动'
                    },
                    {
                        value: '登陆抽奖',
                        label: '登陆抽奖'
                    },
                    {
                        value: '解锁炮台',
                        label: '解锁炮台'
                    },
                    {
                        value: '每日任务',
                        label: '每日任务'
                    },
                    {
                        value: '新手任务',
                        label: '新手任务'
                    },
                    {
                        value: '微信礼包',
                        label: '微信礼包'
                    },
                    {
                        value: '兑换码',
                        label: '兑换码'
                    }
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

        }
    }
}
</script>

<style scoped>
    .mg-lf{
        margin-left: 10px;
    }
</style>
