<template>
    <div>
        <statisTile :cycle="cycle">
            <Table 
            :columns="columns" 
            :data="data">
            </Table>
        </statisTile>
        
    </div>    
</template>

<script>
import statisTile from "./tempalte/statisTile";
import {keep} from './defined.js'
export default {
    name: 'keep',
    components: {statisTile},
    data (){
        return {
            cycle: false,
            columns: keep,
            data: []
        }
    }
}
</script>

<style>

</style>
