<template>
  <v-app>
    <v-content class="app">
      <v-container fluid>
        <v-row >
          <v-col class="drw-col">
            <DrawerNav/>
          </v-col>
          <v-col>
            <TopNav/>
            <Orders/>
          </v-col>

        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import DrawerNav from './components/DrawerNav';
import TopNav from './components/TopNav';
import Orders from './components/Orders';
export default {
  name: 'App',
  components: {
    DrawerNav,
    TopNav,
    Orders,
  },
};
</script>

<style scoped>
  .drw-col {
    flex-grow:0;
  }
</style>