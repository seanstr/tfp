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
    <div class="full-width">
      <div class="card">
        <div class="card-title bg-primary text-white">
          Start The Day
        </div>
        <div class="card-content card-force-top-padding">
          <div class="row gutter wrap justify-stretch content-center">
            <div class="width-1of1 auto">
              <div class="row" style="margin-bottom: 5px;">
                <label class="width-1of5">Date:</label>
                <div class="auto tx-switch">
                  <q-datetime v-model="dateOfShow" type="date" @input="tfpData.markets.dateOfShow" placeholder="date of the market"></q-datetime>
                </div>
              </div>
              <div class="row" style="margin-bottom: 5px;">
                <label class="width-1of5">Location:</label>
                <input class="auto" style="background-color: #cacaca;" v-model="market" placeholder="select the market">
              </div>
              <div class="row" style="margin-bottom: 5px;">
                <label class="width-1of5">Location:</label>
                <q-select type="list" v-model="tfpData.markets" :options="tfpData.markets"></q-select>
              </div>
              <div class="row" style="margin-bottom: 5px;">
                <label class="row width-1of5">Team:</label>
                <input class="auto" style="background-color: #cacaca;" v-model="teamName" placeholder="team name">
              </div>
            </div>
          </div>
          <div class="row wrap">
            <div class="width-1of1">
                <button class="primary width-1of1" style="width: 250px; margin-bottom: 5px;" @click="startNewTransaction()">
                  Save
                </button>
                <button class="primary width-1of1" style="width: 250px; margin-bottom: 5px;" @click="transactionList()">
                  Cancel
                </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </q-layout>
</template>
