<script>
export default {
	name: 'Card',
	props: ['user'],
};
</script>

<template>
	<div>
		<!-- <img /> -->
		<!-- <h2>{{ user.name.first }} {{ user.name.last }}</h2> -->
		<ul>
			<li>Age: 30</li>
			<li>Gender: Female</li>
			<li>
				Email:
				<a href="mailto:email@email.com">email@email.com</a>
			</li>
			<li>Phone: (999) 999-9999</li>
		</ul>
	</div>
</template>

<style scoped></style>
