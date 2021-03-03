<template>
  <h1>{{ slug.post }}</h1>
</template>

<script>
export default {
  validate({ params }) {
    return /^\d+$/.test(params.post)
  },
  data() {
    return {
      slug : this.$route.params
    }
  }
}
</script>

<style>

</style>