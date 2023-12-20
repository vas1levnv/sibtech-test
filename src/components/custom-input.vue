<script>
export default {
	name: "custom-input",
	props:{
		modelValue: String,
	},
}
</script>

<template>
	<input :value="modelValue" @input="$emit('update:modelValue', $event.target.value)">
</template>

<style scoped lang="scss">
input {
	background: white;
	border-radius: 0.5rem;
	padding: 2rem;
	border: none;
	outline: none;
	width: 100%;
	font-size: 1rem;
}
</style>