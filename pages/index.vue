<template>
  <div>
    <section class="section hero is-primary">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">
            {{ page.title }}
          </h1>
          <h2 class="subtitle">
            {{ page.description }}
          </h2>
        </div>
      </div>
    </section>
    <section class="section">
      <div class="container">
        <nuxt-content :document="page" />
      </div>
    </section>
  </div>
</template>

<script>

export default {
  async asyncData ({ $content, error }) {
    try {
      const page = await $content('index').fetch()
      return {
        page
      }
    } catch (e) {
      error({ statusCode: 404, message: 'Page not found' })
    }
  }
}
</script>
