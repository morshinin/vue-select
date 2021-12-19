<template>
	<div 
		:class="{ 
			[$style.list]: true, 
		}"
		v-if="!isOpen"
	>
		<div 
			:class="$style.listItem"
			v-for="(item, i) of items" 
			:key="i"
			@click="changeOpen(); changeSelect($event)"
		>
			{{ item }}
		</div>
	</div>
</template>

<script>
export default {
	name: 'ItemsListComponent',
	props: {
		items: {
			type: Array,
			required: true
		},
		isOpen: {
			type: Boolean,
			default: false
		}
	},
	methods: {
		changeOpen() {
			this.$emit('changeOpen', !this.isOpen);
		},
		changeSelect(e) {
			this.$emit('changeSelect', e.target.innerText);
		}
	}
}
</script>

<style lang="stylus" module>
.list
	position: absolute
	width: 100%
	left: 0
	background-color: #fff
	border: 1px solid silver
	box-sizing: border-box
	box-shadow 0 0 10px rgba(0, 0, 0, .4)
	z-index 1

	&Item
		padding: 1rem
		transition: background-color .5s ease

		&:not(:first-child)
			border-top: 1px solid silver

		&:hover
			background-color: silver
</style>