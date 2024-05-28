<script>
export default {
	name: 'FormButton',
	props: ['messageLength'],
}
</script>

<template>
	<button
		v-if="messageLength"
		class="button message-submit-button"
		type="submit"
	>
		<img
			src="../assets/submit-image.svg"
			loading="lazy"
			alt="submit"
			width="50"
			height="50"
		/>
	</button>

	<button
		v-else
		class="button message-submit-button disabled"
		type="button"
		disabled
	>
		<img
			src="../assets/submit-image.svg"
			loading="lazy"
			alt="submit"
			width="50"
			height="50"
		/>
	</button>
</template>

<style lang="scss" scoped>
.message-submit-button {
	margin-left: auto;
	&:hover {
		opacity: 0.7;
	}
}
</style>
