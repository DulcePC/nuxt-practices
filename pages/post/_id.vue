<template>
<!-- Poniendole un _ antes del nombre la convierte ebn una ruta dinamica -->
  <div>
    <h1>{{post.title}}</h1>
    <p class="text-base text-blue-400">{{post.description}}</p>
  </div>
  
</template>

<script>
export default {
  data() {
    return {
      id: this.$route.params.id,
      // id al final es el nombre del archivo
      posts: [
        {
          id: 'Dulce',
          title: 'Dulce life',
          description: 'Dulce its just a little, little programmer developer...'
        },
        {
          id: 'Luis',
          title: 'Luis life',
          description: 'Luis its just a little, little hacker person...'
        }
      ]
    }
  },
  computed: {
    post() {
      return this.posts.find( post => post.id === this.id)
    }
  }
}
</script>

<style>

</style>