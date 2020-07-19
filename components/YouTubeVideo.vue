<template lang="pug">
  .video-container
    iframe(:src="url" allowfullscreen="allowfullscreen" width="854" height="480" frameborder="0")
</template>
<script>
export default {
  name: 'YouTubeVideo',
  props: {
    url: {
      type: String,
      required: true
    }
  }
}
</script>
<style lang="scss" scoped>
.video-container {
  position: relative;
  padding-bottom: 56.25%; /*16:9*/
  padding-top: 30px;
  height: 0;
  overflow: hidden;
  margin-top: 2rem;
}

.video-container iframe,
.video-container object,
.video-container embed {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
