<script>

import Fields from "@/components/fields.vue";
import CustomButton from "@/components/custom-button.vue";

export default {
	components: {CustomButton, Fields},
	data() {
		return {}
	},
	methods: {
		sendForm(){
			alert('форма отправлена!')
		}
	},
	
	watch: {},
}
</script>

<template>
	<div class="app-wrapper">
		<div class="sidebar">
			<custom-button @click="sendForm">Сохранить</custom-button>
		</div>
		<Fields/>
		<div class="form"></div>
	</div>
</template>

<style scoped lang="scss">
.app-wrapper {
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	width: 100%;
	height: 100%;
	background: var(--primary_color);
}

.sidebar {
	background: white;
	padding: 5rem 2rem;
	display: flex;
	justify-content: center;
	align-items: end;
}
</style>
