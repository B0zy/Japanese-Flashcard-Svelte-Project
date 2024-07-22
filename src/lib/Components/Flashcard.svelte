<script>
	let { katana, hiragana } = $props();
</script>

<div class="bg-slate-700 min-w-1/3 text-blue-50 flex flex-col rounded-2xl shadow-2xl mx-4 gap-4">
	<h1 class="text-xl md:text-3xl text-center p-4">Japanese Katana & Hiragana Flash Card</h1>
	<div class="flex flex-col gap-4 justify-center">
		<div class="flex flex-col items-center text-2xl">
			<h2 class="text-blue-50">Katakana</h2>
			<p>{katana}</p>
		</div>
		<div class="flex flex-col items-center text-2xl p-4">
			<h2 class="text-sky-50">Hiragana</h2>
			<p>{hiragana}</p>
		</div>
	</div>
</div>
