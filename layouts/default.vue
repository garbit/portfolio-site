<template lang="pug">
div#app
  section#navbar
    .container
      b-navbar.is-spaced
        template(slot="brand")
          b-navbar-item.has-text-weight-medium(tag="router-link" :to="{ path: '/' }") Andy Garbett
        template(slot="end")
          b-navbar-item.has-text-weight-medium(href="/Andrew-Garbett-CV.pdf" target="_blank") CV
          b-navbar-item.has-text-weight-medium(href="#projects") Projects
          b-navbar-item.has-text-weight-medium(href="#publications") Publications
          b-navbar-item.has-text-weight-medium(href="#events") Events
          b-navbar-item.has-text-weight-medium(href="#contact") Contact

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

#navbar {
  box-shadow: 0 0 2px #e3e3e3;
}
</style>
