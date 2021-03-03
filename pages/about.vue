<template>
  <div>
    <h1>{{ title }}</h1>
    <nuxt-link to="/">Home</nuxt-link>
  </div>
</template>

<script>
export default {
  middleware : 'test',
  asyncData(){
    return { title: 'About'}
  },
  head(){
    return {
      title: this.title,
      script: [
        {src:'/about.js'}
      ]
    }
  }
}
</script>

<style>

</style>