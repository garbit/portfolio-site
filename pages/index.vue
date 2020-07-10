<template lang="pug">
  div
    section
      .container.has-text-centered
        h1.title.is-size-3.is-family-primary {{ page.title }}
        h2.subtitle.is-size-6 {{ page.description }}
    hr
    .columns.is-mobile.is-centered
      .column.is-3-desktop.is-5-tablet.is-8-mobile
        figure.image
          img(:src="bio.photo")
    .columns.is-centered.has-text-centered
      .column.is-6
        nuxt-content(:document="bio")
    .columns.is-centered.has-text-centered
      .column.is-6
        a(:href="bio.cv" target="_blank")
          b-button.button.is-family-secondary.is-primary.is-rounded Curriculum Vitae
        hr

    section
      .columns
        .column.has-text-centered
          h3.title.is-size-4.is-family-primary Projects
</template>

<script>
export default {
  async asyncData ({ $content, error }) {
    try {
      const page = await $content('index').fetch()
      const bio = await $content('bio').fetch()
      return {
        page,
        bio
      }
    } catch (e) {
      error({ statusCode: 404, message: 'Page not found' })
    }
  }
}
</script>
