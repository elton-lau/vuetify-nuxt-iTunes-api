<template>
  <div class="text-xs-center">
    <h1 class="pt-4 display-1">Search iTunes</h1>
    <br />

    <v-form @submit.prevent="OnSubmit">
      <v-text-field
            v-model="search"
            label="Enter Artist Name"
          ></v-text-field>
    </v-form>
  </div>
</template>


<script>
export default {
  components:{

  },
  data() {
    return {
      search: ''
    }
  },
  methods: {
    OnSubmit(event) {
      this.$router.push(`results/${this.search}`)
    }
  }
}
</script>

<style>
</style>
