<template>
	<li>
		<img :src="video.snippet.thumbnails.default.url" />
		<h3>{{ video.snippet.title }}</h3>
	</li>
</template>

<script>
export default {
	name: 'VideoListItem',
	props: ['video'],
};
</script>

<style></style>
