<script>
export default {
	methods: {
		logout() {
			localStorage.removeItem("session_token");
			this.$router.push({ name: "login" });
		},
	},
};
</script>

<template>
	<main class="home">
		<section class="container mx-auto p-4">
			<h1 class="text-4xl mb-8 text-center">Home</h1>
			<p class="text-gray-500 text-center">
				Welcome to the home page, <span class="link" @click="logout">Logout?</span>
			</p>
		</section>
	</main>
</template>
