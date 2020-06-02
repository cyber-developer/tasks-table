<template>
  <div>
    <!-- calendar -->
    <v-layout class="mb-3 pa-3 bg-grey" align-center>
      <v-flex xs6>
        <DatePicker />
      </v-flex>
      <v-flex xs6>
        <div class="size-18 grey--text text--darken-2 font-weight-bold text-center">
          7 Duplicate Sets
        </div>
      </v-flex>
    </v-layout>
    <!-- search and export -->
    <v-layout class="mb-3">
      <v-flex class="pr-2 width-100">
        <v-text-field
            placeholder="search"
            append-icon="mdi-magnify"
            hide-details
            outlined
            dense
        />
      </v-flex>
      <v-flex>
        <v-btn outlined height="40" color="grey darken-2">Export</v-btn>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import DatePicker from './DatePicker'

export default {
  name: 'table-top',
  components: {
    DatePicker
  }
}
</script>

<style>

</style>
