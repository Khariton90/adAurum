<script>
import DashboardHeader from './DashboardHeader.vue'
import ChatGreeting from './ChatGreeting.vue'
import MessageList from './MessageList.vue'
import FormButton from './FormButton.vue'
import FormActions from './FormActions.vue'

export default {
	name: 'Dashboard',
	props: ['mediaPlanes', 'reports'],
	components: {
		DashboardHeader,
		ChatGreeting,
		MessageList,
		FormButton,
		FormActions,
	},
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
		handleSubmit(message) {
			if (!this.messages.length) {
				const newMessageAssist = {
					id: 1,
					message: `Lörem ipsum suparad pepött då satsig och soskap metrosocial. 
						Sapongar trenåvis i hypol innan visiskap, heterovybelt. Besav ditugen stenosade om exopagt.`,
					createdAt: new Date().toLocaleTimeString([], {
						hour: '2-digit',
						minute: '2-digit',
					}),
					assist: 'assist',
					user: 'Jim',
				}

				this.messages.push(newMessageAssist)
			}

			const newMessage = {
				id: 1,
				message,
				createdAt: new Date().toLocaleTimeString([], {
					hour: '2-digit',
					minute: '2-digit',
				}),
			}
			this.messages.push(newMessage)
			this.message = ''
		},
		addMediaPlane() {
			this.$emit('add-media')
		},
		addReport() {
			this.$emit('add-report')
		},
	},
}
</script>

<template>
	<section class="content dashboard">
		<DashboardHeader />

		<div class="dashboard-body chat">
			<ChatGreeting v-if="!messages.length" />
			<MessageList v-else :messages="messages" />

			<form
				class="chat-form form"
				action="submit"
				@submit.prevent="handleSubmit(message)"
			>
				<FormActions @add-media-plane="addMediaPlane" @add-report="addReport" />

				<div class="chat-form-message message">
					<input
						class="message__field"
						type="text"
						placeholder="Введите сообщение для администратора"
						v-model="message"
					/>

					<div class="message-actions">
						<div class="message-actions__files">
							<label class="message__label" for="message-file">
								<img
									src="../assets/folder-add.svg"
									alt="folder"
									loading="lazy"
								/>

								<input
									class="message__file visually-hidden"
									type="file"
									name="file"
									id="message-file"
								/>
							</label>
							<label class="message__label" for="message-image">
								<img src="../assets/gallery.svg" alt="gallery" loading="lazy" />

								<input
									class="message__image visually-hidden"
									type="file"
									name="image"
									id="message-image"
								/>
							</label>
						</div>

						<FormButton :messageLength="message.length" />
					</div>
				</div>
			</form>
		</div>
	</section>
</template>

<style lang="scss" scoped>
.dashboard {
	background-color: $color-white;
	@include flex(column);
	row-gap: 30px;
	height: auto;
}

.dashboard-body {
	background-color: $color-dark-grey;
	flex: 1;
	height: 100%;
	padding: 50px 0 0 0;
	@include flex(column);
}

.message {
	padding: 0 16px 10px 16px;
	background-color: $color-white;
	border-radius: $border-radius;
	border: 2px solid $color-dark-grey;
	margin: 0 20px 30px 20px;

	&:has(input:focus) {
		border: 2px solid $color-pink;
	}

	&__field {
		width: 100%;
		border: none;
		outline: none;
		font-size: 15px;
		padding: 25px 0 0;

		&:placeholder-shown {
			text-overflow: ellipsis;
		}
	}

	&__label {
		&:hover {
			opacity: 0.7;
		}
	}
}

.message-actions {
	@include flex(row);
	align-items: flex-end;
	min-height: 50px;
}

.message-actions__files {
	@include flex(row);
	align-items: center;
	column-gap: 20px;
}

.chat-form {
	margin-top: auto;
}

@media (min-width: $media-sm2) {
	.message {
		margin: 0;
	}
}

@media (min-width: $media-md) {
	.dashboard {
		height: 709px;
		padding: 20px 38px;
		box-shadow: 0px 0px 30px 0px #00000014;
	}

	.message {
		padding: 0 20px 20px 20px;
	}
}

@media (min-width: 1200px) {
	.dashboard {
		border-radius: $border-radius;
	}

	.dashboard-body {
		border-radius: $border-radius;
	}
}
</style>
