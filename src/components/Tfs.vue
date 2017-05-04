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
    <div class="full-width">
      <button class="primary full-width" @click="$('#stepper-section')">
        Start New Transaction<i class="on-right">add</i>
      </button>
<!--       <div id="app">
        message
      </div>

      <div id="app-2">
        <span>
          app-2
        </span>
      </div>
 -->
      <div id="app-3">
        <div class="card">
          <div class="card-content">
            <div class="row">
              <span class="width-1of4">June 13 2017</span>
              <span class="auto">Millarville Farmers Market</span>
              <span class="auto">Team Sean</span>
              <span id="tx-total" class="auto">Total: 170</span>
            </div>
          </div>
        </div>
      </div>  

      <div id="app-4">
        <div class="card">
          <div class="card-content">
            <div class="row">
              <div class="width-4of4">
            <div class="row">
              <div class="width-2of8">Tx:00010</div>
              <div class="width-1of8">14:22</div>
              <div class="width-1of8">1</div>
              <div class="width-3of8">
                <div class="width-2of3">peppermill</div>
                <div class="width-1of3">Green</div>
              </div>
              <div class="width-1of8">85</div>
              </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div id="stepper-section" class="hidden">
      <q-stepper @finish="finish()" ref="stepper">
        <q-step title="Add Products">
          <button id="addProduct" class="primary big" @click="clickMethod()">
            <img src="~assets/peppermill.png" alt="peppermills">
          </button>
          
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
