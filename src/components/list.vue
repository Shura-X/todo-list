<template>
	<!--<ul>
		<transition-group name="item" mode="out-in">
			<li v-for="(message, index) in todos" :key="index">
				<p>{{ message }}</p>
				<button @click="deleteItem(index)">delete</button>
			</li>
		</transition-group>
	</ul>-->

	<!--due to the old bug with transition-group,
		i can't just deconstruct each item in v-for
		and remove items by their index, so i added
		id field-->
	<transition-group tag="ul" name="item">
		<li v-for="item in todos" :key="item.id">
			<p>{{ item.message }}</p>
			<button @click="$emit('remove-item', item.id)">remove</button>
		</li>
	</transition-group>
</template>


<script>
	export default {
		props: ['todos']
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

	.item-enter-active,
	.item-leave-active
		transition: all .5s

		p, button
			transition: all .5s

	.item-enter,
	.item-leave-to
		opacity: 0

		p, button
			transform: translate(50px)
</style>