<script>
export default {
	name: 'DashboardHeader',
	data() {
		return {
			isOpen: false,
			messages: [],
			message: '',
		}
	},
	methods: {
		openTooltip() {
			this.isOpen = !this.isOpen
		},
	},
}
</script>

<template>
	<div class="dashboard-header">
		<div class="dashboard-header__title title">
			<span>Личный помощник</span>
		</div>
		<div class="dashboard-header__assist assist">
			<span class="assist__username">Jim Davidson</span>
			<a href="mailto:Davidson@adaurum.ru">
				<span class="assist__email">Jim Davidson@adaurum.ru</span>
			</a>
		</div>

		<button
			type="button"
			class="dashboard-header-button button"
			@focus="openTooltip"
			@blur="openTooltip"
		>
			<img src="../assets/ellipses.svg" loading="lazy" alt="menu" />
			<div class="tooltip" :class="{ 'visually-hidden': !isOpen }">
				<a href="#">Обратная связь о работе сервиса</a>
				<a href="#">Сменить помощника</a>
			</div>
		</button>
	</div>
</template>

<style lang="scss" scoped>
.dashboard-header {
	display: flex;
	justify-content: space-between;
	align-items: center;
	column-gap: 20px;
	row-gap: 20px;
	flex-wrap: wrap;
	padding: 0 20px;

	&__title {
		font-size: 20px;
		order: 0;
	}
}

.assist {
	@include flex(row);
	gap: 10px;
	order: 2;
	font-size: 15px;
	&__username {
		font-weight: 600;
	}
}

.dashboard-header-button {
	width: 40px;
	height: 40px;
	background-color: $color-grey;
	border-radius: 50%;
	@include flex(row);
	align-items: center;
	justify-content: center;
	order: 1;

	&:hover {
		opacity: 0.7;
	}
}

@media (min-width: $media-sm2) {
	.dashboard-header {
		column-gap: 0;
		&__title {
			font-size: 24px;
			width: 100%;
			margin-right: auto;
		}
	}

	.dashboard-header-button {
		order: 3;
		margin-left: 6px;
	}
}

@media (min-width: $media-md) {
	.dashboard-header {
		&__title {
			margin-right: 0;
		}
	}
}

@media (min-width: 700px) {
	.dashboard-header {
		&__title {
			width: max-content;
			margin-right: 0;
		}
	}

	.dashboard-header-button {
		order: 3;
		margin-left: 6px;
	}
}

@media (min-width: 1200px) {
	.dashboard-header {
		&__title {
			margin-right: auto;
		}
	}

	.dashboard-header-button {
		order: 3;
		margin-left: 6px;
	}
}

@media (min-width: $media-lg) {
	.dashboard-header {
		column-gap: 26px;
	}
}
</style>
