<template>
	<div v-if="video" class="video-container">
		<div class="iframe-container">
			<iframe class="embedded-video" :src="videoUrl" />
		</div>
		<div class="details">
			<h4>{{ video.snippet.title }}</h4>
			<p>{{ video.snippet.description }}</p>
		</div>
	</div>
</template>

<script>
export default {
	name: 'VideoDetail',
	props: ['video'],
	computed: {
		videoUrl() {
			const { videoId } = this.video.id;
			return `https://www.youtube.com/embed/${videoId}`;
		},
	},
};
</script>

<style scoped>
.video-container {
	max-width: 75%;
}

.iframe-container {
	position: relative;
	overflow: hidden;
	width: 100%;
	padding-top: 56.25%;
}

.embedded-video {
	position: absolute;
	top: 0;
	left: 0;
	bottom: 0;
	right: 0;
	width: 100%;
	height: 100%;
}

.details {
	padding: 10px;

	border: 1px solid #457b9d;
}
</style>
