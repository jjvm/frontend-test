<template>
  <v-card class="drawer" style="background:red;"
  >
    <v-card
      width="256"
    >
      <v-navigation-drawer
        permanent
      >
        <v-list-item>
            <v-list-item-avatar>
                <v-img :src="require('../assets/logo.png')"></v-img>
            </v-list-item-avatar>
        </v-list-item>
        <v-list shaped>
            <v-list-item 
                v-on:click="nav">
                <v-list-item-content>
                    <v-list-item-title v-text="items[0].title"></v-list-item-title>
                </v-list-item-content>
            </v-list-item>
            <v-list-group
            v-for="item in items"
            v-show="item.title !== 'Dashboard'"
            :key="item.title"
            v-model="item.active"
            v-bind:class="{isActive: item.active}"
            no-action
            >
            <template v-slot:activator >
                <v-list-item-content >
                    <v-list-item-title class="nav-title" v-text="item.title" ></v-list-item-title>
                </v-list-item-content>
            </template>
            <v-list-item 
                
                v-for="subItem in item.items"
                v-on:click="nav"
                :key="subItem.title"
            >
                <v-list-item-content>
                    <v-list-item-title v-text="subItem.title"></v-list-item-title>
                </v-list-item-content>
            </v-list-item>
            </v-list-group>
        </v-list>
      </v-navigation-drawer>
    </v-card>
  </v-card>
</template>

<script>
  export default {
    data () {
      return {
        items: [
            {
                title: 'Dashboard',
            },
            {
            title: 'Customers',
            active: true,
            items: [
                { title: 'Orders',
                 active: true, 
                },
                { title: 'Companies' },
                { title: 'Users' },
                { title: 'Price Lists' },
            ],
            },
            {
            title: 'Suppliers',
            items: [
                { title: 'Supplier' },
            ],
            },
            {
            title: 'Catalog',
            items: [
                { title: 'See Catalogs' },
            ],
            }
        ],
      }
    },
    methods: {
        nav: function () {
            console.log('nothing')
        }
    }
  }
</script>

<style scoped>
    .v-card  {
      -webkit-box-shadow: none !important;
      box-shadow: none !important;
      border: none!important;
    }
    .v-navigation-drawer {
        background: #F3F3F4;
    }
    .v-list-item__title {
        
        padding-left: 10px;
        font-size: 16px;
        color: #7D7D7D !important;
    }
    .v-avatar {
        min-width:214px;
        width:214px !important;
        height: 40px;
        border-radius: 0;
    }
    .isActive .nav-title
     {
        color: black;
        font-weight: 700;
        border-left: 3px solid #593EC2;
        padding-left: 10px;
    }
</style>