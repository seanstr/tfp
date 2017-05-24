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
              <span class="width-1of4">June 13 2017</span>
              <span class="auto">Millarville Farmers Market</span>
              <span class="auto">Team Sean</span>
              <span id="tx-total" class="auto">Total: 595</span>
            </div>
          </div>
        </div>
      </section>  

      <section id="transactions">
        <section class="card">
          <div class="card-content">
            <div class="row tx-summary-title">
              <div class="width-1of5">Tx#</div>
              <div class="width-1of3">Time</div>
              <div class="width-2of4">TxTotal</div>
              <div class="auto">TxType</div>
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
              <div class="offset-1of5"></div>
              <div class="width-1of3">Product</div>
              <div class="width-2of4">Description</div>
              <div class="auto">Price</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div>
              <div class="width-1of3">peppermill</div>
              <div class="width-2of4">Green</div>
              <div class="auto">85</div>
            </div>
          </div>
        </section>
        <section class="card">
          <div class="card-content">
            <div class="row tx-summary-title">
              <div class="width-1of5">Tx#</div>
              <div class="width-1of3">Time</div>
              <div class="width-2of4">TxTotal</div>
              <div class="auto">TxType</div>
            </div>
            <div class="row tx-summary">
              <div class="width-1of5">00009</div>
              <div class="width-1of3">14:00</div>
              <div class="row width-2of4">
                <div class="auto">170</div>
                <div class="auto">8.5</div>
                <div class="auto">185.5</div>
              </div>
              <div class="auto">pl</div>
            </div>
            <div class="row tx-rows-title">
              <div class="offset-1of5"></div>
              <div class="width-1of3">Product</div>
              <div class="width-2of4">Description</div>
              <div class="auto">Price</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div>
              <div class="width-1of3">peppermill</div>
              <div class="width-2of4">Red</div>
              <div class="auto">85</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div>
              <div class="width-1of3">peppermill</div>
              <div class="width-2of4">Blue</div>
              <div class="auto">85</div>
            </div>
          </div>
        </section>
      </section>
        <section class="card">
          <div class="card-content">
            <div class="row tx-summary-title">
              <div class="width-1of5">Tx#</div>
              <div class="width-1of3">Time</div>
              <div class="width-2of4">TxTotal</div>
              <div class="auto">TxType</div>
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
              <div class="offset-1of5"></div>
              <div class="width-1of3">Product</div>
              <div class="width-2of4">Description</div>
              <div class="auto">Price</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div>
              <div class="width-1of3">pen</div>
              <div class="width-2of4">Winchester Lever Action</div>
              <div class="auto">75</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div>
              <div class="width-1of3">pen</div>
              <div class="width-2of4">Dragon</div>
              <div class="auto">95</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div>
              <div class="width-1of3">pen case</div>
              <div class="width-2of4">Gun case</div>
              <div class="auto">20</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div>
              <div class="width-1of3">peppermill</div>
              <div class="width-2of4">Spalted Maple</div>
              <div class="auto">85</div>
            </div>
            <div class="row">
              <div class="offset-1of5"></div>
              <div class="width-1of3">peppermill</div>
              <div class="width-2of4">Burnt Birch</div>
              <div class="auto">75</div>
            </div>
          </div>
        </section>
      </section>
    </div>

    <div id="stepper-section" class="list">
      <q-collapsible id="chooseProduct" opened icon="explore" label="Select a Product">
        <div>
          <div class="row wrap">
            <div class="width-1of12 auto">
              <button :id="'btn'+item[0]" class="tx-img-button" @click="selectProductType(item[0])" v-for="item in productTypes">
                <img :src= "'./statics/'+item[1]" :alt="item[0]" />
              </button>
            </div>
          </div>
        </div>
      </q-collapsible>
      <q-collapsible id="chooseItem" icon="perm_identity" label="Select an Item">
        <div>
          <div class="row wrap">
            <div class="width-1of12 auto">
              <button :id="'btn'+item[0]" class="tx-img-button" @click="selectProduct(item[2], item[1])" v-for="item in productType">
                <img :src= "'./statics/'+item[2]" :alt="item[0]" style="width: 128px" />
              </button>
            </div>
          </div>
        </div>
      </q-collapsible>
      <q-collapsible id="chooseQty" icon="shopping_cart" label="Finish">
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
        </div>
      </q-collapsible>

      <q-card title="Finish">
        <div class="full-width">
          <div class="row gutter wrap justify-stretch content-center">
            <div class="width-1of1 auto">
              <div>
                <label>Type:</label>
                <label>pp</label>
                <q-toggle v-model="pp"></q-toggle>
                <label>pl</label>
              </div>
              <div>
                <label>Tx Price:</label>
                <input v-model="price" placeholder="Total">
                +
                <input v-model="tax" placeholder="Tax">
                =
                <input v-model="total" placeholder="Pay">
              </div>
              <div>
                <button class="primary">Add Item to Tx</button>
              </div>
            </div>
          </div>
        </div>
      </q-card>
    </div>
  </q-layout>
</template>

<script>
  export default {
    data () {
      return {
        quantity: 1,
        price: 85,
        tax: 0,
        total: 0,
        pp: false,
        productType: '',
        productTypes: [
          ['pens', 'pen.png'],
          ['peppermills', 'peppermill.png'],
          ['pizzacutters', 'pizzacutter.png'],
          ['icecreamscoops', 'icecreamscoop.png'],
          ['seamrippers', 'seamripper.png'],
          ['corkscrews', 'corkscrew.png'],
          ['shavingkits', 'peppermill.png'],
          ['lamps', 'peppermill.png'],
          ['clocks', 'peppermill.png'],
          ['maps', 'peppermill.png']
        ],
        pens: [
          ['30/30 lever', 75, 'pens/lever.jpg'],
          ['30 cal', 75, 'pens/peppermill.png'],
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
          ['bubinga', 85, '~assets/peppermills/peppermill.png'],
          ['burnt cedar', 75, '~assets/peppermills/peppermill.png'],
          ['burmese redwodd', 85, '~assets/peppermills/peppermill.png'],
          ['burnt catalpa', 75, '~assets/peppermills/peppermill.png'],
          ['burnt elm', 75, '~assets/peppermills/dragon.png'],
          ['catalpa', 75, '~assets/peppermills/peppermill.png'],
          ['cedar', 75, '~assets/peppermills/peppermill.png'],
          ['cherry', 85, '~assets/peppermills/peppermill.png'],
          ['elm', 75, '~assets/peppermills/peppermill.png'],
          ['indian redwood', 85, '~assets/peppermills/peppermill.png'],
          ['laminatedblue', 85, '~assets/peppermills/peppermill.png'],
          ['laminatedgreen', 85, '~assets/peppermills/peppermill.png'],
          ['laminatedred', 85, '~assets/peppermills/peppermill.png'],
          ['laminatedsilverblue', 85, '~assets/peppermills/peppermill.png'],
          ['laminatedsilvergreen', 85, '~assets/peppermills/peppermill.png'],
          ['laminatedsilverred', 85, '~assets/peppermills/peppermill.png'],
          ['mahogany', 85, '~assets/peppermills/peppermill.png'],
          ['oak', 85, '~assets/peppermills/shotgun.png'],
          ['padauk', 85, '~assets/peppermills/peppermill.png'],
          ['spalted maple', 85, '~assets/peppermills/peppermill.png'],
          ['spalted elm', 85, '~assets/peppermills/peppermill.png'],
          ['walnut', 85, '~assets/peppermills/peppermill.png']
        ],
        pizzacutters: [
          ['burmese redwodd', 60, '~assets/peppermills/peppermill.png'],
          ['catalpa', 60, '~assets/peppermills/peppermill.png'],
          ['cedar', 60, '~assets/peppermills/peppermill.png'],
          ['cherry', 60, '~assets/peppermills/peppermill.png'],
          ['elm', 60, '~assets/peppermills/peppermill.png'],
          ['indian redwood', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedblue', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedgreen', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedred', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedsilverblue', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedsilvergreen', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedsilverred', 60, '~assets/peppermills/peppermill.png'],
          ['mahogany', 60, '~assets/peppermills/peppermill.png'],
          ['oak', 60, '~assets/peppermills/shotgun.png'],
          ['padauk', 60, '~assets/peppermills/peppermill.png'],
          ['spalted maple', 60, '~assets/peppermills/peppermill.png'],
          ['spalted elm', 60, '~assets/peppermills/peppermill.png'],
          ['walnut', 60, '~assets/peppermills/peppermill.png']
        ],
        icecreamscoops: [
          ['burmese redwodd', 60, '~assets/peppermills/peppermill.png'],
          ['catalpa', 60, '~assets/peppermills/peppermill.png'],
          ['cedar', 60, '~assets/peppermills/peppermill.png'],
          ['cherry', 60, '~assets/peppermills/peppermill.png'],
          ['elm', 60, '~assets/peppermills/peppermill.png'],
          ['indian redwood', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedblue', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedgreen', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedred', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedsilverblue', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedsilvergreen', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedsilverred', 60, '~assets/peppermills/peppermill.png'],
          ['mahogany', 60, '~assets/peppermills/peppermill.png'],
          ['oak', 60, '~assets/peppermills/shotgun.png'],
          ['padauk', 60, '~assets/peppermills/peppermill.png'],
          ['spalted maple', 60, '~assets/peppermills/peppermill.png'],
          ['spalted elm', 60, '~assets/peppermills/peppermill.png'],
          ['walnut', 60, '~assets/peppermills/peppermill.png']
        ],
        seamrippers: [
          ['burmese redwodd', 60, '~assets/peppermills/peppermill.png'],
          ['catalpa', 60, '~assets/peppermills/peppermill.png'],
          ['cedar', 60, '~assets/peppermills/peppermill.png'],
          ['cherry', 60, '~assets/peppermills/peppermill.png'],
          ['elm', 60, '~assets/peppermills/peppermill.png'],
          ['indian redwood', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedblue', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedgreen', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedred', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedsilverblue', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedsilvergreen', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedsilverred', 60, '~assets/peppermills/peppermill.png'],
          ['mahogany', 60, '~assets/peppermills/peppermill.png'],
          ['oak', 60, '~assets/peppermills/shotgun.png'],
          ['padauk', 60, '~assets/peppermills/peppermill.png'],
          ['spalted maple', 60, '~assets/peppermills/peppermill.png'],
          ['spalted elm', 60, '~assets/peppermills/peppermill.png'],
          ['walnut', 60, '~assets/peppermills/peppermill.png']
        ],
        corkscrews: [
          ['burmese redwodd', 60, '~assets/peppermills/peppermill.png'],
          ['catalpa', 60, '~assets/peppermills/peppermill.png'],
          ['cedar', 60, '~assets/peppermills/peppermill.png'],
          ['cherry', 60, '~assets/peppermills/peppermill.png'],
          ['elm', 60, '~assets/peppermills/peppermill.png'],
          ['indian redwood', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedblue', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedgreen', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedred', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedsilverblue', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedsilvergreen', 60, '~assets/peppermills/peppermill.png'],
          ['laminatedsilverred', 60, '~assets/peppermills/peppermill.png'],
          ['mahogany', 60, '~assets/peppermills/peppermill.png'],
          ['oak', 60, '~assets/peppermills/shotgun.png'],
          ['padauk', 60, '~assets/peppermills/peppermill.png'],
          ['spalted maple', 60, '~assets/peppermills/peppermill.png'],
          ['spalted elm', 60, '~assets/peppermills/peppermill.png'],
          ['walnut', 60, '~assets/peppermills/peppermill.png']
        ],
        shavingkits: [
          ['cocobolo', 235, '~assets/peppermills/peppermill.png']
        ],
        lamps: [
          ['steampunk', 235, '~assets/peppermills/peppermill.png'],
          ['tripledome', 235, '~assets/peppermills/peppermill.png'],
          ['dome', 235, '~assets/peppermills/peppermill.png'],
          ['edison', 235, '~assets/peppermills/peppermill.png']
        ],
        clocks: [
          ['dome', 235, '~assets/peppermills/peppermill.png']
        ],
        maps: [
          ['small', 185, '~assets/peppermills/peppermill.png'],
          ['medium', 235, '~assets/peppermills/peppermill.png'],
          ['large', 295, '~assets/peppermills/peppermill.png']
        ]
      }
    },

    methods: {
      selectProductType: function (productType) {
        alert('selected ' + productType)
        this.productType = this[productType]
      },

      selectProduct: function (_product, _price) {
        alert(_product + ': ' + _price)
        this.price = _price
      },

      finish: function () {
        alert('finished')
      }
    }
  }
</script>

<style>
</style>
