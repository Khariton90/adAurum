<script>
export default {
	name: 'Select',
	props: ['title', 'options', 'type'],
	data() {
		return {
			isOpen: true,
			optionList: this.options,
			current: 5,
			messages: {
				media: {
					loading: 'Медиаплан в процессе составления',
					completed: 'Медиаплан от 1.06.22 готов',
				},
				reports: {
					loading: 'Отчет формируется',
					completed: 'Отчет от 1.06.22 готов',
				},
			},
		}
	},
	methods: {
		handleOpen() {
			this.isOpen = !this.isOpen
		},
		changeCurrent() {
			if (this.optionList.length > this.current) {
				this.current += 5
				return
			}
			this.current = 5
		},
	},
	computed: {
		slicedOptionList() {
			return this.optionList.slice(this.current - 5, this.current).reverse()
		},
	},
}
</script>

<template>
	<div v-if="optionList.length" class="select">
		<p class="select__title">
			{{ title }}
			<button class="button" @click="handleOpen">
				<img
					class="select__arrow"
					src="../assets/select-arrow.svg"
					alt="select-arrow"
					:class="{ rotate: !isOpen }"
				/>
			</button>
		</p>
		<div class="options" :class="{ 'visually-hidden': !isOpen }">
			<div class="option" v-for="item in slicedOptionList">
				<div class="option__body">
					<img src="../assets/xml.svg" alt="xml" />
					<span>{{ item.title }} {{ optionList.length }}</span>
					<button class="option-button button">
						<img
							v-if="item.status === 'completed' || item.status === 'done'"
							src="../assets/arrow-button.svg"
							alt="Arrow button"
						/>
						<img
							v-else="item.status === 'completed' || item.status === 'done'"
							src="../assets/load-button.svg"
							alt="Arrow button"
						/>
					</button>
				</div>
				<div class="option__process">
					<span v-if="item.status === 'loading'">
						<img
							src="../assets/Subtract.svg"
							alt="В процессе"
							loading="lazy"
							width="16"
							height="16"
						/>
						{{ messages[type].loading }}</span
					>

					<span v-if="item.status === 'completed'">
						<img
							src="../assets/done.svg"
							alt="В процессе"
							loading="lazy"
							width="16"
							height="16"
						/>
						{{ messages[type].completed }}</span
					>

					<span v-else="item.status === 'completed'"></span>
				</div>
			</div>

			<a
				href="#"
				v-if="optionList.length > 5"
				class="select__button"
				@click.prevent="changeCurrent"
				>Показать еще</a
			>
		</div>
	</div>
</template>

<style lang="scss" scoped>
.select {
	flex: 1;
	max-width: 314px;
	width: 100%;

	&__title {
		font-size: 18px;
		font-weight: 600;
		margin-bottom: 20px;
		@include flex(row);
		justify-content: space-between;
	}

	&__button {
		width: 100%;
		text-align: right;
		color: $color-pink;
		display: block;
	}
}

.select__arrow {
	transition: all 0.2s ease;
	rotate: 0;
}

.is-active {
	flex: 0.5;
}

.option {
	&__body {
		@include flex(row);
		align-items: center;
		justify-content: space-between;
		background-color: $color-grey;
		height: 42px;
		padding-left: 9px;
		border-radius: 12px;
	}

	&__process {
		font-size: 12px;
		color: $color-text-dark-grey;
		padding: 8px 0 14px;

		& span {
			@include flex(row);
			align-items: center;
			column-gap: 5px;
		}
	}
}

@media (min-width: $media-md) {
	.select {
		&__title {
			font-size: 18px;
			font-weight: 600;
			margin-bottom: 20px;
			@include flex(row);
		}
	}
}
</style>
