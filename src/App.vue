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
			currentPage: 1,
		};
	},
	methods: {
		goToNextPage() {
			this.currentPage++;
			const url = `https://randomuser.me/api/?page=${this.currentPage}&results=10&seed=members`;
			fetch(url)
				.then((response) => response.json())
				.then((data) => (this.users = data.results));
		},
		goToPreviousPage() {
			this.currentPage--;
			const url = `https://randomuser.me/api/?page=${this.currentPage}&results=10&seed=members`;
			fetch(url)
				.then((response) => response.json())
				.then((data) => (this.users = data.results));
		},
	},
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
		<div role="presentation">
			<button
				@click="goToPreviousPage"
				:disabled="currentPage === 1"
				class="member-list__button"
			>
				Back
			</button>
			<button
				@click="goToNextPage"
				:disabled="currentPage === 500"
				class="member-list__button m--next"
			>
				Next
			</button>
		</div>
	</div>
</template>

<style scoped lang="scss">
.member-list {
	display: flex;
	flex-direction: column;
	align-items: center;
	&__title {
		font-family: var(--fontStackAlt);
		color: var(--primary);
		font-size: 2.4rem;
	}
	&__button {
		background-color: var(--accent);
		font-family: var(--fontStackAlt);
		color: var(--black);
		border: none;
		border-radius: 4px;
		box-shadow: 1px 1px 2px var(--box-shadow);
		padding: 0.8rem 2.4rem;
		font-size: 1.2rem;
		&:disabled {
			opacity: 0.5;
		}
		&.m {
			&--next {
				margin-left: 2rem;
			}
		}
	}
}
</style>
