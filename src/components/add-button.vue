<script>
import Plus from "@/components/icons/plus.vue";

export default {
	name: "add-button",
	components: {Plus},
}
</script>

<template>
	<button>
		<slot></slot>
		<svg width="30" height="30" viewBox="0 0 30 30" fill="none" xmlns="http://www.w3.org/2000/svg">
			<path d="M15 6.25V23.75" stroke="#3EA748" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
			<path d="M6.25 15H23.75" stroke="#3EA748" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
		</svg>
	</button>
</template>

<style scoped lang="scss">
button {
	display: flex;
	align-items: center;
	justify-content: space-between;
	background: transparent;
	padding: 1rem 2rem;
	border-radius: 0.5rem;
	border: 1px dashed var(--primary_color);
	outline: none;
	color: var(--primary_color);
	font-weight: 500;
	cursor: pointer;
	width: 100%;
	transition: 0.4s ease;
	
	svg path {
		transition: 0.4s ease;
	}
	
	&:hover {
		background: var(--primary_color);
		color: white;
		
		svg path {
			stroke: white;
		}
	}
}
</style>