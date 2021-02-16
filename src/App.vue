<template>
  <div id="app">
    <div class="level-display-container">
      <level-display :value="value" avatar-src="avatar.jpg" />
    </div>

    <h1>value:{{value}}</h1>
    <input type="range" v-model="value" max="2600" />
    <input type="number" v-model="value" />
  </div>
</template>

<script>
import LevelDisplay from './components/LevelDisplay/LevelDisplay.vue'

export default {
  name: 'App',
  components: {
    LevelDisplay
  },
  data() {
    return {
      value: 1600
    };
  }
}
</script>

<style>
html, body {
  background: #f5f5f5;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.level-display-container {
  margin: 0 auto;
  width: 800px;
  padding: 16px;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  background: #fff;
}
</style>
