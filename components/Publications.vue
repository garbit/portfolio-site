<template lang="pug">
  section#publications.section
    .container
      .columns.is-centered.is-multiline
        .column.is-10
          h3.title.is-size-4.is-family-primary Publications
          p Full publication list can be found on #{' '}
            a(href="https://scholar.google.co.uk/citations?user=4N-DHfgAAAAJ") Google Scholar
            span .
      .year.columns.is-centered.is-multiline(v-for="(year, i) in publicationsList")
        .column.is-10
          p.is-size-5.has-text-weight-semibold.is-family-primary {{ year.year }}
        .column.is-10(v-for="(publication, i) in year.publications")
          h4.is-size-5.has-text-weight-medium.is-family-primary {{ publication.title }}
          p.is-size-6
            span(v-for="(author, index) in publication.authors" :class="isMainAuthor(author)") {{ author }}
              span(v-if="index < (publication.authors.length - 1)") , #{' '}
          p {{ publication.proceedings }}. {{ publication.publisher }}. #{' '}
            span (
              nuxt-link(:to="publication.link" target="_blank") pdf
            span )
</template>
<script>
export default {
  name: 'Publications',
  props: {
    publicationsList: {
      type: Array,
      required: true
    }
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
  }
}
</script>
<style lang="scss" scoped>
.year {
  margin-bottom: 1.5rem
}

.year:last-child {
  margin-bottom: 0;
}
</style>
