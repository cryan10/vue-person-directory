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
			isFetchingUsers: false,
		};
	},
	methods: {
		getUsers(currentPage) {
			this.isFetchingUsers = true;
			const url = `https://randomuser.me/api/?page=${currentPage}&results=10&seed=members&inc=gender,name,location,email,phone,id,picture,dob`;
			fetch(url)
				.then((response) => response.json())
				.then((data) => (this.users = data.results))
				.then(() => (this.isFetchingUsers = false))
				.then(() => window.scrollTo(0, 0));
		},
		goToNextPage() {
			this.currentPage++;
			this.getUsers(this.currentPage);
		},
		goToPreviousPage() {
			this.currentPage--;
			this.getUsers(this.currentPage);
		},
	},
	created() {
		//get first page of users from api
		this.getUsers(1);
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
				:class="{ 'is--disabled': currentPage === 1 }"
				:disabled="currentPage === 1 || isFetchingUsers"
				class="member-list__button"
			>
				Back
			</button>
			<button
				@click="goToNextPage"
				:class="{ 'is--disabled': currentPage === 500 }"
				:disabled="currentPage === 500 || isFetchingUsers"
				class="member-list__button m--next"
			>
				Next
			</button>
		</div>
		<a
			:href="`https://randomuser.me/api/?page=${currentPage}&results=10&seed=members&inc=gender,name,location,email,phone,id,picture,dob&format=csv`"
			download
			class="member-list__button m--download"
		>
			Download CSV
		</a>
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
		max-width: 18rem;
		font-size: 1.2rem;
		&:hover {
			cursor: pointer;
		}
		&.is {
			&--disabled {
				opacity: 0.5;
			}
		}
		&.m {
			&--download {
				background-color: transparent;
				color: var(--primary);
				border: 1px solid var(--primary);
				align-self: end;
				margin: 1rem;
				text-decoration: none;
				&:hover {
					background-color: var(--black_s10);
				}
			}
			&--next {
				margin-left: 2rem;
			}
		}
	}
}
</style>
