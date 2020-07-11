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
      .column.is-10
        nuxt-content(:document="bio")
    .columns.is-centered.has-text-centered
      .column.is-6
        a(:href="bio.cv" target="_blank")
          b-button.button.is-family-secondary.is-primary.is-rounded Curriculum Vitae
        hr

    section
      .columns.is-centered
        .column.is-6.has-text-centered
          h3.title.is-size-4.is-family-primary Projects
          p The projects listed below are key projects that I have been involved in during my career at both the University of Lincoln and Newcastle University.
      .projects
        .project(v-for="(project, i) in projects" :key="project.title")
          .columns.reverse-columns
            .column
              h4.title.is-size-5.is-family-primary {{ project.title }}
              h5.subtitle.is-size-6.is-italic.is-family-primary {{ project.subtitle }}
              p {{ project.summary }}
            .column
              figure.image
                img(:src="project.photo")
          hr
</template>

<script>
export default {
  async asyncData ({ $content, error }) {
    try {
      const page = await $content('index').fetch()
      const bio = await $content('bio').fetch()
      const projects = await $content('projects').only(['title', 'subtitle', 'order', 'photo', 'summary']).sortBy('order').fetch()
      return {
        page,
        bio,
        projects
      }
    } catch (e) {
      error({ statusCode: 404, message: 'Page not found' })
    }
  }
}
</script>

<style lang="scss" scoped>
@media(max-width: 767px) { /* <== You can change this break point as per your  needs */
  .reverse-columns {
    flex-direction: column-reverse;
    display: flex;
    padding: 1.5rem;
  }

  .project {
    hr {
      margin: 0 auto 1.5rem;
      width: 45%;
    }
  }
}
@media(min-width: 768px) {
  .project {
    hr {
      margin: auto;
      width: 45%;
    }
    .columns {
      margin: 3rem 10%;
      .column {
        width: 50%;
      }
    }
  }

  .project:nth-child(even) {
    .columns {
      flex-direction: row-reverse;
    }
  }
}

.project:last-child {
  hr {
    display: none;
  }
}

// .projects .columns
</style>
