<template>
    <div>
        <div>
            <span class="mg-lf">游戏选择：</span>
            <Select v-model="model1" style="width:100px">
                <Option v-for="item in gameList" :value="item.value" :key="item.value">{{item.value}}</Option>
            </Select>
            <span class="mg-lf" v-if="channel">渠道选择：</span>
            <Select v-model="model2" style="width:100px" v-if="channel">
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
            <span class="mg-lf" v-if="cycle">周期选择：</span>
            <Select v-model="model3" style="width:100px" v-if="cycle">
                <Option v-for="item in cycleList" :value="item.value" :key="item.value">{{item.value}}</Option>
            </Select>
            <Button type="primary" style="margin-left:10px" >查询</Button>
        </div>
        <slot></slot>
        <div>
            <Page :total="total" on-change="handlePage" @click.native="handleSearch"></Page>
        </div>
    </div>
</template>

<script>
export default {
    name: 'statisTile',
    props:{
        cycle:{
            type: Boolean,
            default: true
        },
        channel:{
            type: Boolean,
            default: true
        }
    },
    data (){
        return {
            model1: '全服',
            model2: '全渠道',
            model3: '日',
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
                    value: '日',
                    lable: '日'
                },
                {
                    value: '月',
                    lable: '月'
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
            console.log(date);
        },
        handlePage (index){
            console.log(index);
        },
        handleSearch (){
            console.log()
        }
    }
}
</script>

<style scoped>
    .mg-lf{
        margin-left: 10px;
    }
</style>
