<template>
  <v-app :dark="dark">
    <the-header/>

    <v-main>
      <v-container fluid>
        <router-view/>
      </v-container>
      <snackbar/>
    </v-main>

    <the-footer/>
  </v-app>
</template>

<script>
  import TheHeader from '@/components/App/TheHeader'
  import TheFooter from '@/components/App/TheFooter'
  import Snackbar from '@/components/Snackbar'
  import store from '@/store'
  import { computed } from '@vue/composition-api'
  import { vuexAccessors } from '@/helpers/store'

  export default {
    name: 'App',
    components: {
      TheHeader,
      TheFooter,
      Snackbar
    },
    setup () {
      const isConnected = computed(() => {
        return store.state.connection.instances.length > 0
      })

      const { dark } = vuexAccessors('theme', ['dark'])

      return {
        dark,
        isConnected
      }
    }
  }
</script>
