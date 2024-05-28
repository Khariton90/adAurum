<script>
export default {
	name: 'AsidePreview',
}
</script>

<template>
	<div class="aside__title title"><span>Файлы</span></div>
	<div class="aside__preview preview">
		<img class="preview__image" src="../assets/media-files.png" alt="preview" />
		<p class="preview__description">
			Закажи у личного помощника медиаплан. Он появится в этом разделе
		</p>
	</div>
</template>

<style lang="scss" scoped>
.title {
	display: none;
}

.preview {
	display: none;
	&__image {
		margin-bottom: 30px;
	}

	&__description {
		max-width: 255px;
	}
}

@media (min-width: $media-md) {
	.preview {
		padding: 0 80px;
		display: block;
		font-weight: 500;
		text-align: center;
		@include flex(row);
		align-items: center;
		justify-content: center;
	}

	.title {
		margin-bottom: 30px;
		display: block;
	}
}

@media (min-width: 1200px) {
	.preview {
		@include flex(column);
		padding: 0;
	}
}
</style>
