<script>
export default {
	name: "custom-button",
}
</script>

<template>
	<button>
		<slot></slot>
	</button>
</template>

<style scoped lang="scss">
button {
	display: block;
	background: var(--primary_color);
	padding: 1rem 2rem;
	border-radius: 0.5rem;
	border: none;
	outline: none;
	color: white;
	font-weight: 500;
	cursor: pointer;
	transition: .4s ease;
	&:hover{
		opacity: 0.8;
	}
}
</style>