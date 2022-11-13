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
	<div class="directory" role="presentation">
		<div v-bind:key="user.login.uuid" v-for="user in users" role="presentation">
			<Card v-bind:user="user" />
		</div>
	</div>
</template>

<style scoped lang="scss">
.directory {
	display: grid;
	grid-template-columns: repeat(2, 1fr);
	gap: 2rem;
	background-color: var(--accent);
	max-width: fit-content;
	min-width: 660px;
	min-height: 800px;
	padding: 2rem;
	border-radius: 6px;
	box-shadow: 1px 1px 2px #0000001f;
}
</style>
