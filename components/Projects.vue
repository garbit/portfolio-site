<template lang="pug">
  section.section.is-small
    .container
      .columns.is-centered
        .column.is-6.has-text-centered
          h3.title.is-size-4.is-family-primary Research Projects
          p The projects listed below are technologies that I designed and developed as part of my research at University of Lincoln and Newcastle University.
      .projects
        .project(v-for="(project, i) in projects" :key="project.title")
          .columns.reverse-columns
            .column
              h4.title.is-size-5.is-family-primary {{ project.title }}
              h5.subtitle.is-size-6.is-italic.is-family-primary {{ project.subtitle }}
              p {{ project.summary }}
              p.more
                nuxt-link(:to="project.slug")
                  p.title.is-size-6.is-family-primary Read more
            .column
              figure.image
                img(:src="project.photo")
          hr
</template>
<script>
export default {
  name: 'Projects',
  props: {
    projects: {
      type: Array,
      required: true
    }
  }
}
</script>
<style lang="scss" scoped>
@media(max-width: 767px) { /* <== You can change this break point as per your  needs */
  .reverse-columns {
    flex-direction: column-reverse;
    display: flex;
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

.more {
  margin-top: 1.5rem;
  text-decoration: underline;
}

.more:hover {
  color: hsl(0, 0%, 86%);
}
</style>
