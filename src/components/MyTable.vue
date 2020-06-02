<template>
  <div class="table-container">
    <!-- Table Meta -->
    <div class="mb-3">
      <div class="mb-3">
        <span class="font-weight-bold mr-3">Completed Tasks</span>
        <v-icon size="20">mdi-information-outline</v-icon>
      </div>
      <v-progress-linear value="15" color="blue darken-4"></v-progress-linear>
    </div>
    <!-- Table top -->
    <TableTop />
    <!-- Table -->
    <v-data-table
      class="my-table"
      :headers="headers"
      :items="data"
      :mobile-breakpoint="420"
      item-key="name"
      show-expand
      hide-default-footer
      disable-sort
      dense
    >
      <template v-slot:item.source="{item}">
        <span class="font-weight-bold size-13">{{item.source}}</span>
      </template>
      <template v-slot:item.name="{item}">
        <span class="text-blue size-13">{{item.name}}</span>
      </template>
      <template v-slot:item.date="{item}">
        <span class="text-grey size-13">{{item.date}}</span>
      </template>
      <template v-slot:item.confId="{item}">
        <v-btn class="my-1 font-weight-bold" small outlined color="blue darken-4">
          {{item.confId}}
        </v-btn>
      </template>
      <template v-slot:item.id="{item}">
        <div>
          <v-icon size="20">
            {{item.id % 2 == 0 ? 'mdi-clipboard-check-outline' : 'mdi-clipboard-alert-outline'}}
          </v-icon>
        </div>
      </template>
      <template v-slot:expanded-item="{ headers, item }">
        <td></td>
        <td :colspan="headers.length - 1">
          <div class="my-5">
            <v-layout
              class="size-13 my-3"
              v-for="(prop, i) of expandedProps"
              :key="i"
            >
              <span class="width-x">{{prop.name}}</span>
              <span class="font-weight-bold">{{item[prop.value]}}</span>
            </v-layout>
          </div>
          <v-divider class="mb-5"></v-divider>
          <div class="size-13 mb-4">
            <span class="text-grey mr-2">See a mistake?</span>
            <span class="text-blue">Click here</span>
          </div>
        </td>
      </template>
    </v-data-table>
  </div>
</template>

<script>
import TableTop from './TableTop'
import { DATA } from '@/api/tasks.js'

export default {
  name: 'my-table',
  components: {
    TableTop
  },
  data: () => ({
    expandedProps: [
      { name: 'Submitted By', value: 'submittedBy' },
      { name: 'Source', value: 'source' },
      { name: 'Name', value: 'name' },
      { name: 'Account Id', value: 'accountId' },
      { name: 'Billing Street', value: 'billingStreet' },
      { name: 'Lead Source', value: 'leadSource' },
      { name: 'Billing State', value: 'billingState' }
    ],
    headers: [
      { text: '', value: 'data-table-expand' },
      {
        text: 'Source',
        align: 'start',
        value: 'source'
      },
      { text: 'Name', value: 'name' },
      { text: 'Date', value: 'date' },
      { text: 'Conf.ID', value: 'confId' },
      { text: '', value: 'id' }
    ],
    data: [...DATA]
  })
}
</script>

<style lang="scss">
@import '~@/assets/main.scss';

.table-container {
  max-width: 600px;
  .my-table {
    border: 1px solid $color-border-grey;
    border-radius: 5px;

    .v-data-table-header {
      background-color: $color-bg-grey;
      color: $color-text-grey;
    }
    .v-data-table__expanded__content {
      box-shadow: unset !important;
    }
    .width-x {
      width: 100px;
    }
  }
}
.v-data-table td, .v-data-table th {
  padding: 0 5px !important;
}
</style>
