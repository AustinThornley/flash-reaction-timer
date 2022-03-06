<template>
	<p><span class="score-text">Reaction Time</span>: {{ score }} milliseconds</p>
	<p class="small">Great job! 🎉 Click the button to try again!</p>
</template>

<script>
export default {
	props: ['score'],
}
</script>

<style>
.small {
	font-size: 75%;
}

.score-text {
	color: green;
	font-weight: bold;
}
</style>