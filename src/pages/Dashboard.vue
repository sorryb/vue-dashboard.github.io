<template>
  <v-container fluid grid-list-xl>
    <v-layout row wrap>
      <!-- Widgets-->
      <v-flex d-flex lg6 sm6 xs12>
        <widget icon="domain" title="128 " subTitle= '13% higher then yesterday' supTitle="May's Hazards" color="#00b297"/>
      </v-flex>
      <v-flex d-flex lg6 sm6 xs12>
        <widget icon="money_off" title="1.414" subTitle= '7.212 since 2020' supTitle="All Hazards" color="#dc3545"/>
      </v-flex>
      <!-- Widgets Ends -->
      <!-- Statistics -->
      <v-flex d-flex lg6 sm6 xs12>
        <site-view-statistic/>
      </v-flex>
      <v-flex d-flex lg6 sm6 xs12>
        <location-statistic/>
      </v-flex>
      <!-- Statistics Ends -->
      <!-- DataTable&TimeLine Starts -->
      <v-flex d-flex lg12 sm12 xs12>
        <data-table/>
      </v-flex>
      <!-- DataTable&TimeLine Ends -->
      <v-flex d-flex lg6 sm6 xs12>
        <stepper/>
      </v-flex>
      <v-flex d-flex lg6 sm6 xs12>
        <user-tree-view />
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      lorem: `Lorem ipsum dolor sit amet, mel at clita quando.`
    }
  }
}
</script>

<style>

</style>
