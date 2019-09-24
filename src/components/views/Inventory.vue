<template>
      <div v-if="!loading" class = "row">
        <div v-for="(item,index) in items" :key="index" class="card" style="width: 14rem;">
          <router-link :to="{ path: '/item/' + item.id }" tag="div">
          <img class="card-img-top" :src="item.photo" alt="Card image cap">
          <div class="card-body">
            <h5 class="card-title text-center">{{ item.title }}</h5>
          </div>
          </router-link>
          <div class="card-footer">
            <span class="card-text">${{ item.price }}</span>
            <a @click="addToCart(item)" class="btn btn-primary float-right">+Add</a>
          </div>
        </div>
      </div>
      <h1 v-else>Loading...</h1>
</template>

<script>
import axios from 'axios'

export default {
  // props: ['items'],
  data() {
    return {
      loading: true,
      items: []
    }
  },
  mounted() {
    this.fetchInventory()
  },
  methods: {
    addToCart(item) {
      this.$store.commit('addToCart', item)
    },
    fetchInventory() {
      var self = this
      axios.get('http://localhost:3000/items').then(Response => {
        self.items = Response.data
        self.loading = false
      })
    }
  }
}
</script>

<style>

</style>
