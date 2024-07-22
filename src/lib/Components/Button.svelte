<script>
	let { text, onclick } = $props();
</script>

<div class="flex flex-col p-4 items-center">
	<button class="bg-slate-700 rounded-2xl w-44 text-sky-50 text-xl p-4 shadow" {onclick}
		>{text}</button
	>
</div>
