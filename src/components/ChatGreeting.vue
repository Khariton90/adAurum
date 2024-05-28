<script>
export default {
	name: 'ChatGreeting',
}
</script>

<template>
	<div class="chat-greeting">
		<div class="chat-greeting__image">
			<img src="../assets/chat-preview.png" alt="Chat Greeting" />
		</div>
		<p class="chat-greeting__description">
			Это чат с администратором. Ты можешь с ним пообщаться по любому вопросу о
			нашем сервисе и узнать о ходе работы
		</p>
	</div>
</template>

<style lang="scss" scoped>
.chat-greeting {
	@include flex(column);
	align-items: center;
	text-align: center;
	justify-content: space-between;
	margin: 0 auto;
	max-width: 470px;
	margin-bottom: 57px;
	padding: 0 20px;

	&__image {
		width: 130px;
		aspect-ratio: 1 / 1;
	}
	&__description {
		padding: 20px 0;
		font-weight: 500;
		font-size: 1rem;
	}
}

@media (min-width: $media-lg) {
	.chat-greeting {
		&__image {
			width: 190px;
		}
	}
}
</style>
