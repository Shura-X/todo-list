<template>
	<div @keydown.enter="addItem($event)">
		<input type="text" 
			placeholder="add some task to do"
			v-model="input">
		<button type="submit" @click="addItem(input)">add</button>
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
			addItem(event) {
				this.input = '';

				if (typeof event == 'string') {
					if (event.length < 50) { 
						this.$emit('add-item', event);
					} else {
						alert('Hey, this note is too long')
					}
				} else {
					this.$emit('keydown', event)
				}
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