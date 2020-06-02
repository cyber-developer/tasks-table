<template>
  <v-app>
    <v-content class="container pa-4">
      <MyTable />
    </v-content>
  </v-app>
</template>

<script>
import MyTable from '@/components/MyTable'

export default {
  name: 'App',

  components: {
    MyTable
  },

  data: () => ({
    //
  })
}
</script>
