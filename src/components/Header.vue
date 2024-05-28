<script>
export default {
	name: 'Header',
}
</script>

<template>
	<header class="header">
		<div class="container">
			<div class="header__logo">
				<a href="#">
					<img src="../assets/pink-logo.png" alt="pink-chicken" />
				</a>
			</div>

			<ul class="header-list">
				<li class="header__item">
					<a class="header__link" href="#">
						<span class="header-list__image">
							<img
								src="../assets/procced.svg"
								alt="procced"
								width="24px"
								height="24px"
							/>
						</span>
						<span class="header__procent">5%</span>
						<span class="header__procent-sm">5% выручки</span>
					</a>
				</li>
				<li class="header__item">
					<a href="#" class="header__link">
						<span class="header-list__image">
							<img
								src="../assets/user.svg"
								alt="user"
								width="24px"
								height="24px"
							/>
						</span>
						<span class="header__email">Username@adaurum.ru</span>
					</a>
				</li>
			</ul>

			<div class="header-actions">
				<button type="button" class="header-settings-button button">
					<img
						src="../assets/settings.svg"
						alt="settings button"
						width="24"
						height="24"
					/>
				</button>
				<button type="button" class="header-entry-button button">
					<img
						src="../assets/login.svg"
						alt="entry button"
						width="24"
						height="24"
					/>
				</button>
			</div>
		</div>
	</header>
</template>

<style lang="scss" scoped>
.header {
	grid-column: 1/3;
	background-color: $color-white;

	& .container {
		margin: 0 auto;
		padding: 20px;
		display: grid;
		grid-template-columns: 1fr auto;
	}

	&__link {
		@include flex(row);
		align-items: center;
	}

	&__logo {
		flex: 1;
		max-width: 181px;
		grid-column: 1/3;
	}

	&__email {
		font-weight: 600;
	}

	&__procent {
		display: none;
	}

	&__procent-sm {
		font-size: 12px;
		font-weight: 500;
		color: #797979;
	}
}

.header-list {
	@include flex(column);
	column-gap: 20px;
	margin: 20px 0;
}

.header-list {
	padding: 0;

	&__image {
		display: none;
	}
}

.header-actions {
	@include flex(row);
	column-gap: 12px;
	align-items: center;
	margin-left: 10px;

	& .button {
		display: block;
		padding: 8px;
		background-color: $color-grey;
		border-radius: 50%;
		width: 40px;
		height: 40px;

		&:hover {
			opacity: 0.7;
		}
	}
}

@media (min-width: $media-md) {
	.header {
		background-color: $color-grey;
		& .container {
			@include flex(row);
			align-items: center;
			padding: 30px 20px;
		}

		&__procent {
			display: block;
		}

		&__procent-sm {
			display: none;
		}

		&__logo {
			flex: 1;
			max-width: 100%;
		}
	}

	.header-actions {
		padding-left: 26px;

		& .button {
			background-color: $color-white;
		}
	}

	.header-list {
		padding: 0;
		margin: 0;
		flex-direction: row;
		&__image {
			display: inline-flex;
			padding: 8px;
			border-radius: 50%;
			background-color: $color-pink;
			margin-right: 10px;
		}
	}
}
</style>
