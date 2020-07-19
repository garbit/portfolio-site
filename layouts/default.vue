<template lang="pug">
div
  b-navbar
    template(slot="brand")
      b-navbar-item(tag="router-link" :to="{ path: '/' }") Andy Garbett
    template(slot="start")
      b-navbar-item(href="#") Projects
      b-navbar-item(href="#") Publications
      b-navbar-item(href="#") Contact

  section.main-content
    .container
      nuxt
  footer.footer
    .container
      .columns
        .column.has-text-centered
          p Crafted by Andy Garbett
</template>

<script>

export default {
  data () {
    return {
      items: [
        {
          title: 'Home',
          icon: 'home',
          to: { name: 'index' }
        },
        {
          title: 'Inspire',
          icon: 'lightbulb',
          to: { name: 'inspire' }
        }
      ]
    }
  }
}
</script>

<style lang="scss">
</style>
