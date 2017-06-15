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
      <button class="primary full-width" @click="page = 'new-transactions' ">
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
        <section class="card">
          <div class="card-content">
            <div class="row tx-summary-title">
              <div class="width-1of5">Tx#</div><div class="width-1of3">Time</div><div class="width-2of4">TxTotal</div><div class="auto">TxType</div>
            </div>
            <div class="row tx-summary">
              <div class="width-1of5">00010</div>
              <div class="width-1of3">14:22</div>
              <div class="row width-2of4">
                <div class="auto">85</div>
              </div>
              <div class="auto">pp</div>
            </div>
            <div class="row tx-rows-title">
              <div class="offset-1of5"></div><div class="width-1of3">Product</div><div class="width-2of4">Description</div><div class="auto">Price</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div><div class="width-1of3">peppermill</div><div class="width-2of4">Green</div><div class="auto">85</div>
            </div>
          </div>
        </section>
        <section class="card">
          <div class="card-content">
            <div class="row tx-summary-title">
              <div class="width-1of5">Tx#</div><div class="width-1of3">Time</div><div class="width-2of4">TxTotal</div><div class="auto">TxType</div>
            </div>
            <div class="row tx-summary">
              <div class="width-1of5">00009</div>
              <div class="width-1of3">14:00</div>
              <div class="row width-2of4">
                <div class="auto">170</div><div class="auto">8.5</div><div class="auto">185.5</div>
              </div>
              <div class="auto">pl</div>
            </div>
            <div class="row tx-rows-title">
              <div class="offset-1of5"></div><div class="width-1of3">Product</div><div class="width-2of4">Description</div><div class="auto">Price</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div><div class="width-1of3">peppermill</div><div class="width-2of4">Red</div><div class="auto">85</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div><div class="width-1of3">peppermill</div><div class="width-2of4">Blue</div><div class="auto">85</div>
            </div>
          </div>
        </section>
      </section>
        <section class="card">
          <div class="card-content">
            <div class="row tx-summary-title">
              <div class="width-1of5">Tx#</div><div class="width-1of3">Time</div><div class="width-2of4">TxTotal</div><div class="auto">TxType</div>
            </div>
            <div class="row tx-summary">
              <div class="width-1of5">00008</div>
              <div class="width-1of3">13:00</div>
              <div class="row width-2of4">
                <div class="auto">340</div>
              </div>
              <div class="auto">pp</div>
            </div>
            <div class="row tx-rows-title">
              <div class="offset-1of5"></div><div class="width-1of3">Product</div><div class="width-2of4">Description</div><div class="auto">Price</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div><div class="width-1of3">pen</div><div class="width-2of4">Winchester Lever Action</div><div class="auto">75</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div><div class="width-1of3">pen</div><div class="width-2of4">Dragon</div><div class="auto">95</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div><div class="width-1of3">pen case</div><div class="width-2of4">Gun case</div><div class="auto">20</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div><div class="width-1of3">peppermill</div><div class="width-2of4">Spalted Maple</div><div class="auto">85</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div><div class="width-1of3">peppermill</div><div class="width-2of4">Burnt Birch</div><div class="auto">75</div>
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

    <div id="stepper-section" class="list item-delimiter"  v-if="page == 'new-transactions'">
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
                <q-numeric v-model="quantity" :min="1" :max="99"></q-numeric>
              </div>
              <div>
                <label>Price:</label>
                <input v-model="price" placeholder="Unit price">
              </div>
            </div>
          </div>
          <div class="row wrap">
            <div class="width-1of12 auto">
                <button class="primary" @click="finish()">Finish and Pay</button>
                <button class="primary" @click="saveAndAddNew()">Add Another Item</button>
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
            <q-data-table :data="newItems" :config="config" :columns="columns">
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
              <div>
                <label>Type:</label>
                <label>pl</label>
                <q-toggle v-model="pp" @input="selectPayType"></q-toggle>
                <label>pp</label>
              </div>
              <div>
                <label>Tx Price:</label>
                <input v-model="runningTotal" placeholder="Total">
                +
                <input v-model="transactionTax" placeholder="Tax">
                =
                <input v-model="transactionTotal" placeholder="Pay">
              </div>
            </div>
          </div>
          <div class="row wrap">
            <div class="width-1of12 auto">
                <button class="primary" @click="newTransaction()">
                    Start New Transaction<i class="on-right">add</i>
                </button>
                <button class="primary" @click="transactionList()">Back to Transaction List</button>
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
        quantity: 1,
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

        productTypes: TfpData,
        newItems: '',

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
            field: 'productType', // [REQUIRED] Row property name
            width: '50px' // [REQUIRED] Column width
          },
          {
            label: 'Product',
            field: 'product',
            width: '100px'
          },
          {
            label: 'Qty',
            field: 'quantity',
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
      selectProductType: function (productType) {
        this.productTypeSelected = productType
        this.productType = productType
        this.selectedProductTypeImage = './statics/' + productType.img
        this.productTypeMessage = productType.name + ' selected'
        this.$refs['chooseItem'].open()
      },

      selectProduct: function (item) {
        this.product = item.name
        this.price = item.price
        this.selectedItemImage = './statics/' + item.img
        this.itemMessage = this.product + ' selected'
        this.$refs['chooseQty'].open()
      },

      selectPayType: function (val) {
        this.calculateTransactionTotals()
      },

      finish: function () {
        if (Object.keys(this.newItems[0]).length === 0 && this.newItems[0].constructor === Object) this.newItems = []
        let _tax = this.pp ? 0 : this.taxRate
        this.newItems.push({
          productType: this.productTypeSelected,
          product: this.product,
          quantity: this.quantity,
          price: this.price,
          tax: _tax,
          total: this.price + (this.price * _tax) * this.quantity,
          runningTotal: this.runningTotal += (this.price + (this.price * _tax) * this.quantity)
        })
        this.calculateTransactionTotals()
      },

      calculateTransactionTotals: function () {
        let tempArr = []
        let _runningTotal = 0
        let _runningTotalTax = 0
        let _tax = this.pp ? 0 : this.taxRate

        this.newItems.forEach(function (item) {
          _runningTotal += item.price * item.quantity
          _runningTotalTax += (item.price * _tax) * item.quantity
          tempArr.push({
            productType: item.productType,
            product: item.product,
            quantity: item.quantity,
            price: item.price,
            tax: _tax,
            total: (item.price + (item.price * _tax)) * item.quantity,
            runningTotal: _runningTotal + _runningTotalTax
          })
        })
        this.newItems = tempArr
        this.runningTotal = _runningTotal
        this.transactionTax = _runningTotalTax
        this.transactionTotal = this.runningTotal + this.transactionTax
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
