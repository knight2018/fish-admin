<template>
    <div>
        <span class="mg-lf">游戏选择：</span>
        <Select v-model="model1" style="width:100px">
            <Option v-for="item in gameList" :value="item.value" :key="item.value">{{item.value}}</Option>
        </Select>
        <span class="mg-lf">房间选择：</span>
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
        <Button type="primary" style="margin-left:10px">查询</Button>
        <Table 
         :columns="columns" 
         :data="data">
         </Table>
         <Page :total="total" on-change="handlePage"></Page>
    </div>
</template>

<script>
import {gameRoom} from '../defined.js'
export default {
        data (){
            return {
                model1: '全服',
                model2: '全部',
                columns: gameRoom,
                data: [
                    {
                        number: 1
                    }
                ],
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
                        value: '初级房',
                        label: '初级房'
                    },
                    {
                        value: '高级房',
                        label: '高级房'
                    },
                    {
                        value: '全部',
                        lable: '全部'
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
            
        },

    }
}
</script>

<style scoped>
    .mg-lf{
        margin-left: 10px;
    }
</style>
