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
	column-gap: 1rem;
	border-radius: 4px;
	box-shadow: 1px 1px 2px var(--box-shadow);
	background-color: var(--white);
	@media (min-width: 400px) {
		grid-template-columns: min-content auto;
		padding-right: 1rem;
	}
	&__info {
		padding: 0;
		margin: 0;
		list-style: none;
		color: var(--black_s80);
		@media (max-width: 399px) {
			padding: 0 0.5rem 0.5rem;
		}
	}
	&__image {
		grid-area: 1/1/3/2;
		border-start-start-radius: 4px;
		border-end-start-radius: 4px;
		height: 100%;
		width: fit-content;
		@media (max-width: 399px) {
			height: fit-content;
			width: 100%;
			border-start-end-radius: 4px;
			border-end-start-radius: 0;
		}
	}
	&__title {
		align-self: center;
		margin: 0;
		font-family: var(--fontStackAlt);
		color: var(--primary);
		@media (max-width: 399px) {
			margin: 0.5rem 0 0 0.5rem;
		}
	}
	&__gender {
		text-transform: capitalize;
	}
	&__link {
		color: var(--primary);
	}
}
</style>
