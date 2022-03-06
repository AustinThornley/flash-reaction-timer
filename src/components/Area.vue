<template>
	<div v-if="showArea" @click="stopTime" class="area">
		Click Me!
	</div>
</template>

<script>
export default {
	props: ['delay'],
	data() {
		return {
			showArea: false,
			time: null,
			reactionTime: 0
		}
	},
	methods: {
		startTime() {
			this.time = setInterval(() => {
				this.reactionTime += 10;
			}, 10);
		},
		stopTime() {
			clearInterval(this.time);
			this.$emit('stop', this.reactionTime);
		}
	},
	mounted() {
		setTimeout(() => {
			this.showArea = true;
			this.startTime();
		}, this.delay);
	}
}
</script>

<style>
.area {
	width: 400px;
	border-radius: 20px;
	background: green;
	color: white;
	text-align: center;
	padding: 100px 0;
	margin: 40px auto;
}
</style>