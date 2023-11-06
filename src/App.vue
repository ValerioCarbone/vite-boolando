<script>
import pageHeader from './components/pageHeader.vue'
import pageContent from './components/pageContent.vue'
import pageFooter from './components/pageFooter.vue'

export default {
  components: {
    pageHeader: pageHeader,
    pageContent,
    pageFooter
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
