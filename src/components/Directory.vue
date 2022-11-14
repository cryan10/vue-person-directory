<script>
import Card from './Card.vue';

export default {
	name: 'Directory',
	components: {
		Card,
	},
	props: ['users'],
};
</script>

<template>
	<div class="directory" role="presentation">
		<div v-bind:key="user.id" v-for="user in users" role="presentation">
			<Card v-bind:user="user" />
		</div>
	</div>
</template>

<style scoped lang="scss">
.directory {
	display: grid;
	grid-template-columns: repeat(2, 1fr);
	gap: 2rem;
	background-color: var(--secondary);
	min-width: 660px;
	min-height: 800px;
	padding: 2rem;
	margin-bottom: 1.5rem;
	border-radius: 6px;
	box-shadow: 1px 1px 2px var(--box-shadow);
	@media (max-width: 699px) {
		min-width: 0;
		min-height: 0;
		grid-template-columns: 1fr;
	}
}
</style>
