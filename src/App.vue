<script>
import pageHeader from './components/pageHeader.vue'
import pageContent from './components/pageContent.vue'

export default {
  components: {
    pageHeader: pageHeader,
    pageContent
  }
}
</script>

<template>
  <pageHeader />
  <pageContent />
</template>

<style lang="scss">
@use './styles/general.scss'
</style>
