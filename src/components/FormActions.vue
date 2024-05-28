<script>
export default {
	name: 'FormActions',
	data() {
		return {}
	},
	methods: {
		addMediaPlane() {
			this.$emit('add-media-plane')
		},
		addReport() {
			this.$emit('add-report')
		},
	},
}
</script>

<template>
	<fieldset class="fieldset form-actions">
		<button
			type="button"
			class="form-actions__button button"
			@click="addMediaPlane"
		>
			Заказать медиаплан
		</button>
		<button
			type="button"
			class="form-actions__button button"
			@click="addReport"
		>
			Заказать отчет
		</button>
	</fieldset>
</template>

<style lang="scss" scoped>
.form-actions {
	@include flex(column);
	gap: 12px;
	align-items: flex-end;
	padding: 10px 20px;

	&__button {
		color: $color-white;
		padding: 12px 18px;
		font-weight: 600;
		border-radius: $border-radius;
		max-width: max-content;

		&:hover {
			opacity: 0.7;
		}

		&:first-child {
			background-color: $color-pink;
		}

		&:last-child {
			order: -1;
			background-color: $color-blue;
		}
	}
}

@media (min-width: $media-md) {
	.form-actions {
		@include flex(row);
	}
}

@media (min-width: $media-lg) {
	.form-actions {
		padding: 20px;

		&__button {
			padding: 12px 22px;
		}
	}
}
</style>
