<template>
	<ul>
		<li v-for="(message, index) in todos" :key="index">
			<p>{{ message }}</p>
			<button @click="deleteItem(index)">delete</button>
		</li>
	</ul>
</template>


<script>
	export default {
		props: ['todos'],

		methods: {
			deleteItem(index) {
				this.$emit('delete-item', index);
			}
		}
	}
</script>


<style lang="sass" scoped>
	@import '../assets/style.sass'

	li
		display: flex
		flex-direction: row
		align-items: center
		list-style: none
		padding-left: 1em
		position: relative

		@include font($black, 20)

		&::before
			content: '',
			display: block
			height: 0.5em
			width: 0.5em
			background-color: $green
			position: absolute
			top: calc(50% - 0.25em)
			left: 0
			border-radius: 50%

		&:not(:last-child)
			margin-bottom: 8px

	ul
		padding-left: 0
		margin-left: 20px

	p
		margin: 0
		margin-right: 0.75em

	button
		@extend %btn
		@extend %focus
</style>