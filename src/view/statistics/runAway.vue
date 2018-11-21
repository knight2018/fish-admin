<template>
    <div>
        <statisTile :cycle="cycle">
            <Table 
            :columns="columns1" 
            :data="data1">
            </Table>
        </statisTile>
         
    </div>
    
</template>

<script>
import statisTile from "./tempalte/statisTile";
import {runAway} from './defined.js'
export default {
    components:{statisTile},
    data (){
        return {
            columns1:runAway,
            data1: [],
            cycle: false
        }
    }
}
</script>

<style scoped>

</style>
