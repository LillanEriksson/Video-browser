<template>
	<div>
		<SearchBar @termChange="onTermChange"></SearchBar>
		<VideoDetail :video="selectedVideo"></VideoDetail>
		<VideoList v-bind:videos="videos" @videoSelect="onVideoSelect"></VideoList>
	</div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from '@/components/VideoDetail';

const API_KEY = 'AIzaSyCA8XOfs8AtnNifuj4XXXRpbseiUhxKTDw';
export default {
	name: 'App',
	components: { SearchBar, VideoList, VideoDetail },
	data() {
		return { videos: [], selectedVideo: null };
	},
	methods: {
		onTermChange(searchTerm) {
			axios
				.get('https://www.googleapis.com/youtube/v3/search', {
					params: {
						key: API_KEY,
						type: 'video',
						part: 'snippet',
						q: searchTerm,
					},
				})
				.then((res) => {
					this.videos = res.data.items;
				});
		},
		onVideoSelect(video) {
			this.selectedVideo = video;
		},
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
