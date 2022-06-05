<template>
  <v-row dense>
    <template v-for="cat in cats">
      <cat-item :key="cat.uuid" :cat="cat" />
    </template>
  </v-row>
</template>

<script>
import CatItem from '~/components/CatItem.vue'
export default {
  components: {
    CatItem,
  },
  data() {
    return {
      cats: [],
    }
  },
  async created() {
    try {
      const response = await this.$axios.get(
        'https://livlog.xyz/webapi/cats.json'
      )
      this.cats = response.data.results
    } catch (err) {
      const res = err.response
      alert(res)
    }
  },
}
</script>

<style lang="scss" module>
.container {
  width: 100%;
}
</style>
