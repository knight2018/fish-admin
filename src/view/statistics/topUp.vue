<template>
    <div>
        <statisTile>
             <Table 
             width="98%"
            :columns="columns1" 
            :data="data1">
            </Table>
        </statisTile>
        
    </div>
    
</template>

<script>
import statisTile from "./tempalte/statisTile";
import { topUp } from "./defined.js";
export default {
  name: "basics",
  components: { statisTile },
  data() {
    return {
      columns1: topUp,
      data1: []
    };
  }
};
</script>

<style scoped>
</style>
