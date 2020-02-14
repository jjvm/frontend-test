<template>
    <div  style="padding:20px;!important">
        <v-card  v-for="item in suppliers"
                    :key="item.tab">
            <table class="tbl-quotes">
                
                <tr class="first-row">
                    <th colspan="4" style="text-align:start;"><v-icon>mdi-chevron-down</v-icon>Quote from <b>{{item.supplierName}}</b> <span class="accredited" v-if="item.accredited"><v-btn rounded x-small><v-icon  x-small>mdi-star</v-icon> Accredited</v-btn></span></th>
                    <th colspan="2">Status<br><v-icon left style="color:#007BFF">mdi-checkbox-blank-circle</v-icon> {{item.status}}</th>
                    <th>Date sent<br> {{item.sent}}</th>
                    <th>Date Received<br> {{item.received}}</th>
                </tr>
                
                <tr>
                    <th>Products</th>
                    <th>Quantity</th>
                    <th class="buy">Buy/Unit</th>
                    <th class="buy">Buy total</th>
                    <th class="sell">Sell/Unit</th>
                    <th class="sell">Sell total</th>
                    <th>Margin $</th>
                    <th>Margin %</th>
                </tr>
                <tbody 
                v-for="product in item.products" :key="product.productId">
                    <tr>
                        <td class="product">
                            <v-img src="https://picsum.photos/510/300?random" max-height="30" max-width="40"></v-img>
                            <div style="width:100%;">
                                <span class="product-id">{{product.productId}}</span> <br>
                                <span class='product-name'>{{product.name}}</span> <br>
                                <span class="category">Category: {{product.category}}</span>
                            </div>
                        </td>
                        <td>{{ product.quantity }}</td>
                        <td v-if="!product.buy">---</td>
                        <td v-else class="buy">${{(product.buy).toLocaleString().replace(/,/g,",",)}}</td>

                        <td v-if="!product.buy">---</td>
                        <td v-else class="buy">${{(product.quantity * product.buy).toLocaleString().replace(/,/g,",",)}}</td>

                        <td v-if="!product.sell">---</td>
                        <td v-else class="sell">${{(product.sell).toLocaleString().replace(/,/g,",",)}}</td>

                        <td v-if="!product.sell">---</td>
                        <td v-else class="sell">${{(product.quantity * product.sell).toLocaleString().replace(/,/g,",",)}}</td>
                        <td v-if="!product.margin">---</td>
                        <td v-else>+ ${{(product.margin).toLocaleString().replace(/,/g,",",)}}</td>
                        <td v-if="!product.margin">---</td>
                        <td v-else class="margin"><span>{{product.marginPercent}}% </span><span class="icon"><v-icon >mdi-emoticon-outline</v-icon></span></td>
                    </tr>
                    <tr v-if="product.availability !== ''">
                        <td colspan="2"></td>
                        <td colspan="2" class="availability">Availability: {{product.availability}}</td>
                        <td colspan="2" class="best-quote">Last best quote: <b><u>${{product.bestQuote}}</u></b></td>
                    </tr>
                </tbody>
                <tr class="table-actions">
                    <th colspan="3">Actions</th>
                    <th>Quote Reference</th>
                    <th>Buy total amount</th>
                    <th>Sell total amount</th>
                    <th>Margin $</th>
                    <th>Margin %</th>
                </tr>
                <tr>
                    <td  colspan="3" >
                        <v-btn class="ma-2 tst-active" tile outlined small>
                            <v-icon left>mdi-eye</v-icon> View Qoute
                        </v-btn>
                        <v-btn class="ma-2 tst-primary" tile outlined small>
                            <v-icon left>mdi-cash-100</v-icon> Provide as supplier
                        </v-btn>
                        
                        <v-btn class="ma-2 tst-danger" tile outlined small>
                            <v-icon left>mdi-cancel</v-icon> Cancel
                        </v-btn>
                    </td>
                    <td>{{item.reference}}</td>
                    <td>${{Object.values(item.products).reduce((a, b) => a + (b.buy * b.quantity), 0).toLocaleString().replace(/,/g,",",)}}</td>
                    <td>${{Object.values(item.products).reduce((a, b) => a + (b.sell * b.quantity), 0).toLocaleString().replace(/,/g,",",)}}</td>
                    <td>${{Object.values(item.products).reduce((a, b) => a + b.margin, 0).toLocaleString().replace(/,/g,",",)}}</td>
                    <td>{{(Object.values(item.products).reduce((a, b) => a + b.marginPercent, 0) / (item.products.length - 1)).toFixed(2).toLocaleString().replace(/,/g,",",)}}%</td>
                </tr>
            </table>
        </v-card>
    </div>
</template>

<script>
export default {
     data: () => ({
      suppliers: [
          { 
            supplierName: 'Honest Buildings', 
            accredited: true,
            status: "Received quote",
            sent: "Jul 14, 5:45 AM",
            received: "Jul 17, 11:30 PM",
            reference: "#474733-1",
            products: [
                {
                    productId:"H-2734",
                    name: "Portable Folding Safety Barrier with Casters",
                    img: "",
                    category: "Safety Guards / Barriers",
                    availability: "In stock",
                    quantity: 50,
                    buy: 117.00,
                    sell: 249.00,
                    bestQuote: 150,
                    margin: 6600.00,
                    marginPercent: 53.01
                },
                {
                    productId:"H-5927",
                    name: "4 Drawer/1 Leg Pedestal Workbench - 60 x 30\", Maple Top",
                    img: "",
                    category: "Workbenches",
                    availability: "In stock",
                    quantity: 120,
                    buy: 410.00,
                    sell: 590.00,
                    bestQuote: 550,
                    margin: 21600.00,
                    marginPercent: 30.51
                },
                {
                    productId:"S-2789",
                    name: "Uline Economy Tape - 2.5 Mil, 2\" x 110 yds, Clear",
                    img: "",
                    category: "Carton Selling Tape",
                    availability: "8 days",
                    quantity: 1000,
                    buy: 1.75,
                    sell: 2.50,
                    bestQuote: 1.75,
                    margin: 750.00,
                    marginPercent: 30
                },
                {
                    productId:"Shipping/Fuel",
                    name: "Shipping Cost",
                    img: "",
                    category: "",
                    availability: "",
                    quantity: 1,
                    buy: 0,
                    sell: 0,
                    bestQuote: 0,
                    margin: 0,
                    marginPercent: 0
                },
            ]
          },
          { 
            supplierName: 'Ritchie and Sons', 
            accredited: true,
            status: "Received quote",
            sent: "Jul 14, 5:45 AM",
            received: "Jul 17, 11:30 PM",
            reference: "#474733-2",
            products: [
                {
                    productId:"H-4791",
                    name: "Portable Floor Fan - 12\"",
                    img: "",
                    category: "Fans, Heaters",
                    availability: "In stock",
                    quantity: 700,
                    buy: 73.00,
                    sell: 88.00,
                    bestQuote: 74.00,
                    margin: 10500.00,
                    marginPercent: 17.05
                },
                {
                    productId:"Shipping/Fuel",
                    name: "Shipping Cost",
                    img: "",
                    category: "",
                    availability: "",
                    quantity: 1,
                    buy: 0,
                    sell: 0,
                    bestQuote: 0,
                    margin: 0,
                    marginPercent: 0
                },
            ]
          },          
          { 
            supplierName: 'Bastion Packaging', 
            accredited: false,
            status: "Received quote",
            sent: "Jul 14, 5:45 AM",
            received: "Jul 17, 11:30 PM",
            reference: "#474733-3",
            products: [
                {
                    productId:"H-4791",
                    name: "Manual Time Clock",
                    img: "",
                    category: "Time/Wall Clocks",
                    availability: "In stock",
                    quantity: 50,
                    buy: 270.00,
                    sell: 359.00,
                    bestQuote: 74.00,
                    margin: 4450.00,
                    marginPercent: 24.79
                },
                {
                    productId:"Shipping/Fuel",
                    name: "Shipping Cost",
                    img: "",
                    category: "",
                    availability: "",
                    quantity: 1,
                    buy: 0,
                    sell: 0,
                    bestQuote: 0,
                    margin: 0,
                    marginPercent: 0
                },
            ]
          },
        ],
  }),
}
</script>


<style scoped>
    .tbl-quotes {
        width:100%;
    }
    .tbl-quotes th{
        padding:20px;
        font-weight: 400;
    }
    
    .tbl-quotes td{
        text-align: center;
        padding:20px;
    }
    .tbl-quotes .first-row th {
        color: #7D7D7D;
        font-weight: 400;
        border-top: 1px solid #E4E4E4;
        border-bottom: 1px solid #E4E4E4;
    }
    .product {
        display:flex;
        justify-content: flex-start;
        flex-direction: row;
    }
    .product img {
        margin-right: 10px;
    }
    .product-id {
        width: 100%;;
        text-align: start;

    }
    .product-name {
        font-size:14px;
    }
    .product-id {
        color:#7D7D7D;
        border:1px solid #7D7D7D;
        border-radius: 20px;
        padding:5px;
    }
    .accredited button{
        background: #593EC2!important;
        color:white;
        
    }
    .buy {
        border: 1px solid #FFF6EB !important;
        background: #FFF6EB;
    }
    td.buy {
        font-weight: 800;
    }
    .sell {
        border: 1px solid #E7F3FF !important;
        background: #E7F3FF;
    }
    td.sell {
        font-weight: 800;
    }
    .availability {
        text-align: start !important;
        padding:0 0 0 10px !important;
        margin:0 !important;
        background: #FFC107;
    }
    .best-quote {
        text-align: start !important;
        padding:0 0 0 10px !important;
        margin:0 !important;
    }
       .margin span{
      background: #28A745;
      color:white;
      font-weight: 400;
      padding:5px;
  }
   .margin .icon{
      background: #218939;
      margin:0 !important;
  }
 .margin .icon .v-icon {
      color:white;
}
.table-actions {
    border: 1px solid #E4E4E4;
}
.table-actions th{
    background: #F3F3F4;
}

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
      .tst-danger {
        text-transform: none;
        color:red !important;
        font-weight: 700;
        font-size: 16px;
        border:1px solid red;
    }
</style>