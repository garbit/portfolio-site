<template lang="pug">
//- div
  //- nav.navbar(role="navigation" aria-label="main navigation")
  //-   .navbar-brand
  //-     a.navbar-item(href="/") Andy Garbett
  //-     a.navbar-burger.burger(role="button" aria-label="menu" aria-expanded="false" data-target="mainNavbar")
  //-     span(aria-hidden="true")
  //-     span(aria-hidden="true")
  //-     span(aria-hidden="true")

  //-   #mainNavbar.navbar-menu
  //-     .navbar-start
  //-       a.navbar-item Projects
  //-       a.navbar-item Publications
  //-       a.navbar-item Contact

  //-   .navbar-end
  //-     .navbar-item
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
