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
    }
  },
  computed: {
    post() {
      return this.$store.state.posts.all.find( post => post.id === this.id);
    },
    relatedPosts () {
      return this.$store.state.posts.all.filter(post => post.id !== this.id);
    }
  },
  head () {
    return {
      title: this.post.title,
      meta: [
        { name: 'twitter:title', content: 'Nuxt Fundamentals by Vue School'},
        { name: 'twitter:description', content: 'test'},
        { name: 'twitter:image', content: 'https://i.imgur.com/UYP2umJ.png'},
        { name: 'twitter:card', content: 'summary_large_image'}
      ]
    }
  }
}
</script>

<style>

</style>