<template>
    <div>
        <statisTile>
            <Table 
            :columns="columns1" 
            :data="data1">
            </Table>
        </statisTile>
         
    </div>
    
</template>

<script>
import statisTile from "./tempalte/statisTile";
import {basics} from './defined.js'
export default {
    name: 'basics',
    components:{statisTile},
    data (){
        return {
            columns1:basics,
            data1: []
        }
    }
}
</script>

<style scoped>

</style>
