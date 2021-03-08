<template>
	<li @click="onVideoSelect">
		<img :src="video.snippet.thumbnails.default.url" />
		<div class="title">
			<h3>{{ video.snippet.title }}</h3>
		</div>
	</li>
</template>

<script>
export default {
	name: 'VideoListItem',
	props: ['video'],
	methods: {
		onVideoSelect() {
			this.$emit('videoSelect', this.video);
		},
	},
};
</script>

<style scoped>
li {
	display: flex;
	border: 1px solid #457b9d;
	margin: 7px;
	cursor: pointer;
}

li:hover {
	background-color: #a8dadc;
}

h3 {
	margin: 10px;
}

.title {
	display: flex;
	flex-wrap: wrap;
}
</style>
