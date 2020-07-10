<template lang="pug">
  div
    section.section.hero
      .hero-body
        .container.has-text-centered
          h1.title.is-family-primary {{ page.title }}
          h2.subtitle {{ page.description }}

    section.section
      .container
        nuxt-content(:document="page")
</template>

<script>

export default {
  async asyncData ({ $content, error }) {
    try {
      const page = await $content('index').fetch()
      return {
        page
      }
    } catch (e) {
      error({ statusCode: 404, message: 'Page not found' })
    }
  }
}
</script>
