<template lang="pug">
  section#events.section
    .container
      .columns.is-centered.is-multiline
        .column.is-10
          h3.title.is-size-4.is-family-primary Conferences & Events
      .columns.is-centered.is-multiline
        .event.column.is-10(v-for="(year, i) in eventList")
          p.is-size-5.has-text-weight-semibold.is-family-primary {{ year.year }}
          ul(v-for="(event, i) in year.events")
            li
              p.is-family-primary.is-hidden-mobile {{ event.month }} - {{ event.name }}, {{ event.location }}
            li
              p.is-family-primary.is-hidden-tablet {{ event.name }}
</template>
<script>
export default {
  name: 'Events',
  props: {
    eventList: {
      type: Array,
      required: true
    }
  }
}
</script>
<style lang="scss" scoped>
</style>
