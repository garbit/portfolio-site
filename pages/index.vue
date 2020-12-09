<template lang="pug">
  div
    section.section
      .container.has-text-centered
        h1.title.is-size-3.is-family-primary {{ page.title }}
        h2.subtitle.is-size-6.is-size-7-mobile Software Engineer / Interaction Designer / UX Researcher

    hr.small

    section.section.is-small
      .container
        .columns.is-mobile.is-centered
          .column.is-3-desktop.is-5-tablet.is-8-mobile
            figure.image
              img(:src="bio.photo")
        .columns.is-centered.has-text-centered
          .column.is-8
            h2.title.is-size-5.is-family-primary {{ page.description }}
            nuxt-content(:document="bio")
        .columns.is-centered.has-text-centered
          .column.is-6
            a(:href="bio.cv" target="_blank")
              b-button.button.is-family-secondary.is-primary.is-rounded.has-text-weight-medium Curriculum Vitae

    hr.small

    Projects(:projects="projects")

    hr.small

    section.section
      .container
        .columns.is-centered
          .column.is-10
            h3.title.is-size-4.is-family-primary Ph.D. Thesis
            p.is-size-5.is-family-primary
              span.has-text-weight-semibold Designing Community Driven Participatory Platforms
              span.is-italic : Reconfiguring Roles, Resources, Infrastructure, and Constraints for Community Commissioning.
            br
            p.has-text-weight-medium.is-family-primary Ph.D. Computing Science (Human-Computer Interaction)
            p.is-family-primary Open Lab, School of Computing Science, Newcastle Unviersity, 2017. #{' '}
              span (
                span
                  nuxt-link(to="/publications/Community Commissioning Designing Platforms to Support Community Driven Information Systems.pdf" target="_blank") pdf
              span )
            .content
              ul
                li Launched an online platform that enables communities to collaboratively design and automatically generate location-based review mobile apps resulting in ~125,000 users and 24 mobile applications.
                li Explored the design of tools, platforms, and services to maximize reach and depth of citizen participation in the generation of community-driven information resources.

    hr.small

    section.section
      .container
        .columns.is-centered.is-multiline
          .column.is-10
            h3.title.is-size-4.is-family-primary Recent Talk
            h4.is-size-5.has-text-weight-semibold.is-family-primary ThinkActive: Designing for Pseudonymous Activity Tracking in the Classroom
            p Andrew Garbett, David Chatting, Gerard Wilkinson, Clement Lee, Ahmed Kharrufa. In Proc. CHI 2018. ACM.
          .column.is-10
            YouTubeVideo(url="https://www.youtube.com/embed/mVZT5GWgdjE")

    hr.small

    Publications(:publicationsList="publicationsList")

    hr.small

    Events(:eventList="eventList")

    hr.small

    section#contact.section
      .container
        .columns.is-centered.is-multiline.has-text-centered
          .column.is-10
            h3.title.is-size-4.is-family-primary Contact
          .column.is-10
            h4.is-size-5.is-family-primary a.garbett@samsung.com
            p.is-family-primary
              a(href="https://twitter.com/garbit" target="_blank") @garbit
</template>

<script>
import Projects from '@/components/Projects'
import YouTubeVideo from '@/components/YouTubeVideo'
import Publications from '@/components/Publications'
import Events from '@/components/Events'
import PublicationsList from '@/content/publications.json'
import EventList from '@/content/events.json'

export default {
  components: {
    Projects,
    YouTubeVideo,
    Publications,
    Events
  },
  async asyncData ({ $content, error }) {
    try {
      const page = await $content('index').fetch()
      const bio = await $content('bio').fetch()
      const projects = await $content('projects').sortBy('order').fetch()
      // const publications = await $content('publications').sortBy('year').fetch()
      const publications = PublicationsList
      const publicationYears = [...new Set(publications.map(p => p.year))].sort().reverse()
      const publicationsList = []
      publicationYears.forEach((year) => {
        publicationsList.push({
          year,
          publications: publications.filter(p => p.year === year)
        })
      })

      const events = EventList
      const eventYears = [...new Set(events.map(e => e.year))].sort().reverse()
      const eventList = []
      eventYears.forEach((year) => {
        eventList.push({
          year,
          events: events.filter(e => e.year === year)
        })
      })
      return {
        page,
        bio,
        projects,
        publicationsList,
        eventList
      }
    } catch (e) {
      error({ statusCode: 404, message: 'Page not found' })
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
