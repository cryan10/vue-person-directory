<script>
import Card from './Card.vue';

export default {
	name: 'Directory',
	components: {
		Card,
	},
	props: ['users'],
};

//loop through and create a button for each page. click will call api again, but for the right page
</script>

<template>
	<div class="directory">
		<div v-bind:key="user.login.uuid" v-for="user in users">
			<Card v-bind:user="user" />
		</div>
	</div>
</template>

<style scoped lang="scss">
.directory {
	display: grid;
	grid-template-columns: repeat(2, 1fr);
	gap: 2rem;
}
</style>
