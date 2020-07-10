<template lang="pug">
  div
    div(v-html="$md.render(bio)")
</template>
<script>
export default {
  name: 'Bio',
  props: {
    bio: {
      type: String,
      required: true
    }
  }
}
</script>
