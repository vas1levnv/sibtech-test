<script>
import Button from "@/components/custom-button.vue";
import Input from "@/components/custom-input.vue";
import CustomInput from "@/components/custom-input.vue";
import CustomButton from "@/components/custom-button.vue";
import AddButton from "@/components/add-button.vue";

export default {
	name: "fields",
	components: {AddButton, CustomButton, CustomInput, Input, Button},
	data() {
		return {
			fields: [
				{id: 1, title: 'Фамилия', value: '', isNecessarily: false, type: 'text'},
				{id: 2, title: 'Имя', value: '', isNecessarily: false, type: 'text'},
			],
			options: [
				{value: 'text', title: 'Строка'},
				{value: 'number', title: 'Число'},
				{value: 'list', title: 'Список'},
			],
			selected: '',
			textForAskedField: '',
			isOpenPopup: false,
			isError: false,
		}
	},
	methods: {
		addFiled() {
			if(this.selected && this.textForAskedField) {
				this.fields = [...this.fields,
					{id: Date.now(), value: this.textForAskedField, isNecessarily: false, type: this.selected}]
				this.isOpenPopup = false
			} else {
				this.isError = true
			}
		},
		removeField(id) {
			this.fields = [...this.fields.filter(el => el.id !== id)]
		}
	},
}
</script>

<template>
	<div class="fields">
		<h1>Поля</h1>
		<add-button @click="isOpenPopup = true">
			<div>Добавить поле</div>
		</add-button>
		<div class="fields-list">
			<div v-if="fields.length > 0" class="fields-item" v-for="field in fields" :key="field.id">
				<div class="fields-item-top">
					<div>{{ field.title }}</div>
					<div class="fields-item-delete" @click="removeField(field.id)">Удалить поле</div>
				</div>
				<custom-input :type="field.type" :placeholder="field.title" v-model="field.value"/>
				<label>
					<input type="checkbox" v-model="field.isNecessarily">
					<span>Сделать поле обязательным</span>
				</label>
			</div>
			<div v-else>Пожалуйста добавьте поле!</div>
		</div>
		<div class="popup" :class="{open: isOpenPopup}" @click="isOpenPopup = false">
			<div class="popup-wrapper" @click.stop>
				<div class="error" v-show="isError">Пожалуйста заполните все поля</div>
				<div class="popup-close" @click="isOpenPopup = false">X</div>
				<select v-model="selected">
					<option selected disabled value="">Выберите тип поля:</option>
					<option v-for="option in options" :value="option.value">{{ option.title }}</option>
				</select>
				<div>Напишите поле для текста</div>
				<input type="text" v-model="textForAskedField" placeholder="Поле для текста">
				
				<div v-show="selected === 'list'">
					<div style="margin: 1rem 0; color: #3EA748; font-weight: 700">В фигме не нарисовано как сделать далее, ТЗ написно не четко, поэтому далее код не писал</div>
					<div>Выберите тип выбор</div>
					<label>
						<input type="radio" name="choice" value="1">
						<span>Единичный</span>
					</label>
					<label>
						<input type="radio"  name="choice" value="2">
						<span>Множественный</span>
					</label>
				</div>
				<custom-button @click="addFiled">
					Добавить поле
				</custom-button>
			</div>
		</div>
	</div>
</template>

<style scoped lang="scss">

.fields {
	background: #F9F9F9;
	height: 100%;
	padding: 5rem 2rem;
	border-radius: 0 0.5rem 0.5rem 0;
	
	h1 {
		margin-bottom: 2rem;
	}
	
	&-list{
		margin-top: 2rem;
		display: grid;
		gap: 2rem;
	}
	
	&-item {
		&-top {
			display: flex;
			align-items: center;
			justify-content: space-between;
			margin-bottom: 0.5rem;
		}
		
		&-delete {
			color: var(--primary_color);
			cursor: pointer;
		}
		label{
			display: flex;
			align-items: center;
			gap: 0.5rem;
			margin-top: 0.5rem;
			font-weight: 500;
		}
	}
}

.popup {
	position: fixed;
	display: flex;
	justify-content: center;
	align-items: center;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background: rgba(0, 0, 0, .5);
	transition: 0.2s ease;
	transform: scale(0);
	pointer-events: none;
	
	&.open {
		transform: scale(1);
		pointer-events: auto;
	}
	
	&-wrapper {
		position: relative;
		width: 100%;
		max-width: 800px;
		padding: 2rem;
		border-radius: 1rem;
		background: white;
	}
	
	.error {
		color: red;
		font-weight: 700;
		margin-bottom: 1.25rem;
	}
	
	&-close {
		position: absolute;
		top: 0.75rem;
		right: 0.75rem;
		padding: 0.5rem;
		cursor: pointer;
		font-weight: 900;
		transition: 0.4s ease;
		
		&:hover {
			color: gray;
		}
	}
}
</style>