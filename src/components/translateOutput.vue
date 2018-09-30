<template>
	<div id="translateOutput" class="transOutput">
		{{ translatedText }}
	</div>
</template>

<script>
	export default {
		name: 'translateOutput',
		props: [
			"translatedText"
		]
	}

</script>

<style>
	.transOutput{
		font-size: 20px
	}
</style>