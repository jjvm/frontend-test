<template>
     <v-toolbar flat>
        <v-btn rounded class="ma-2 tst-active" outlined small >
            <v-icon left>mdi-hammer-wrench</v-icon> By Supplier
        </v-btn>
        <v-btn rounded class="ma-2 tst-primary" outlined small>
            <v-icon left>mdi-table</v-icon> By Product
        </v-btn>
        <v-spacer></v-spacer>
        <v-btn class="ma-2 tst-plan" tile outlined small>
            <v-icon left>mdi-flashlight</v-icon> Hexie smart combo plan
        </v-btn>
    </v-toolbar>
</template>

<script>
export default {
    
}
</script>


<style scoped>
   .tst-active {
        text-transform: none;
        color:#ffffff !important;
        font-size: 16px;
        background: #007BFF;
        border:none;
    }
    .tst-primary {
        text-transform: none;
        color: #333333;
        font-size: 16px;
        background: #F3F3F4;
        border:none;
    }
    .tst-plan {
        text-transform: none;
        color: #ffffff;
        font-weight: 700;
        font-size: 17px;
        background: #593EC2;
        border:none;
    }
</style>