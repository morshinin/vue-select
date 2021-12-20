<template>
	<div 
		:class="$style.select"
		@blur="open = false"
		:tabindex="tabindex"
	>
		<div 
			:class="{
				[$style.selected]: true,
				[$style.selectedOpen]: !open }"
			@click="open = !open">
			{{ selected || placeholder }}
		</div>
		<items-list-component
			:items="items"
			:isOpen="open"
			@changeOpen="setOpen"
			@changeSelect="setSelect"
		/>
	</div>
</template>

<script>
import ItemsListComponent from './ItemsList.vue';

export default {
	name: 'SelectComponent',
	props: {
		items: {
			type: Array,
			required: true
		},
		tabindex: {
			type: Number,
			required: false,
			default: 0
		}
	},
	data() {
		return {
			open: false,
			placeholder: 'Choose a song',
			selected: this.placeholder,
		}
	},
	components: {
		ItemsListComponent
	},
	methods: {
		setOpen(value) {
			this.open = value;
		},
		setSelect(value) {
			this.selected = value;
		}
	}
}
</script>

<style lang="stylus" module>
.select
	cursor: pointer
	text-transform: uppercase
	position: relative

.selected 
	padding: 1rem
	transition: background-color .5s ease
	font-weight: bold
	border: 1px solid silver
	border-radius: 5px
	text-align left

	&:after
		content '\25b4'
		position absolute
		top 50%
		right 0
		padding 0 1rem
		transform rotateX(180deg) translateY(50%)

	&Open:after
		transform rotateX(0) translateY(-50%)

	&:hover
		background-color: silver
</style>