<script>
import Directory from './components/Directory.vue';
import Buttons from './components/Buttons.vue';

export default {
	name: 'app',
	components: {
		Directory,
		Buttons,
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
				.then(() => window.scrollTo(0, 0))
				.catch((error) => console.log(error));
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
			<Directory :users="users" />
			<Buttons
				:currentPage="currentPage"
				:isFetchingUsers="isFetchingUsers"
				@go-to-previous-page="goToPreviousPage"
				@go-to-next-page="goToNextPage"
			/>
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
		color: var(--primary);
		font-size: 2.4rem;
	}
}
</style>
