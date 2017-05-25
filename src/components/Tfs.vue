<template>
  <q-layout>
    <!-- Header -->
    <div slot="header" class="toolbar">
      <!-- opens left-side drawer using its ref -->
      <button class="hide-on-drawer-visible" @click="$refs.leftDrawer.open()">
        <i>menu</i>
      </button>
      <q-toolbar-title :padding="1">
        Tracy Fine Products
      </q-toolbar-title>
      <!-- opens right-side drawer using its ref -->
      <button class="hide-on-drawer-visible" @click="$refs.rightDrawer.open()">
          <i>menu</i>
        </button>
    </div>

    <!-- Navigation Tabs -->
<!--     <q-tabs slot="navigation">
      <q-tab icon="mail" route="/layout" exact replace>Mails</q-tab>
      <q-tab icon="alarm" route="/layout/alarm" exact replace>Alarms</q-tab>
      <q-tab icon="help" route="/layout/help" exact replace>Help</q-tab>
    </q-tabs>
 -->
<!--     <q-drawer ref="leftDrawer">
       <div class="toolbar">
        <q-toolbar-title>
          Drawer Title
        </q-toolbar-title>
      </div>

       <div class="list no-border platform-delimiter">
        <q-drawer-link icon="mail" :to="{path: '/', exact: true}">
          Link
        </q-drawer-link>
      </div>

     </q-drawer>
 -->
    <div class="full-width hidden">
      <button class="primary full-width" @click="$('#stepper-section')">
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

    <div id="stepper-section" class="list item-delimiter">
      <q-collapsible id="chooseProduct" opened icon="explore" label="Select a Product" group="tx" ref="chooseProduct">
        <div>
          <div class="row wrap">
            <div class="width-4of12 auto">
              <button :id="'btn'+item[0]" class="tx-img-button" @click="selectProductType(item[0])" v-for="item in productTypes">
                <img :src= "'./statics/'+item[1]" :alt="item[0]" style="width: 128px" />
                <br/>
                <span class="label">{{item[0]}}</span> 
              </button>
            </div>
          </div>
        </div>
      </q-collapsible>
      <q-collapsible id="chooseItem" icon="perm_identity" label="Select an Item" group="tx" ref="chooseItem">
        <div>
          <div class="row wrap">
            <div class="width-1of12 auto">
              <button :id="'btn'+item[0]" class="tx-img-button" @click="selectProduct(item)" v-for="item in productType">
                <img :src= "'./statics/'+item[2]" :alt="item[0]" style="width: 128px" />
                <br/>
                <span class="label">{{item[0]}}</span> 
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
                <input v-model="tax" placeholder="Tax">
                =
                <input v-model="total" placeholder="Pay">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </q-layout>
</template>

<script>
  export default {
    data () {
      return {
        // settings
        taxRate: 0.05,

        // item values
        quantity: 1,
        price: 0,
        tax: 0,
        total: 0,

        // transaction values
        runningTotal: 0,
        taxTotal: 0,
        transactionTotal: 0,
        pp: false,
        productTypeSelected: '',
        productType: '',
        product: '',

        // transaction arrays
        transactions: [],
        // newItems: [{productType: 'pens', product: '30 cal', quantity: 1, price: 75, tax: 0, total: 75, runningTotal: 75}],
        newItems: [{}],
        // newItems: [],

        // data arrays
        productTypes: [
          ['pens', 'pen.png'],
          ['peppermills', 'peppermill.png'],
          ['pizzacutters', 'pizzacutter.png'],
          ['icecreamscoops', 'icecreamscoop.png'],
          ['seamrippers', 'seamripper.png'],
          ['corkscrews', 'corkscrew.png'],
          ['shavingkits', 'shavingkit.jpg'],
          ['lamps', 'steampunklamp.jpg'],
          ['clocks', 'clocks.jpg'],
          ['maps', 'maps.jpg']
        ],
        pens: [
          ['30/30 lever', 75, 'pens/lever.jpg'],
          ['30 cal', 75, 'pens/30cal.png'],
          ['50 cal', 55, 'pens/peppermill.png'],
          ['celtic', 95, 'pens/celtic.jpg'],
          ['cowboy', 85, 'pens/cowboy.jpg'],
          ['crystal', 45, 'pens/princess.jpg'],
          ['dragon', 95, 'pens/dragon.jpg'],
          ['firefighter', 120, 'pens/firefighter.jpg'],
          ['flyfish', 75, 'pens/flyfish.jpg'],
          ['harley', 95, 'pens/harley.jpg'],
          ['revolver', 95, 'pens/revolver.jpg'],
          ['shotgun', 95, 'pens/shotgun.jpg'],
          ['skeletonkey', 85, 'pens/peppermill.jpg'],
          ['skull', 85, 'pens/skull.jpg'],
          ['steampunk', 95, 'pens/steampunk.jpg'],
          ['stylus', 55, 'pens/stylus.jpg'],
          ['tech', 55, 'pens/tech.jpg'],
          ['victoriacross', 55, 'pens/victoriacross.jpg']
        ],
        penwood: [
          'antler', 'cocobolo', 'mahogany', 'maple', 'cherry', 'dark', 'light', 'red', 'other'
        ],
        penmetal: [
          'brassplain', 'brassfancy', 'copper', 'gunmetal', 'chrome', 'pewter', 'n/a'
        ],
        'peppermills': [
          ['b_w_ebony', 150, 'peppermills/peppermill.png'],
          ['bubinga', 85, 'peppermills/peppermill.png'],
          ['burnt cedar', 75, 'peppermills/peppermill.png'],
          ['burmese redwodd', 85, 'peppermills/peppermill.png'],
          ['burnt catalpa', 75, 'peppermills/peppermill.png'],
          ['burnt elm', 75, 'peppermills/dragon.png'],
          ['catalpa', 75, 'peppermills/peppermill.png'],
          ['cedar', 75, 'peppermills/peppermill.png'],
          ['cherry', 85, 'peppermills/peppermill.png'],
          ['elm', 75, 'peppermills/peppermill.png'],
          ['indian redwood', 85, 'peppermills/peppermill.png'],
          ['laminatedblue', 85, 'peppermills/peppermill.png'],
          ['laminatedgreen', 85, 'peppermills/peppermill.png'],
          ['laminatedred', 85, 'peppermills/peppermill.png'],
          ['laminatedsilverblue', 85, 'peppermills/peppermill.png'],
          ['laminatedsilvergreen', 85, 'peppermills/peppermill.png'],
          ['laminatedsilverred', 85, 'peppermills/peppermill.png'],
          ['mahogany', 85, 'peppermills/peppermill.png'],
          ['oak', 85, 'peppermills/shotgun.png'],
          ['padauk', 85, 'peppermills/peppermill.png'],
          ['spalted maple', 85, 'peppermills/peppermill.png'],
          ['spalted elm', 85, 'peppermills/peppermill.png'],
          ['walnut', 85, 'peppermills/peppermill.png']
        ],
        pizzacutters: [
          ['burmese redwodd', 60, 'pizzacutters/peppermill.png'],
          ['catalpa', 60, 'pizzacutters/peppermill.png'],
          ['cedar', 60, 'pizzacutters/peppermill.png'],
          ['cherry', 60, 'pizzacutters/peppermill.png'],
          ['elm', 60, 'pizzacutters/peppermill.png'],
          ['indian redwood', 60, 'pizzacutters/peppermill.png'],
          ['laminatedblue', 60, 'pizzacutters/peppermill.png'],
          ['laminatedgreen', 60, 'pizzacutters/peppermill.png'],
          ['laminatedred', 60, 'pizzacutters/peppermill.png'],
          ['laminatedsilverblue', 60, 'pizzacutters/peppermill.png'],
          ['laminatedsilvergreen', 60, 'pizzacutters/peppermill.png'],
          ['laminatedsilverred', 60, 'pizzacutters/peppermill.png'],
          ['mahogany', 60, 'pizzacutters/peppermill.png'],
          ['oak', 60, 'pizzacutters/shotgun.png'],
          ['padauk', 60, 'pizzacutters/peppermill.png'],
          ['spalted maple', 60, 'pizzacutters/peppermill.png'],
          ['spalted elm', 60, 'pizzacutters/peppermill.png'],
          ['walnut', 60, 'pizzacutters/peppermill.png']
        ],
        icecreamscoops: [
          ['burmese redwodd', 60, 'peppermills/peppermill.png'],
          ['catalpa', 60, 'peppermills/peppermill.png'],
          ['cedar', 60, 'peppermills/peppermill.png'],
          ['cherry', 60, 'peppermills/peppermill.png'],
          ['elm', 60, 'peppermills/peppermill.png'],
          ['indian redwood', 60, 'peppermills/peppermill.png'],
          ['laminatedblue', 60, 'peppermills/peppermill.png'],
          ['laminatedgreen', 60, 'peppermills/peppermill.png'],
          ['laminatedred', 60, 'peppermills/peppermill.png'],
          ['laminatedsilverblue', 60, 'peppermills/peppermill.png'],
          ['laminatedsilvergreen', 60, 'peppermills/peppermill.png'],
          ['laminatedsilverred', 60, 'peppermills/peppermill.png'],
          ['mahogany', 60, 'peppermills/peppermill.png'],
          ['oak', 60, 'peppermills/shotgun.png'],
          ['padauk', 60, 'peppermills/peppermill.png'],
          ['spalted maple', 60, 'peppermills/peppermill.png'],
          ['spalted elm', 60, 'peppermills/peppermill.png'],
          ['walnut', 60, 'peppermills/peppermill.png']
        ],
        seamrippers: [
          ['burmese redwodd', 60, 'peppermills/peppermill.png'],
          ['catalpa', 60, 'peppermills/peppermill.png'],
          ['cedar', 60, 'peppermills/peppermill.png'],
          ['cherry', 60, 'peppermills/peppermill.png'],
          ['elm', 60, 'peppermills/peppermill.png'],
          ['indian redwood', 60, 'peppermills/peppermill.png'],
          ['laminatedblue', 60, 'peppermills/peppermill.png'],
          ['laminatedgreen', 60, 'peppermills/peppermill.png'],
          ['laminatedred', 60, 'peppermills/peppermill.png'],
          ['laminatedsilverblue', 60, 'peppermills/peppermill.png'],
          ['laminatedsilvergreen', 60, 'peppermills/peppermill.png'],
          ['laminatedsilverred', 60, 'peppermills/peppermill.png'],
          ['mahogany', 60, 'peppermills/peppermill.png'],
          ['oak', 60, 'peppermills/shotgun.png'],
          ['padauk', 60, 'peppermills/peppermill.png'],
          ['spalted maple', 60, 'peppermills/peppermill.png'],
          ['spalted elm', 60, 'peppermills/peppermill.png'],
          ['walnut', 60, 'peppermills/peppermill.png']
        ],
        corkscrews: [
          ['burmese redwodd', 60, 'peppermills/peppermill.png'],
          ['catalpa', 60, 'peppermills/peppermill.png'],
          ['cedar', 60, 'peppermills/peppermill.png'],
          ['cherry', 60, 'peppermills/peppermill.png'],
          ['elm', 60, 'peppermills/peppermill.png'],
          ['indian redwood', 60, 'peppermills/peppermill.png'],
          ['laminatedblue', 60, 'peppermills/peppermill.png'],
          ['laminatedgreen', 60, 'peppermills/peppermill.png'],
          ['laminatedred', 60, 'peppermills/peppermill.png'],
          ['laminatedsilverblue', 60, 'peppermills/peppermill.png'],
          ['laminatedsilvergreen', 60, 'peppermills/peppermill.png'],
          ['laminatedsilverred', 60, 'peppermills/peppermill.png'],
          ['mahogany', 60, 'peppermills/peppermill.png'],
          ['oak', 60, 'peppermills/shotgun.png'],
          ['padauk', 60, 'peppermills/peppermill.png'],
          ['spalted maple', 60, 'peppermills/peppermill.png'],
          ['spalted elm', 60, 'peppermills/peppermill.png'],
          ['walnut', 60, 'peppermills/peppermill.png']
        ],
        shavingkits: [
          ['cocobolo', 235, 'peppermills/peppermill.png']
        ],
        lamps: [
          ['steampunk', 235, 'peppermills/peppermill.png'],
          ['tripledome', 235, 'peppermills/peppermill.png'],
          ['dome', 235, 'peppermills/peppermill.png'],
          ['edison', 235, 'peppermills/peppermill.png']
        ],
        clocks: [
          ['dome', 235, 'peppermills/peppermill.png']
        ],
        maps: [
          ['small', 185, 'peppermills/peppermill.png'],
          ['medium', 235, 'peppermills/peppermill.png'],
          ['large', 295, 'peppermills/peppermill.png']
        ],
        config: {
          rowHeight: '50px',  // [REQUIRED] Set the row height
          title: 'Transaction Items',
          noHeader: false,
          refresh: true,
          columnPicker: false,
          leftStickyColumns: 0,
          rightStickyColumns: 0,
          bodyStyle: {
            maxHeight: '500px'
          },
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
    methods: {
      selectProductType: function (productType) {
        this.productTypeSelected = productType
        this.productType = this[productType]
        this.$refs['chooseItem'].open()
      },

      selectProduct: function (item) {
        this.product = item[0]
        this.price = item[1]
        this.$refs['chooseQty'].open()
      },

      selectPayType: function (val) {
        this.calculateTransactionTotals()
      },

      finish: function () {
        if (Object.keys(this.newItems[0]).length === 0 && this.newItems[0].constructor === Object) this.newItems = []
        this.newItems.push({
          productType: this.productTypeSelected,
          product: this.product,
          quantity: this.quantity,
          price: this.price,
          tax: this.tax,
          total: this.total,
          runningTotal: this.runningTotal
        })
        // this.calculateTransactionTotals()
      },

      calculateTransactionTotals: function () {
        let _runningTotal = 0
        let _pp = this.pp
        let _taxRate = this.taxRate
        alert(_runningTotal + ' ' + _pp + ' ' + _taxRate)
        let aaa = this.newItems.filter(function (item) {
          _runningTotal += (item.price + item.price * item.tax) * item.quantity
          alert(_pp ? 0 : _taxRate)
          alert(JSON.stringify(item))
          return {
            productType: item.productTypeSelected,
            product: item.product,
            quantity: item.quantity,
            price: 85,
            tax: _pp ? 0 : _taxRate,
            total: 111,
            // total: (item.price + item.price * item.tax) * item.quantity,
            runningTotal: _runningTotal,
            a: 'ab'
          }
        })
        this.runningTotal = _runningTotal
        this.transactionTax = this.runningTotal * this.taxRate
        this.transactionTotal = this.runningTotal + this.transactionTax
        alert(JSON.stringify(aaa))
        // alert(JSON.stringify(this.newItems))
      },

      saveAndAddNew: function () {
        alert('saveAndAddNew')
      }
    }
  }

</script>

<style>
</style>
