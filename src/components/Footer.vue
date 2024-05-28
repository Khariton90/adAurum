<script>
import LanguageList from './LanguageList.vue'
import SocialLinkList from './SocialLinkList.vue'

export default {
	name: 'Footer',
	components: {
		LanguageList,
		SocialLinkList,
	},
}
</script>

<template>
	<footer class="footer">
		<div class="container">
			<div class="row footer__top">
				<div class="footer__logo">
					<a href="#">
						<img src="../assets/logo.png" loading="lazy" alt="pink-chicken" />
					</a>
				</div>
				<div class="footer__privacy-policy">
					<a href="#" target="_blank">Политика конфиденциальности</a>
				</div>
			</div>

			<div class="row footer__bottom">
				<div class="footer__contacts">
					<a href="mailto:pinkchicken@adaurum.ru" target="_blank"
						><img
							src="../assets/sms-tracking.svg"
							loading="lazy"
							alt="sms-tracking"
						/>
						pinkchicken@adaurum.ru</a
					>
				</div>
				<LanguageList />
				<SocialLinkList />
			</div>
		</div>
	</footer>
</template>

<style lang="scss" scoped>
.footer {
	color: $color-text-dark-grey;
	grid-column: 1/3;
	background-color: $color-white;

	& .container {
		padding: 40px 20px;
		@include flex(column);
		row-gap: 20px;
	}

	& .row {
		width: 100%;
		@include flex(column);
	}

	&__top {
		column-gap: 40px;
		padding-right: 40px;
		row-gap: 20px;
	}

	&__bottom {
		column-gap: 64px;
		row-gap: 20px;
	}

	&__contacts {
		order: 1;
		& a {
			@include flex(row);
			align-items: center;
			column-gap: 10px;
			color: $color-text-dark-grey;
		}
	}
}

@media (min-width: 1200px) {
	.footer {
		background-color: $color-dark-grey;

		& .container {
			@include flex(row);
			flex-wrap: wrap;
			align-items: center;
		}

		& .row {
			width: 50%;
			@include flex(row);
			align-items: center;
		}

		&__contacts {
			order: 1;
		}
	}
}

@media (min-width: $media-lg) {
	.footer {
		&__contacts {
			order: 0;
		}
	}
}
</style>
