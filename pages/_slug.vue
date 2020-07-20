<template lang="pug">
  div
    section.section.is-small
      .container.has-text-centered
        h1.title.is-size-3.is-family-primary Andrew Garbett
        h2.subtitle.is-size-6 Software Engineer / Interaction Designer / UX Researcher

    hr.small

    section.section
      .container
        .columns.is-centered.is-multiline
          .column.is-8
            h4.title.is-size-2.is-family-primary {{ project.title }}
            h5.subtitle.is-size-5.is-italic.is-family-primary {{ project.subtitle }}
            p {{ project.summary }}
          .column.is-8
            nuxt-content(:document="project")
          .column.is-12.has-text-centered
            a(:href="project.url" target="_blank")
              button.button.is-primary View Project
</template>

<script>
export default {
  async asyncData ({ $content, params, error }) {
    const slug = params.slug
    try {
      const project = await $content('projects', slug).fetch()
      return {
        project
      }
    } catch (e) {
      error({ statusCode: 404, message: 'Page not found' })
    }
  }
}
</script>
