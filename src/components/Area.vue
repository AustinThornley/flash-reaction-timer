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
	transition: 0.4s all;
	cursor: pointer;
}

.area:hover {
	transition: 0.4s all;
	background: #007300;
}

/* Mobile Styles */
@media only screen and (max-width: 750px) {
	.area {
		max-width: 300px;
	}
}

@media only screen and (max-width: 575px) {
	.area {
		max-width: 200px;
	}
}
</style>