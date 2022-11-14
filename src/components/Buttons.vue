<script>
export default {
	name: 'Buttons',
	props: ['currentPage', 'isFetchingUsers'],
};
</script>

<template>
	<div role="presentation" class="container">
		<div role="presentation">
			<button
				@click="$emit('go-to-previous-page')"
				:class="{ 'is--disabled': currentPage === 1 }"
				:disabled="currentPage === 1 || isFetchingUsers"
				class="button"
			>
				Back
			</button>
			<button
				@click="$emit('go-to-next-page')"
				:class="{ 'is--disabled': currentPage === 500 }"
				:disabled="currentPage === 500 || isFetchingUsers"
				class="button m--next"
			>
				Next
			</button>
		</div>

		<a
			:href="`https://randomuser.me/api/?page=${currentPage}&results=10&seed=members&inc=gender,name,location,email,phone,id,picture,dob&format=csv`"
			download
			class="button m--download"
		>
			Download CSV
		</a>
	</div>
</template>

<style scoped lang="scss">
.container {
	display: grid;
	grid-template-rows: 1fr 1fr;
	justify-items: center;
	@media (max-width: 768px) {
		row-gap: 2rem;
	}
}
.button {
	background-color: var(--accent);
	font-family: var(--fontStackAlt);
	color: var(--black);
	border: none;
	border-radius: 4px;
	box-shadow: 1px 1px 2px var(--box-shadow);
	padding: 0.8rem 2.4rem;
	max-width: 8rem;
	font-size: 1.2rem;
	text-align: center;
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
			justify-self: end;
			margin: 1rem;
			text-decoration: none;
			@media (max-width: 768px) {
				justify-self: center;
				margin: 0;
			}
			&:hover {
				background-color: var(--black_s10);
			}
		}
		&--next {
			margin-left: 1.5rem;
		}
	}
}
</style>
