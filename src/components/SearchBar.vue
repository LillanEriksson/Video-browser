<template>
	<div>
		<input @input="onInput" />
	</div>
</template>

<script>
export default {
	name: 'SearchBar',
	methods: {
		onInput() {
			this.$emit('termChange', event.target.value);
		},
	},
};
</script>

<style></style>
