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
                <label class="width-1of5">Date:</label>
                <div class="auto tx-switch">
                  <q-inline-datetime v-model="dateOfShow" type="date" @input="dateOfShow" placeholder="2017-10-24T10:40:14.674Z"></q-inline-datetime>
                </div>
              </div>
              <div class="row" style="margin-bottom: 5px;">
                <label class="width-1of5">Location:</label>
                <input class="auto" style="background-color: #cacaca;" v-model="location" placeholder="Total">
              </div>
              <div class="row" style="margin-bottom: 5px;">
                <label class="row width-1of5">Team:</label>
                <input class="auto" style="background-color: #cacaca;" v-model="teamName" placeholder="Tax">
              </div>
            </div>
          </div>
          <div class="row wrap">
            <div class="width-1of1">
                <button class="primary width-1of1" style="width: 250px; margin-bottom: 5px;" @click="startNewTransaction()">
                  Save<i class="on-right">add</i>
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