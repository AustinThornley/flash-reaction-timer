<template>
	<h1><span class="flash">Flash! - </span> Reaction Timer</h1>
	<button @click="init" :disabled="isPlaying">Start Game</button>
	<Area v-if="isPlaying" :delay="delay" @stop="stopGame"/>
	<!-- To-Do: convert score from ms to seconds -->
	<Stats v-if="gameEnded" :score="score"></Stats>
</template>

<script>
import Area from './components/Area.vue';
import Stats from './components/Stats.vue';

export default {
  name: 'App',
  components: { Area, Stats },
	data() {
		return {
			isPlaying: false,
			gameEnded: false,
			delay: null,
			score: null,
		}
	},
	methods: {
		init() {
			this.delay = 2000 + Math.random() * 5000;
			this.isPlaying = true;
		},
		stopGame(reactionTime) {
			this.score = reactionTime;
			this.isPlaying = false;
			this.gameEnded = true;
		}
	},
	mounted() {
		document.title = 'Flash! - Reaction Timer';
	}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto+Slab:wght@400;500;700&display=swap');

#app {
  font-family: 'Roboto Slab', serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
.flash {
	color: green;
	font-style: italic;
	font-size: 150%;
}
</style>
