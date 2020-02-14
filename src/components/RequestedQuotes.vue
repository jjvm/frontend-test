<template>
    <v-row>
        <v-col>
           <FilterQuotes />
            
           <TableQuotes />
            
        </v-col>
    </v-row>
</template>

<script>
import FilterQuotes from './FilterQuotes';

import TableQuotes from './TableQuotes';
  export default {
    components: {
        FilterQuotes,
        TableQuotes

    },
    data () {
      return {
      }
    },
    methods: {
    }
  }
</script>

<style scoped>
    
</style>