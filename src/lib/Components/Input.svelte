<script>
	let { value = $bindable() } = $props();
</script>

<div class="flex flex-col p-4 gap-4">
	<input
		class="rounded-2xl h-12 bg-sky-50 text-stone-900 text-center"
		placeholder="Romaji Character"
		type="text"
		bind:value
	/>
</div>
