<script>
import MessageItem from './MessageItem.vue'

export default {
	name: 'MessageList',
	props: ['messages'],
	components: {
		MessageItem,
	},
	computed: {
		getCurrentTime() {
			return new Date().toLocaleTimeString([], {
				hour: '2-digit',
				minute: '2-digit',
			})
		},
	},
}
</script>

<template>
	<div class="message-list">
		<div class="message-list-date">Сегодня {{ getCurrentTime }}</div>
		<MessageItem
			v-for="message of messages"
			:key="message.message"
			:message="message"
		/>
	</div>
</template>

<style lang="scss" scoped>
.message-list {
	padding: 0 26px 0 20px;
	max-height: 300px;
	height: 100%;
	overflow-y: scroll;

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
}

.message-list-date {
	width: 100%;
	text-align: center;
	padding: 24px;
	font-size: 15px;
	color: $color-text-dark-grey;
}
</style>
