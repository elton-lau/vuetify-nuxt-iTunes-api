<template>
  <div>
    <h1 class="display-1">Hello from results route {{ $route.params.id }}</h1>
    <div v-if="albumExists">
      <div v-for="(album, id) in albumData">
        <card
          :title="album.collectionCensoredName"
          :image="album.artworkUrl100"
          :artistName="album.artistName"
          :url="album.artistViewUrl"
          :color="picker(index)"
        />
      </div>

    </div>
    <div v-else>
      <h1>Could not find Album</h1>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Card from '~/components/Card.vue'

export default {
  data() {
    index: 0
  },
  asyncData({params}) {
    return axios.get(`https://itunes.apple.com/search?term=${params.id}&entity=album`)
    .then((response) => {
      return {albumData: response.data.results}
    });
  },
  components: {
    Card
  },
  middleware: 'search',
  computed: {
    albumExists() {
      return this.albumData.length > 0;
    }
  },
  methods: {
    picker(index) {
      return index % 2 == 0 ? 'red' : 'blue'
    }
  }
}
</script>
