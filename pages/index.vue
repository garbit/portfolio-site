<template lang="pug">
  div
    section
      .container.has-text-centered
        h1.title.is-size-3.is-family-primary {{ page.title }}
        h2.subtitle.is-size-6 Software Engineer / Interaction Designer / UX Researcher
    hr
    .columns.is-mobile.is-centered
      .column.is-3-desktop.is-5-tablet.is-8-mobile
        figure.image
          img(:src="bio.photo")
    .columns.is-centered.has-text-centered
      .column.is-10
        h2.title.is-size-5.is-family-primary {{ page.description }}
        nuxt-content(:document="bio")
    .columns.is-centered.has-text-centered
      .column.is-6
        a(:href="bio.cv" target="_blank")
          b-button.button.is-family-secondary.is-primary.is-rounded Curriculum Vitae
        hr

    projects(:projects="projects")

    .columns.is-centered
      .column.is-6
        hr

    section.section
      .container
        .columns.is-centered
          .column.is-10
            h3.title.is-size-4.is-family-primary Ph.D. Thesis
            p.is-size-5.is-family-primary
              span.has-text-weight-semibold Designing Community Driven Participatory Platforms
              span.is-italic : Reconfiguring Roles, Resources, Infrastructure, and Constraints for Community Commissioning.
            br
            p.has-text-weight-medium.is-family-primary Ph.D. Computing Science (Human-Computer Interaction), School of Computing Science, Newcastle Unviersity.
            .content
              ul
                li Explored the design of tools, platforms, and services to maximize reach and depth of citizen participation in the generation of community-driven information resources.
                li Launched an online platform that enables communities to collaboratively design and automatically generate location-based review mobile apps resulting in ~125,000 users and 24 mobile applications.

    .columns.is-centered
      .column.is-6
        hr.small

    section.section
      .container
        .columns.is-centered.is-multiline
          .column.is-10
            h3.title.is-size-4.is-family-primary Recent Talk
            h4.is-size-5.has-text-weight-semibold.is-family-primary ThinkActive: Designing for Pseudonymous Activity Tracking in the Classroom
            p Andrew Garbett, David Chatting, Gerard Wilkinson, Clement Lee, Ahmed Kharrufa. In Proc. CHI 2018. ACM.
          .column.is-10
            .video-container
              iframe(src="https://www.youtube.com/embed/mVZT5GWgdjE" allowfullscreen="allowfullscreen" width="854" height="480" frameborder="0")

    .columns.is-centered
      .column.is-6
        hr.small

    section.section
      .container
        .columns.is-centered.is-multiline
          .column.is-10
            h3.title.is-size-4.is-family-primary Publications
            p Full publication list can be found on Google Scholar
        .columns.is-centered.is-multiline
          .publication.column.is-10(v-for="(publication, i) in publications" :key="publication.title")
            h4.is-size-5.has-text-weight-semibold.is-family-primary {{ publication.title }}
            p.is-size-6
              span(v-for="(author, index) in publication.authors" :class="isMainAuthor(author)") {{ author }}
                span(v-if="index < (publication.authors.length - 1)") , #{' '}
            p.is-size-6 {{ publication.proceedings }}. {{ publication.publisher }}.

    .columns.is-centered
      .column.is-6
        hr.small

    section.section
      .container
        .columns.is-centered.is-multiline.has-text-centered
          .column.is-10
            h3.title.is-size-4.is-family-primary Contact
          .column.is-10
            p a.garbett@samsung.com
            p @garbit
</template>

<script>
import Projects from '@/components/Projects'
import Publications from '@/content/publications.json'

export default {
  components: {
    Projects
  },
  data: () => {
    return {
      author: 'Andrew Garbett'
    }
  },
  methods: {
    isMainAuthor (author) {
      if (author === this.author) {
        return 'has-text-weight-medium'
      }
      return false
    }
  },
  async asyncData ({ $content, error }) {
    try {
      const page = await $content('index').fetch()
      const bio = await $content('bio').fetch()
      const projects = await $content('projects').only(['title', 'subtitle', 'order', 'photo', 'summary']).sortBy('order').fetch()
      // const publications = await $content('publications').sortBy('year').fetch()
      const publications = Publications
      return {
        page,
        bio,
        projects,
        publications
      }
    } catch (e) {
      error({ statusCode: 404, message: 'Page not found' })
    }
  }
}
</script>

<style lang="scss" scoped>
.video-container {
  position: relative;
  padding-bottom: 56.25%; /*16:9*/
  padding-top: 30px;
  height: 0;
  overflow: hidden;
  margin-top: 2rem;
}

.video-container iframe,
.video-container object,
.video-container embed {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

</style>
