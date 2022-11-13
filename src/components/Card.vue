<script>
export default {
	name: 'Card',
	props: ['user'],
};
</script>

<template>
	<div class="card">
		<img class="card__image" :src="user.picture.large" />
		<div class="card__info-container">
			<h2 class="card__title">{{ user.name.first }} {{ user.name.last }}</h2>
			<ul>
				<li>{{ user.dob.age }} years old</li>
				<li class="card__gender">{{ user.gender }}</li>
				<li>
					<a :href="`mailto:${user.email}`">{{ user.email }}</a>
				</li>
				<li>
					<a :href="`tel:${user.phone}`">{{ user.phone }}</a>
				</li>
			</ul>
		</div>
	</div>
</template>

<style scoped lang="scss">
.card {
	display: flex;
	column-gap: 1rem;
	border: 1px solid var(--black_s20);
	border-radius: 4px;
	box-shadow: 1px 1px 2px #0000001f;
	&__image {
		border-start-start-radius: 4px;
		border-end-start-radius: 4px;
		height: 100%;
		width: fit-content;
	}
	&__title {
		font-family: var(--fontStackAlt);
		color: var(--secondary);
	}
	&__gender {
		text-transform: capitalize;
	}
}
</style>
