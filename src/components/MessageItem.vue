<script>
export default {
	name: 'MessageItem',
	props: ['message'],
}
</script>

<template>
	<div class="message-item" :class="{ 'message-item_assist': message.assist }">
		<div v-if="message.assist" class="message-item__avatar">
			<img src="../assets/message-avatar.png" alt="avatar" loading="lazy" />
		</div>
		<div class="message-item-wrapper">
			<p class="message-item__body">{{ message.message }}</p>
			<div v-if="message.assist" class="message-item__time">
				<span
					><b>{{ message.user }}</b>
				</span>
				<time :datetime="message.createdAt">{{ message.createdAt }}</time>
			</div>
			<time v-else :datetime="message.createdAt" class="message-item__time">{{
				message.createdAt
			}}</time>
		</div>
	</div>
</template>

<style lang="scss" scoped>
.message-item {
	@include flex(row);
	width: 100%;
	margin-bottom: 11px;
	justify-content: flex-end;
	font-size: 14px;
	&__body {
		background-color: $color-white;
		border-radius: 12px;
		padding: 16px 22px;
		max-width: 540px;
		width: 100%;
		font-weight: 500;
		font-size: 1rem;
		overflow-wrap: break-word;
		margin-bottom: 10px;
	}

	&__time {
		font-size: 15px;
		color: $color-text-dark-grey;
		float: right;
		display: flex;
		gap: 8px;
	}
}

.message-item_assist {
	justify-content: flex-start;
	& .message-item__time {
		float: left;
	}
}

.message-item__avatar {
	margin-right: 13px;
}

.message-item-wrapper {
	width: 100%;
	max-width: 540px;
}

@media (min-width: $media-md) {
	.message-item {
		font-size: 1rem;
	}
}
</style>
