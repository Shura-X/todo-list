<template>
	<div @keydown.enter="addItem">
		<input type="text" 
			placeholder="add some task to do"
			v-model="input">
		<button type="submit" @click="addItem">add</button>
	</div>
</template>


<script>
	export default {
		data() {
			return {
				input: ''
			}
		},

		methods: {
			addItem() {
				if (this.input.length) {

					if (this.input.length < 50) {
						this.$emit('add-item', this.input)
					} else {
						alert('Hey, this note is too long')
					}

				}

				this.input = '';
			}
		}
	}
</script>


<style lang="sass" scoped>
	@import '../assets/style.sass'

	input
		width: 600px
		margin-right: 18px
		border-radius: 10px

		@extend %btn

	button
		@extend %btn
		@extend %focus
</style>