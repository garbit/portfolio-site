<template>
  <article>
    <h1>{{ blogPost.title }}</h1>
    <div v-html="$md.render(blogPost.body)" />
  </article>
</template>

<script>
export default {
  // async asyncData ({ params, payload }) {
  //   if (payload) {
  //     return { blogPost: payload }
  //   }

  //   return {
  //     blogPost: null
  //   }
  // }
}
</script>
