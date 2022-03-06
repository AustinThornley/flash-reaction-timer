<template>
	<div class="game">
			<h1 v-show="!isPlaying"><span class="flash">Flash! - </span> Reaction Timer</h1>
			<button @click="init" v-if="!isPlaying && !gameEnded">Start Game</button>
			<button @click="restart" v-if="!isPlaying && gameEnded">Restart Game</button>
			<Area v-if="isPlaying" :delay="delay" @stop="stop"/>
			<!-- To-Do: convert score from ms to seconds -->
			<Stats v-if="gameEnded" :score="score"></Stats>
	</div>
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
		stop(reactionTime) {
			this.score = reactionTime;
			this.isPlaying = false;
			this.gameEnded = true;
		},
		restart() {
			location.reload();
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
	display: flex;
	justify-content: center;
}
.game {
	background: rgb(199, 199, 199);
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	min-height: 450px;
	min-width: 679px;
}
h1 {
	font-size: 2.5rem;
	padding: 0 5rem 1rem 5rem;
}
.flash {
	color: green;
	font-style: italic;
	font-size: 150%;
}
button {
	font-family: inherit;
	font-size: .95rem;
	background: green;
	color: white;
	border: none;
	border-radius: 11px;
	padding: 1rem;
	cursor: pointer;
	transition: 0.4s all;
	overflow: hidden;
	max-width: 25%;
	margin: 0 auto;
	margin-bottom: 5rem;
}
button:hover {
	transform: translateY(-3px);
	transition: 0.4s all;
	background: #007300;
}
@media only screen and (max-width: 750px) {
	h1 {
		padding: 0 1rem .5rem 1rem;
	}
	.game {
		min-width: 400px;
	}
}
@media only screen and (max-width: 575px) {
	h1 {
		font-size: 1.25rem;
		padding: 0;
	}
	button {
		font-size: .75rem;
		padding: .75rem;
	}
	.game {
		min-width: 300px;
	}
}
</style>
