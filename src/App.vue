<script>
import pageHeader from './components/pageHeader.vue'
import pageContent from './components/pageContent.vue'
import pageFooter from './components/pageFooter.vue'
import axios from 'axios'
import { store } from './store'

export default {
  data() {
    return {
      store
    }
  },
  components: {
    pageHeader: pageHeader,
    pageContent,
    pageFooter
  },
  created() {
    axios
      .get('http://localhost:3000/products')
      .then((res) => {
        const productsDb = res.data
        this.store.products = productsDb
        console.log(this.store.products)

      })
  }
}
</script>

<template>
  <pageHeader />
  <pageContent />
  <pageFooter />
</template>

<style lang="scss">
@use './styles/general.scss'
</style>
