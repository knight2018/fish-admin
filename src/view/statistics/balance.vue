<template>
        <statisTile :cycle="cycle">
            <Table 
            :columns="columns" 
            :data="data">
            </Table>
        </statisTile>
</template>

<script>
import statisTile from "./tempalte/statisTile";
import {balance} from './defined.js'
export default {
    components: {statisTile},
    data (){
        return {
            cycle: false,
            columns: balance,
            data: [
                {
                    number: '1'
                },
                {
                    number: '1000'
                }
            ]
        }
    }
}
</script>

<style>

</style>