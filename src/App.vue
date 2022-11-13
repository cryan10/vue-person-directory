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
		const url = 'https://randomuser.me/api/?page=1&results=10&seed=members';
		fetch(url)
			.then((response) => response.json())
			.then((data) => (this.users = data.results));
	},
};
</script>

<template>
	<div class="member-list" role="presentation">
		<h1 class="member-list__title">Our Members</h1>
		<main>
			<Directory v-bind:users="users" />
		</main>
	</div>
</template>

<style scoped lang="scss">
.member-list {
	display: flex;
	flex-direction: column;
	align-items: center;
	&__title {
		font-family: var(--fontStackAlt);
		color: var(--offWhite);
		font-size: 2.4rem;
		letter-spacing: 0.12rem;
	}
}
</style>
