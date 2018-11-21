<template>
    <div>
        <statisTile :cycle="cycle" :channel="false">
            <Table 
            :columns="columns1" 
            :data="data1">
            </Table>
        </statisTile>
         
    </div>
    
</template>

<script>
import statisTile from "./tempalte/statisTile";
import {gameTax} from './defined.js'
export default {
    components:{statisTile},
    data (){
        return {
            columns1:gameTax,
            data1: [
                {
                    number: '1'
                }
            ],
            cycle: false
        }
    }
}
</script>

<style scoped>

</style>
