<template>
  <div class="order-details">
    <div class="div-details">
        <p>Customer: <b>{{ customer }}</b> <v-icon >mdi-information-outline</v-icon></p> 
        <p>Customer PO: <b>{{ custPO }}</b> | Packform reference: <span style="color:   #593EC2">{{ref}}</span></p> 
    </div>
    <div class="div-table">
        <table class="tst-table">
            <tr class="tbl-title">
                <th colspan="3">Aug 13, 2018 - Aug 13, 2019 <a href="#">(Edit)</a></th>
            </tr>
            <tr>
                <th>Total Spend</th>
                <th>Margin $</th>
                <th>Margin %</th>
            </tr>
            <tr>
                <td>$1,294,000.00</td>
                <td>$107,500.00</td>
                <td class="margin"><span>39.76% </span><span class="icon"><v-icon >mdi-emoticon-outline</v-icon></span></td>
            </tr>
        </table>
    </div>
  </div>
</template>

<script>
export default {

  name: 'OrderDetails',

  data: () => ({
      customer: "Pro Industrial",
      custPO: "Ordering for Christmas Event",
      ref:"#474733"
  }),
};
</script>

<style scoped>
  .order-details {
      padding: 10px;
      display: flex;
  }
  .div-details {
      flex-grow: 6;
      align-self: center;
  }
  .div-table {
      display:flex;
      justify-content: flex-end;
  }
  .tst-table{
      border: 1px solid #E4E4E4;
  }
  .tst-table .tbl-title th{
      background: #F3F3F4;
      padding:10px;
  }
  .tst-table th{
      border-top: 1px solid #E4E4E4;
      border-right: 1px solid #E4E4E4;
      color:#7D7D7D;
  }
  .tst-table td{
      padding:0 20px 10px 20px;
      border-right: 1px solid #E4E4E4;
      font-weight: 800;

  }
  .tst-table .margin span{
      background: #28A745;
      color:white;
      font-weight: 400;
      padding:5px;
  }
  .tst-table .margin .icon{
      background: #218939;
      margin:0 !important;
  }
.tst-table .margin .icon .v-icon {
      color:white;
}
</style>