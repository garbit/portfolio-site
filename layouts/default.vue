<template lang="pug">
div#app
  b-navbar
    template(slot="brand")
      b-navbar-item(tag="router-link" :to="{ path: '/' }") Andy Garbett
    template(slot="start")
      b-navbar-item(href="#") Projects
      b-navbar-item(href="#") Publications
      b-navbar-item(href="#") Contact

  main
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
}
</script>

<style lang="scss">
</style>
