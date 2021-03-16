<template>
<!-- Poniendole un _ antes del nombre la convierte ebn una ruta dinamica -->
  <div class="h-screen mt-10">
    <div class="grid grid-cols-2 px-12">
      <div>
        <h1>{{post.title}}</h1>
        <p class="text-base text-blue-400">{{post.description}}</p>
      </div>
      <aside>
        <h4>Post you might enjoy</h4>
        <ul class="bg-blue-100 pl-3">
          <li v-for="related in relatedPosts">
            <nuxt-link :to="`/post/${related.id}`">{{related.title}}</nuxt-link>
          </li>
        </ul>
      </aside>
    </div>
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
      return this.posts.find( post => post.id === this.id);
    },
    relatedPosts () {
      return this.posts.filter(post => post.id !== this.id);
    }
  }
}
</script>

<style>

</style>