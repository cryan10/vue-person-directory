<script>
export default {
	name: 'Card',
	props: ['user'],
};
</script>

<template>
	<div>
		<img :src="user.picture.large" />
		<h2>{{ user.name.first }} {{ user.name.last }}</h2>
		<ul>
			<li>Age: {{ user.dob.age }}</li>
			<li>Gender: {{ user.gender }}</li>
			<li>
				Email:
				<a :href="`mailto:${user.email}`">{{ user.email }}</a>
			</li>
			<li>Phone: {{ user.phone }}</li>
		</ul>
	</div>
</template>

<style scoped></style>
