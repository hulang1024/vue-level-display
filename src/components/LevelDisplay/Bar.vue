<template>
  <div class="bar">
    <div
      v-for="i in colors.length"
      :key="i"
      class="fill-bar"
      :class="{
        'fill': computedFillBarWidth(i - 1) == 100,
      }"
    >
      <div
        :style="{
          backgroundColor: colors[i - 1],
          width: `${computedFillBarWidth(i - 1)}%`,
        }"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    percentage: {
      type: Number,
      require: true
    },
    instantFeedback: {
      type: Boolean,
      default: false
    },
    colors: {
      type: Array,
      require: true
    },
  },
  data() {
    return {

    };
  },
  methods: {
    computedFillBarWidth(index) {
      const section = 16.666;// todo: 1000 / 6之后会有精度问题
      const fullNum = Math.floor(this.percentage / section);
      const mod = this.percentage % section;
      
      if (fullNum > index) {
        return 100;
      }
      if (mod > 0 && index == fullNum) {
        return mod / section * 100;
      } else {
        return 0;
      }
    }
  },
}
</script>

<style scoped>
.bar {
  display: flex;
  width: 100%;
  height: 16px;
  background: #f6f6f6;
  border-radius: 2px;
  border-style: inset;
  border-width: 1px;
}

.fill-bar {
  display: flex;
  flex-grow: 1;
  border-right: 1px solid rgba(0, 0, 0, 0.1);
  transition: all 0.15s ease;
}

.fill-bar:first-child,
.fill-bar:first-child > div {
  border-top-left-radius: inherit;
  border-bottom-left-radius: inherit;
}

.fill-bar.fill:last-child,
.fill-bar.fill:last-child > div {
  border-top-right-radius: inherit;
  border-bottom-right-radius: inherit;
}

.fill-bar:last-child {
  border-right: none;
}

.fill-bar:hover {
  opacity: 0.5;
}

.fill-bar.fill {
  border-right: none;
}
</style>