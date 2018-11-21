<template>
    <div>
        <span class="mg-lf">用户账号：</span>
        <Input v-model="value" placeholder="请输入用户账号" style="width:200px"></Input>
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
import {define} from '../defined.js'
export default {
        data (){
            return {
                columns: define,
                data: [
                    {
                        number: 1
                    }
                ],
                total: 0,
                value: undefined,
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
