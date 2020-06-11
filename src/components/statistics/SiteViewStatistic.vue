<template>
  <v-card class="card">
    <v-card-text class="pa-3">
      <line-chart :data="data" xtitle="Time" ytitle="Hazards" :dataset="{borderWidth: 3}"/>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      data: {
        '2018-05-13': 64,
        '2018-05-14': 20,
        '2018-05-15': 25,
        '2018-05-16': 150,
        '2018-05-17': 2,
        '2018-05-18': 67,
        '2018-05-19': 6,
        '2018-05-20': 80
        }
    }
  }
}
</script>

<style>
  .card {
    border-radius: 3px;
    background-clip: border-box;
    border: 1px solid rgba(0, 0, 0, 0.125);
    box-shadow: 1px 1px 1px 1px rgba(0, 0, 0, 0.21);
    background-color: transparent;
  }
</style>
