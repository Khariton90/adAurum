<script>
import SelectComponent from '../components/Select.vue'
import AsidePreview from './AsidePreview.vue'
import AsideSelectList from './AsideSelectList.vue'

export default {
	name: 'Aside',
	props: ['mediaPlanes', 'reports'],
	components: {
		SelectComponent,
		AsidePreview,
		AsideSelectList,
	},
}
</script>

<template>
	<aside class="aside">
		<AsidePreview v-if="!mediaPlanes.length && !reports.length" />
		<AsideSelectList v-else :media-planes="mediaPlanes" :reports="reports" />
	</aside>
</template>

<style lang="scss" scoped>
.aside {
	background-color: $color-white;
	padding: 10px 20px;
	@include flex(column);
	height: 100%;
	overflow-y: scroll;
	max-height: 730px;

	&::-webkit-scrollbar {
		width: 6px;
		background-color: transparent;
	}

	&::-webkit-scrollbar-thumb {
		border-radius: $border-radius;
		background-color: $color-scroll;
	}

	&::-webkit-scrollbar-track {
		background-color: transparent;
	}

	&__title {
		margin-bottom: 46px;
	}
}

@media (min-width: $media-md) {
	.aside {
		border-radius: $border-radius;
		max-height: 709px;
		padding: 28px 20px;
		box-shadow: 0px 0px 30px 0px #00000014;
	}
}
</style>
