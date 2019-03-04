<template>
    <div>
      <Navbar />
      <v-container grid-list-xs>
        <nuxt />
      </v-container>
    </div>
</template>

<script>
import Navbar from '~/components/Navbar';

export default {
  data() {
    return { }
  },
  components: {
    Navbar
  }
}
</script>

<style>

</style>
