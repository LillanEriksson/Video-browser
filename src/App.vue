<template>
	<div>
		<SearchBar @termChange="onTermChange"></SearchBar>
		<VideoList v-bind:videos="videos"></VideoList>
	</div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
const API_KEY = 'AIzaSyCA8XOfs8AtnNifuj4XXXRpbseiUhxKTDw';
export default {
	name: 'App',
	components: { SearchBar, VideoList },
	data() {
		return { videos: [] };
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
					console.log(res);
					this.videos = res.data.items;
				});
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
