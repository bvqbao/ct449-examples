<script>
import sourceData from "@/data.json";
import ButtonGoBack from "@/components/ButtonGoBack.vue";
import ExperienceCard from "@/components/ExperienceCard.vue";

export default {
	components: {
		ButtonGoBack,
		ExperienceCard
	},
	props: {
		id: { type: Number, required: true }
	},
	computed: {
		destination() {
			return sourceData.destinations.find(
				destination => destination.id === this.id
			)
		}
	}
}
</script>

<template>
	<div>
		<section class="destination" v-if="destination">
			<h1>{{ destination.name }}</h1>
			<ButtonGoBack />
			<div class="destination-details">
				<img :src="`/images/${destination.image}`" :alt="destination.name" />
				<p>{{ destination.description }}</p>
			</div>
		</section>

		<section class="experiences">
			<h2>Top Experiences in {{ destination.name }}</h2>
			<div class="cards">
				<router-link
					v-for="experience in destination.experiences"
					:key="experience.slug"
					:to="{
						name: 'experience.show',
						params: {
							experienceSlug: experience.slug
						}
					}"
				>
					<ExperienceCard	:experience="experience" />
				</router-link>
			</div>

			<router-view></router-view>
		</section>
	</div>
</template>