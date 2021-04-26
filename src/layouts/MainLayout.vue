<template>

  <q-layout view="lHh Lpr lFf">

    <q-header elevated>

      <q-toolbar>
        <q-toolbar>
      
        <q-toolbar-title>
          Syafiq Basri
        </q-toolbar-title>

        <div>Today is {{ todaysDate }}</div>

      </q-toolbar>
    
      </q-toolbar>

    </q-header>

    <q-page-container>
      <keep-alive>
         <router-view />
      </keep-alive>
    </q-page-container>

  </q-layout>

</template>

<script>
import { date } from 'quasar'

export default {
  name: 'MainLayout',
  components: { },
  data () {
    return {
     
    }
  }, 

  computed: {
    todaysDate() {
      let timeStamp = Date.now()
      return date.formatDate(timeStamp, 'dddd D MMMM')
    }
  }
}

</script>
