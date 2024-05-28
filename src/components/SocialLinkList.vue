<script>
export default {
	name: 'SocialLinkList',
}
</script>

<template>
	<div class="social-links">
		<a href="#" target="_blank">
			<img
				src="../assets/Telegram.svg"
				loading="lazy"
				alt="telegram"
				width="40"
				height="40"
			/>
		</a>
		<a href="#" target="_blank">
			<img
				src="../assets/whatsapp.svg"
				loading="lazy"
				alt="whatsapp"
				width="40"
				height="40"
			/>
		</a>
	</div>
</template>

<style lang="scss" scoped>
.social-links {
	@include flex(row);
	align-items: center;
	column-gap: 10px;
	flex-shrink: 0;
}

.social-links {
	order: 2;
}

@media (min-width: $media-md) {
	.social-links {
		order: -1;
	}
}

@media (min-width: $media-lg) {
	.social-links {
		order: 2;
	}
}
</style>
