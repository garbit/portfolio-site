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
    .container.has-text-centered
      p.has-text-weight-semibold 💡 + 🎨 + 🛠️
      p.has-text-weight-light Crafted by #{' '}
      p.has-text-weight-semibold Andy Garbett

</template>

<script>

export default {
}
</script>

<style lang="scss">
.footer {
  padding: 3rem;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}
</style>
