<script>
import Directory from './components/Directory.vue';

export default {
	name: 'app',
	components: {
		Directory,
	},
	data() {
		return {
			users: [],
		};
	},
	methods: {},
	created() {
		const url = 'https://randomuser.me/api/?results=50';
		fetch(url)
			.then((response) => response.json())
			.then((data) => (this.users = data.results));
	},
};
</script>

<template>
	<header>
		<h1>Our Members</h1>
	</header>

	<main>
		<Directory v-bind:users="users" />
	</main>
</template>

<style scoped></style>
