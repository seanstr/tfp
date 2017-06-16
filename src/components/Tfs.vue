<template>
  <q-layout>
    <!-- Header -->
    <div slot="header" class="toolbar">
      <q-toolbar-title :padding="1">
        Tracy Fine Products
      </q-toolbar-title>
      <!-- opens right-side drawer using its ref -->
      <button class="hide-on-drawer-visible" @click="$refs.rightDrawer.open()">
          <i>menu</i>
        </button>
    </div>
    <div class="full-width" v-if="page == 'transactions'">
      <button class="primary full-width" @click="startNewTransaction()">
        Start New Transaction<i class="on-right">add</i>
      </button>

      <section id="event">
        <div class="card">
          <div class="card-content">
            <div class="row">
              <span class="width-1of4">June 13 2017</span><span class="auto">Millarville Farmers Market</span><span class="auto">Team Sean</span><span id="tx-total" class="auto">Total: 595</span>
            </div>
          </div>
        </div>
      </section>  

      <section id="transactions">
        <section class="card" v-for="tx in tfpData.transactions" v-bind:currTx="tx" :key="tx.id">
          <div :id="'btn'+tx.id" class="card-content">
            <div class="row tx-summary-title text-italic light-paragraph item-delimiter">
              <div class="width-1of5">Tx#</div>
              <div class="width-1of3">Time</div>
              <div class="width-2of4">Sum</div>
              <div class="width-2of4">Tax</div>
              <div class="width-2of4">Total</div>
              <div class="auto">TxType</div>
            </div>
            <div class="row tx-summary">
              <div class="width-1of5">{{tx.id}}</div>
              <div class="width-1of3">{{('0' + new Date(tx.txTime).getHours()).slice(-2) + ':' + ('0' + new Date(tx.txTime).getMinutes()).slice(-2)}}</div>
              <div class="row width-2of4"><div class="auto">{{tx.total}}</div></div>
              <div class="row width-2of4"><div class="auto">{{tx.tax}}</div></div>
              <div class="row width-2of4"><div class="auto">{{tx.total + tx.tax}}</div></div>
              <div class="auto">{{tx.pp_or_pl}}</div>
            </div>
            <div class="row tx-rows-title text-italic" style="background-color: #dadada;">
              <div class="offset-1of5"></div>
              <div class="width-1of3">Product</div>
              <div class="width-2of4">Description</div>
              <div class="width-2of4">Qty</div>
              <div class="width-2of4">Price</div>
              <div class="auto">Tax</div>
            </div>
            <div class="row tx-row" v-for="item in selectedTransactionItems(tx)">
              <div class="offset-1of5"></div>
              <div class="width-1of3">{{item.productTypeDesc}}</div>
              <div class="width-2of4">{{item.productItemDesc}}</div>
              <div class="width-2of4">{{item.qty}}</div>
              <div class="width-2of4">{{item.price}}</div>
              <div class="auto">{{item.tax}}</div>
            </div>
          </div>
        </section>
      </section>
    </div>

    <q-drawer ref="rightDrawer">
      <div class="toolbar">
        <q-toolbar-title>
          Setup
        </q-toolbar-title>
      </div>
      <div class="list no-border platform-delimiter">
        <q-drawer-link icon="mail" :to="{path: '/', exact: true}">
          Start the day
        </q-drawer-link>
        <q-drawer-link icon="mail" :to="{path: '/', exact: true}">
          Product Data
        </q-drawer-link>
      </div>
    </q-drawer>

    <div id="stepper-section" class="list" style="overflow: scroll;" v-if="page == 'new-transactions'">
      <q-collapsible id="chooseProduct" opened icon="explore" :img="selectedProductTypeImage" :label="productTypeMessage" group="tx" ref="chooseProduct">
        <div>
          <div class="row wrap">
            <div class="width-4of12 auto">
              <button :id="'btn'+item.id" class="tx-img-button" @click="selectProductType(item)" v-for="item in tfpData.productTypes">
                <img :src= "'./statics/'+item.img" :title="item.name" style="width: 128px" />
                <br/>
                <span class="label">{{item.name}}</span> 
              </button>
            </div>
          </div>
        </div>
      </q-collapsible>
      <q-collapsible id="chooseItem" icon="perm_identity" :img="selectedItemImage" :label="itemMessage" group="tx" ref="chooseItem">
        <div>
          <div class="row wrap">
            <div class="width-1of12 auto">
              <button :id="'btn'+item.id" class="tx-img-button" @click="selectProduct(item)" v-for="item in selectedProductTypeItems">
                <img :src= "'./statics/'+item.img" :alt="item.desc" style="width: 128px" />
                <br/>
                <span class="label">{{item.desc}}</span> 
              </button>
            </div>
          </div>
        </div>
      </q-collapsible>
      <q-collapsible id="chooseQty" icon="shopping_cart" label="Choose Quantity" group="tx" ref="chooseQty">
        <div>
          <div class="row wrap">
            <div class="width-1of12 auto">
              <div>
                <label>Quantity:</label>
                <q-numeric v-model="qty" :min="1" :max="99"></q-numeric>
              </div>
              <div>
                <label>Price:</label>
                <input v-model="price" placeholder="Unit price">
              </div>
            </div>
          </div>
          <div class="row wrap">
            <div class="width-1of12 auto">
                <button class="primary" style="width: 250px; margin-bottom: 5px;" @click="finish()">Finish and Pay</button>
                <button class="primary" style="width: 250px; margin-bottom: 5px;" @click="saveAndAddNew()">Add Another Item</button>
            </div>
          </div>
        </div>
      </q-collapsible>

      <hr/><br/><br/>

      <div class="card">
        <div class="card-title bg-primary text-white">
          Finish Tx
        </div>
        <div class="card-content card-force-top-padding">
          <div class="row gutter wrap justify-stretch content-center">
            <q-data-table class="width-1of1 auto" style="border: none;" :data="newItems" :config="config" :columns="columns">
              <template slot="selection" scope="selection">
                <button class="primary clear" @click="changeMessage(selection)">
                  <i>edit</i>
                </button>
                <button class="primary clear" @click="deleteRow(selection)">
                  <i>delete</i>
                </button>
              </template>
            </q-data-table>
            <div class="width-1of1 auto">
              <div class="row" style="margin-bottom: 5px;">
                <label class="width-1of5">Type:</label>
                <div class="auto tx-switch">
                  <label class="auto">pl</label>
                  <q-toggle class="auto" v-model="pp" @input="selectPayType"></q-toggle>
                  <label class="auto">pp</label>
                </div>
              </div>
              <div class="row" style="margin-bottom: 5px;">
                <label class="width-1of5">Tx Price:</label>
                <input class="auto" style="background-color: #cacaca;" v-model="runningTotal" placeholder="Total">
              </div>
              <div class="row" style="margin-bottom: 5px;">
                <label class="row width-1of5">+</label>
                <input class="auto" style="background-color: #cacaca;" v-model="transactionTax" placeholder="Tax">
              </div>
              <div class="row" style="margin-bottom: 5px;">
                <label class="row width-1of5">=</label>
                <input class="auto" style="background-color: #cacaca;" v-model="transactionTotal" placeholder="Pay">
              </div>
            </div>
          </div>
          <div class="row wrap">
            <div class="width-1of1">
                <button class="primary width-1of1" style="width: 250px; margin-bottom: 5px;" @click="startNewTransaction()">
                  Start New Transaction<i class="on-right">add</i>
                </button>
                <button class="primary width-1of1" style="width: 250px; margin-bottom: 5px;" @click="transactionList()">
                  Back to Transaction List
                </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </q-layout>
</template>

<script>
  import TfpData from '../TfpData.json'

  export default {
    data () {
      return {
        tfpData: TfpData,

        // settings
        taxRate: 0.05,

        // state values
        page: 'transactions',
        selectedProductTypeImage: '',
        productTypeMessage: 'Select a Product',
        selectedItemImage: '',
        itemMessage: 'Select an Item',

        // item values
        qty: 1,
        price: 0,
        tax: 0,
        total: 0,

        // transaction values
        runningTotal: 0,
        taxTotal: 0,
        transactionTax: 0,
        transactionTotal: 0,
        pp: false,
        productTypeSelected: '',
        productType: '',
        product: '',
        currTx: {},

        productTypes: TfpData,
        txId: 1,
        newItems: [],
        newTransaction: {},

        // transaction arrays
        config: {
          rowHeight: '30px',  // [REQUIRED] Set the row height
          title: 'Transaction Items',
          noHeader: false,
          refresh: true,
          columnPicker: false,
          leftStickyColumns: 1,
          rightStickyColumns: 0,
          bodyStyle: {
            maxHeight: '500px'
          },
          selection: 'single',
          messages: {
            noData: '<i>warning</i> No data available to show.',
            noDataAfterFiltering: '<i>warning</i> No results. Please refine your search terms.'
          },

          // (optional) Override default labels. Useful for I18n.
          labels: {
            rows: 'Items',
            selected: {
              singular: 'item selected.',
              plural: 'items selected.'
            },
            clear: 'clear',
            all: 'All'
          }
        },
        columns: [
          {
            label: 'Type', // [REQUIRED] Column name
            field: 'productTypeDesc', // [REQUIRED] Row property name
            width: '50px' // [REQUIRED] Column width
          },
          {
            label: 'Product',
            field: 'productItemDesc',
            width: '100px'
          },
          {
            label: 'Qty',
            field: 'qty',
            width: '20px'
          },
          {
            label: 'Price',
            field: 'price',
            width: '30px'
          },
          {
            label: 'Tax',
            field: 'tax',
            width: '30px'
          },
          {
            label: 'Total',
            field: 'total',
            width: '40px'
          },
          {
            label: 'Running',
            field: 'runningTotal',
            width: '50px'
          }
        ]
      }
    },
    computed: {
      selectedProductTypeItems () {
        if (this.productTypeSelected === '') return null
        let productTypeSelected = this.productTypeSelected
        let obj = this.tfpData.productItems
        let filtered = {}
        Object.keys(obj).forEach(function (key) {
          if (obj[key].productTypeId === productTypeSelected.id) filtered[key] = obj[key]
        })
        return filtered
      }
    },
    methods: {
      selectedTransactionItems (tx) {
        if (this.tfpData.transactions === '') return null
        let _obj = this.tfpData.transactionItems
        let _filtered = {}
        Object.keys(_obj).forEach(function (key) {
          if (_obj[key].transactionId === tx.id) _filtered[key] = _obj[key]
        })
        // alert(JSON.stringify(_filtered, null, 4))
        return _filtered
      },

      startNewTransaction: function () {
        this.page = 'new-transactions'
        let _txId = this.txId += 1
        this.newTransaction = {
          id: _txId,
          txNumber: _txId,
          txTime: Date.now(),
          dayInfoId: 1,
          user: 1,
          salesperson: 1,
          pp_or_pl: 0,
          total: 0,
          tax: 0
        }
        // alert(JSON.stringify(this.newTransaction, null, 4))
      },

      selectProductType: function (productType) {
        this.productTypeSelected = productType
        this.productType = productType
        this.selectedProductTypeImage = './statics/' + productType.img
        this.productTypeMessage = productType.name + ' selected'
        this.$refs['chooseItem'].open()
      },

      selectProduct: function (item) {
        this.product = item
        this.price = item.price
        this.selectedItemImage = './statics/' + item.img
        this.itemMessage = this.product.desc + ' selected'
        this.$refs['chooseQty'].open()
      },

      selectPayType: function (val) {
        this.calculateTransactionTotals()
      },

      finish: function () {
        let _tax = this.pp ? 0 : this.taxRate
        this.newItems.push({
          productTypeId: this.productTypeSelected.id,
          productTypeDesc: this.productTypeSelected.desc,
          productItemId: this.product.id,
          productItemDesc: this.product.desc,
          qty: this.qty,
          price: this.price,
          tax: _tax,
          total: (this.price + (this.price * _tax)) * this.qty,
          runningTotal: this.runningTotal += (this.price + (this.price * _tax)) * this.qty
        })
        this.calculateTransactionTotals()
        this.saveTransaction()
      },

      calculateTransactionTotals: function () {
        let tempArr = []
        let _runningTotal = 0
        let _runningTotalTax = 0
        let _tax = this.pp ? 0 : this.taxRate

        this.newItems.forEach(function (item) {
          _runningTotal += item.price * item.qty
          _runningTotalTax += (item.price * _tax) * item.qty
          tempArr.push({
            productTypeId: item.productTypeId,
            productTypeDesc: item.productTypeDesc,
            productItemId: item.productItemId,
            productItemDesc: item.productItemDesc,
            qty: item.qty,
            price: item.price,
            tax: item.price * _tax * item.qty,
            total: (item.price + (item.price * _tax)) * item.qty,
            runningTotal: _runningTotal + _runningTotalTax
          })
        })
        this.newItems = tempArr
        this.runningTotal = _runningTotal
        this.transactionTax = _runningTotalTax
        this.transactionTotal = this.runningTotal + this.transactionTax
        // alert(JSON.stringify(this.newItems))
      },

      saveTransaction: function () {
        let _tfpData = this.tfpData
        this.newTransaction.pp_or_pl = this.pp ? 'pl' : 'pp'
        this.newTransaction.total = this.transactionTotal
        this.newTransaction.tax = this.transactionTax
        _tfpData.transactions[this.newTransaction.id] = this.newTransaction

        let _newTx = this.newTransaction
        let _id = 3
        this.newItems.forEach(function (item) {
          let _tmp = {
            id: _id++,
            transactionId: _newTx.id,
            productTypeId: item.productTypeId,
            productTypeDesc: item.productTypeDesc,
            productItemId: item.productItemId,
            productItemDesc: item.productItemDesc,
            qty: item.qty,
            price: item.price,
            tax: item.tax
          }
          _tfpData.transactionItems[_tmp.id] = _tmp
        })
        this.tfpData = _tfpData
      },

      saveAndAddNew: function () {
        this.finish()
        this.$refs['chooseProduct'].open()
      },

      transactionList: function () {
        this.page = 'transactions'
      }
    }
  }

</script>

<style>
</style>
