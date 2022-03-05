<template>
	<h1>Reaction Timer</h1>
	<button @click="init" v-show="!isPlaying">Start Game</button>
	<Area v-show="isPlaying" :delay="delay" />
</template>

<script>
import Area from './components/Area.vue';

export default {
  name: 'App',
  components: { Area },
	data() {
		return {
			delay: null,
			isPlaying: false
		}
	},
	methods: {
		init() {
			this.delay = 2000 + Math.random() * 5000;
			this.isPlaying = true;
		}
	}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
