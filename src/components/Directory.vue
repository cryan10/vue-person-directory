<script>
//import card component
import { useSSRContext } from 'vue';
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
	<div>
		<h2>test test 123</h2>
		<div v-bind:key="user.login.uuid" v-for="user in users">
			<Card v-bind:user="user" />
		</div>
		<Card />
	</div>
</template>

<style scoped></style>
