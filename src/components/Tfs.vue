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

    <div id="stepper-section">
      <q-stepper @finish="finish()" ref="stepper">
        <q-step title="Add Products">
        <div>
          <div class="row gutter wrap justify-stretch content-center">
            <div class="width-1of12 auto">
              <button id="addProduct" class="primary big" @click="clickMethod()">
                <img src="~assets/peppermill.png" alt="peppermills">
              </button>
              <button id="addProduct" class="primary big" @click="clickMethod()">
                <img src="~assets/peppermill.png" alt="peppermills">
              </button>
              <button id="addProduct" class="primary big" @click="clickMethod()">
                <img src="~assets/peppermill.png" alt="peppermills">
              </button>
              <button id="addProduct" class="primary big" @click="clickMethod()">
                <img src="~assets/peppermill.png" alt="peppermills">
              </button>
              <button id="addProduct" class="primary big" @click="clickMethod()">
                <img src="~assets/peppermill.png" alt="peppermills">
              </button>
              <button id="addProduct" class="primary big" @click="clickMethod()">
                <img src="~assets/peppermill.png" alt="peppermills">
              </button>
              <button id="addProduct" class="primary big" @click="clickMethod()">
                <img src="~assets/peppermill.png" alt="peppermills">
              </button>
              <button id="addProduct" class="primary big" @click="clickMethod()">
                <img src="~assets/peppermill.png" alt="peppermills">
              </button>
              <button id="addProduct" class="primary big" @click="clickMethod()">
                <img src="~assets/peppermill.png" alt="peppermills">
              </button>
              <button id="addProduct" class="primary big" @click="clickMethod()">
                <img src="~assets/peppermill.png" alt="peppermills">
              </button>
              <button id="addProduct" class="primary big" @click="clickMethod()">
                <img src="~assets/peppermill.png" alt="peppermills">
              </button>
              <button id="addProduct" class="primary big" @click="clickMethod()">
                <img src="~assets/peppermill.png" alt="peppermills">
              </button>
            </div>
          </div>
        </div>

        </q-step>
        <!-- Step specifying when user should be able to jump to next step -->
        <q-step title="Create an ad group" :ready="ready">
          Content, DOM Elements, Components, ...
          Do something and change 'ready' variable to boolean 'true'.
        </q-step>
        <q-step title="Create an ad">
          Content, DOM Elements, Components, ...
        </q-step>
      </q-stepper>
    </div>

  </q-layout>
</template>

<script>
export default {
  data () {
    return {}
  }
}
</script>

<style>
</style>
