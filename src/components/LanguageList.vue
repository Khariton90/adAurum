<script>
export default {
	name: 'LanguageList',
	data() {
		return {
			list: ['RU', 'EN', 'TUR'],
			current: 'RU',
		}
	},
	methods: {
		changeLang(lang) {
			this.current = lang
		},
	},
}
</script>

<template>
	<div class="language-list">
		<img
			src="../assets/global.svg"
			alt="global"
			loading="lazy"
			width="24"
			height="24"
		/>
		<a
			href="#"
			v-for="item of list"
			:key="item"
			:class="{ 'is-current': current === item }"
			@click.prevent="changeLang(item)"
			>{{ item }}</a
		>
	</div>
</template>

<style lang="scss" scoped>
.language-list {
	@include flex(row);
	align-items: center;
	column-gap: 10px;
	flex-shrink: 0;
}

.is-current {
	color: $color-pink;
}
</style>
