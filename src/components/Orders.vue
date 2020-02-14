<template>
  <v-card>

      <v-row>
        <v-col>
            <OrderDetails />
            <v-tabs
            v-model="tab"
            >
            <v-tab
                v-for="item in items"
                :key="item.tab"
            >
               <v-icon stye="margin-right:5px;">{{item.icon}}</v-icon>  {{ item.tab }}  
            </v-tab>
            </v-tabs>

            <v-tabs-items v-model="tab">
                <v-tab-item
                    v-for="item in items"
                    :key="item.tab"
                >
                    <v-card flat>
                    <v-card-text v-if="item.tab !== 'Purchasing'">{{ item.content }}</v-card-text>
                    <div v-else>
                        <v-tabs v-model="tab2">
                            <v-tab
                                v-for="item2 in items2"
                                :key="item2.tab"
                            >
                            {{ item2.tab }}  
                            </v-tab>
                        </v-tabs>
                        <v-tabs-items v-model="tab2">
                            <v-tab-item
                                v-for="item2 in items2"
                                :key="item2.tab"
                            >
                            <v-card flat>
                                <v-card-text v-if="item2.tab !== 'Requested quotes'">{{ item2.content }}</v-card-text>
                                <RequestedQuotes v-else/>
                            </v-card>
                            </v-tab-item>
                        </v-tabs-items>
                    </div>
                    </v-card>
                </v-tab-item>
            </v-tabs-items>
        </v-col>
      </v-row>
      <v-row >
          <v-col style="
            padding-bottom: 0!important;">
      <Footer/>
          </v-col>
      </v-row>
  </v-card>
</template>

<script>
import OrderDetails from './OrderDetails';

import RequestedQuotes from './RequestedQuotes';

import Footer from './Footer';
export default {

  name: 'Orders',
  components: {
      OrderDetails,
      RequestedQuotes,
     Footer

  },

  data: () => ({
      tab: null,
      tab2: null,
      items: [
          { tab: 'Overview', content: 'Tab 1 Content', icon: "mdi-eye-outline" },
          { tab: 'Product', content: 'Tab 2 Content', icon: "mdi-inbox" },
          { tab: 'Purchasing', content: 'Tab 3 Content', icon: "mdi-hand-heart"  },
          { tab: 'Schedule', content: 'Tab 4 Content', icon: "mdi-calendar"  },
          { tab: 'Messages', content: 'Tab 5 Content', icon: "mdi-android-messages"  },
        ],
      items2: [
          { tab: 'New Quote Request', content: 'Tab 1 Content' },
          { tab: 'Requested quotes', content: 'Tab 2 Content' },
          { tab: 'Accepted quotes', content: 'Tab 3 Content'  },
        ],
  }),
};
</script>

<style scoped>
  .v-tabs .v-tab--active  {
      color: #593EC2 !important;
      caret-color: red !important;
  }
</style>