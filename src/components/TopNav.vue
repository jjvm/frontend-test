<template>
        <v-toolbar>
        <v-btn class="ma-2 tst-primary" tile outlined small>
            <v-icon left>mdi-arrow-left</v-icon> Back to list
        </v-btn>
        <v-btn class="ma-2 tst-active" tile outlined small>
            <v-icon left>mdi-repeat</v-icon> Quick Switch
        </v-btn>
  
        <v-spacer></v-spacer>
        
        <v-btn icon>
          <v-icon>mdi-bell-outline</v-icon>
        </v-btn>
  
        <v-btn class="ma-2 tst-fab" fab small>
            AG
        </v-btn>
         <v-btn class="ma-2 tst-info" text small>
            <span><b>Alex Grady</b> <br> Packform LLC</span>  <v-icon right>mdi-chevron-down</v-icon>
        </v-btn>
  
      </v-toolbar>
</template>

<script>
  export default {
    data () {
      return {
      }
    },
    methods: {
    }
  }
</script>

<style scoped>
    .top-nav {
        padding-left:20px;
    }
    .tst-info {
        
        text-transform: none;
    }
    /* buttons */
    .tst-primary {
        text-transform: none;
        color: #333333;
        font-weight: 700;
        font-size: 16px;
        background: #E4E4E4;
        border:none;
    }
    .tst-active {
        text-transform: none;
        color:#ffffff !important;
        font-weight: 700;
        font-size: 16px;
        background: #007BFF;
        border:none;
    }
    .tst-fab {
        
        text-transform: none;
        color:#ffffff !important;
        font-weight: 700;
        font-size: 16px;
        background: #007BFF !important;
        box-shadow: none !important; 
    }
</style>