<script>
export default {
	name: 'Card',
	props: ['user'],
};
</script>

<template>
	<div class="card">
		<h2 class="card__title">{{ user.name.first }} {{ user.name.last }}</h2>
		<img
			:src="user.picture.large"
			:alt="`headshot of ${user.name.first} ${user.name.last}`"
			class="card__image"
			height="128"
			width="128"
		/>
		<div role="presentation">
			<ul class="card__info">
				<li>{{ user.dob.age }} years old</li>
				<li class="card__gender">{{ user.gender }}</li>
				<li>
					<a :href="`mailto:${user.email}`" class="card__link">
						{{ user.email }}
					</a>
				</li>
				<li>
					<a :href="`tel:${user.phone}`" class="card__link">{{ user.phone }}</a>
				</li>
			</ul>
		</div>
	</div>
</template>

<style scoped lang="scss">
.card {
	display: grid;
	grid-template-columns: min-content auto;
	column-gap: 1rem;
	border-radius: 4px;
	box-shadow: 1px 1px 2px #0000001f;
	background-color: var(--white);
	padding-right: 1rem;
	&__info {
		padding: 0;
		margin: 0;
		list-style: none;
	}
	&__image {
		grid-area: 1/1/3/2;
		border-start-start-radius: 4px;
		border-end-start-radius: 4px;
		height: 100%;
		width: fit-content;
	}
	&__title {
		align-self: center;
		margin: 0;
		font-family: var(--fontStackAlt);
		color: var(--primary);
	}
	&__gender {
		text-transform: capitalize;
	}
	&__link {
		color: var(--secondary);
	}
}
</style>
