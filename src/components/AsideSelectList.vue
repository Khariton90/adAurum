<script>
import SelectComponent from '../components/Select.vue'

export default {
	name: 'AsideSelectList',
	props: ['mediaPlanes', 'reports'],
	components: {
		SelectComponent,
	},
}
</script>

<template>
	<div class="aside__title title">
		<span>Файлы</span>
	</div>
	<div class="aside-select-list">
		<SelectComponent
			title="Медиапланы"
			:options="mediaPlanes"
			type="media"
		></SelectComponent>
		<SelectComponent
			title="Отчеты"
			:options="reports"
			type="reports"
		></SelectComponent>
	</div>
</template>

<style lang="scss" scoped>
.title {
	display: none;
}

.aside-select-list {
	@include flex(column);
	flex: 0.5;
	column-gap: 20px;
	flex-wrap: wrap;
	align-items: center;
}

@media (min-width: $media-sm2) {
	.aside-select-list {
		@include flex(row);
		gap: 30px;
		flex: 1;
		justify-content: center;
		align-items: flex-start;
	}
}

@media (min-width: $media-md) {
	.title {
		margin-bottom: 30px;
		display: block;
	}
}

@media (min-width: 1200px) {
	.aside-select-list {
		@include flex(column);
		gap: 30px;
		flex: 1;
	}
}
</style>
