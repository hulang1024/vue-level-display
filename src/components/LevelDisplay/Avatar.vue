<template>
  <div
    class="avatar"
    :style="{width: this.size, height: this.size}"
  >
    <img :src="src" />
  </div>
</template>

<script>
export default {
  props: {
    src: {
      type: String,
      require: true
    },
    size: {
      type: [Number, String],
      default: '50px'
    }
  }
}
</script>

<style scoped>
.avatar {
  border-radius: 100%;
}

.avatar > img {
  object-fit: cover;
  border-radius: inherit;
  height: inherit;
  width: inherit;
}
</style>