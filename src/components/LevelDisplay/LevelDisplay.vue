<template>
  <div>
    <div class="bar-row">
      <avatar
        :src="avatarSrc"
        size="60px"
        :style="{left: `calc(${percentage}% - 30px)`}"
      />
      <div class="mark-line" :style="{left: `${percentage}%`}"></div>
      <bar :colors="barColors" :percentage="percentage" />
    </div>
    <div class="level-tag-row">
      <div
        v-for="(level, n) in levels"
        :key="n"
        class="level-col"
      >
        <div
          class="level-tag"
          :style="{
            backgroundColor: level.color
          }"
        >V{{n}}</div>
        <div class="level-value">{{level.value}}</div>
      </div>
    </div>
  </div>
</template>

<script>
import Bar from './Bar.vue';
import Avatar from './Avatar.vue';

export default {
  props: {
    avatarSrc: {
      type: String,
      require: true
    },
    value: {
      type: Number,
      require: true
    }
  },
  components: {
    Bar,
    Avatar
  },
  data() {
    this.levels = [
      {value: 0, color: '#e1e1e1'},
      {value: 30, color: '#fdeac0'},
      {value: 140, color: '#f9dc8e'},
      {value: 400, color: '#fc9532'},
      {value: 800, color: '#f44425'},
      {value: 1600, color: '#fb57e2'},
      {value: 2600, color: '#b917cc'}
    ];
    this.maxValue = this.levels[this.levels.length - 1].value;

    return {

    };
  },
  computed: {
    barColors() {
      return this.levels.map(lv => lv.color).slice(1);
    },
    percentage() {
      return this.value / this.maxValue * 100;
    },
  },

}
</script>

<style scoped>
.bar-row {
  padding: 0px 15px;
  margin-bottom: 6px;
}

.avatar,
.mark-line {
  position: relative;
  left: 0px;
  transition: left 0.3s ease;
}

.avatar {
  margin-bottom: 4px;
  box-shadow: 0 0 2px 1px rgba(0, 0, 0, 0.2);
}

.mark-line {
  margin-bottom: 4px;
  width: 1px;
  height: 24px;
  border-right: 1px dashed rgba(0, 0, 0, 0.3);
  box-sizing: border-box;
}

.level-tag-row {
  display: inline-flex;
  justify-content: space-between;
  width: 100%;
}

.level-tag {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 12px;
  padding: 1px 4px;
  width: 32px;
  border-radius: 4px;
  color: #fff;
  font-size: 14px;
  font-weight: 500;
  user-select: none;
  box-sizing: border-box;
  box-shadow: 1px 1px 1px 0px rgba(0, 0, 0, 0.1);
  text-shadow: 1px 1px rgba(0, 0, 0, 0.1);
  transition: all 0.15s ease;
}

.level-tag:hover {
  opacity: 0.5;
}

.level-value {
  font-size: 14px;
  user-select: none;
}
</style>