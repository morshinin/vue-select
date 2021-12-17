<template>
	<div :class="$style.select">
		<div :class="$style.selected" @click="open = !open">
			{{ selected }}
		</div>
		<div :class="{ [$style.items]: true, [$style.itemsHide]: !open }">
			<div 
				v-for="(item, i) of items" 
				:key="i"
				@click="selected=item; open=false"
				:class="$style.item"
			>
				{{ item }}
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'SelectComponent',
	data() {
		return {
			open: false,
			items: ['Item 1', 'Item 2', 'Item 3'],
			selected: null,
		}
	},
	mounted() {
		this.selected = this.items.length > 0 ? this.items[0] : null
	}
}
</script>

<style lang="stylus" module>
.select
	cursor: pointer
	text-transform: uppercase
	position: relative

.selected,
.item 
	padding: 1rem
	transition: background-color .5s ease

.selected 
	font-weight: bold
	border: 1px solid silver
	border-radius: 5px
	border-bottom-right-radius: 0
	border-bottom-left-radius: 0

.items 
	position: absolute
	width: 100%
	left: 0
	background-color: #000
	color: #fff
	border: 1px solid silver
	border-top: 0
	border-bottom-right-radius: 5px
	border-bottom-left-radius: 5px
	box-sizing: border-box

.item:not(:first-child)
	border-top: 1px solid silver

.selected:hover,
.item:hover 
	background-color: silver

.itemsHide 
	display: none
</style>