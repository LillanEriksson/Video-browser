<template>
	<ul>
		<VideoListItem
			v-for="video in videos"
			:video="video"
			:key="video.etag"
			@videoSelect="onVideoSelect"
		>
		</VideoListItem>
	</ul>
</template>

<script>
import VideoListItem from '@/components/VideoListItem';
export default {
	name: 'VideoList',
	components: { VideoListItem },
	props: ['videos'],
	methods: {
		onVideoSelect(video) {
			this.$emit('videoSelect', video);
		},
	},
};
</script>

<style>
ul {
	list-style-type: none;
	width: 20%;
}
</style>
