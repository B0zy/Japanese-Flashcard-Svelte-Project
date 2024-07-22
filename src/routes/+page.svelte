<script>
	import { onMount } from 'svelte';
	import Flashcard from '$lib/Components/Flashcard.svelte';
	import charData from '../characters.json';
	import Input from '$lib/Components/Input.svelte';
	import Button from '$lib/Components/Button.svelte';

	let characters = $state([]);
	let randomCharacterSet = $state([]);
	let inputValue = $state('');
	let incorrectCharacters = $state([]);
	let answerValue = $state('');
	let spanColor = $derived(answerValue === 'Correct!' ? 'text-green-500' : 'text-red-600');

	onMount(() => {
		characters = processCharacters(charData);
		getRandomCharacter();
	});

	function processCharacters(data) {
		let processed = $state([]);
		for (const key in data) {
			for (const subKey in data[key]) {
				processed.push(data[key][subKey].seion);
				if (data[key][subKey].dakuon) {
					processed.push(data[key][subKey].dakuon);
				}
				if (data[key][subKey].handakuon) {
					processed.push(data[key][subKey].handakuon);
				}
			}
		}
		return processed;
	}

	// Get a random object from the array and get its katakana and hiragana
	function getRandomCharacter() {
		let randomIndex = Math.floor(Math.random() * characters.length);
		randomCharacterSet = characters[randomIndex];
	}

	function onCheckAnswer() {
		if (inputValue === randomCharacterSet.romaji) {
			answerValue = 'Correct!';
			getRandomCharacter();
			incorrectCharacters = [];
		} else {
			answerValue = 'Incorrect!';
			incorrectCharacters.push(inputValue);
		}
		inputValue = '';
	}

	$inspect(inputValue);
</script>

<div class="flex flex-col justify-center mt-10 gap-10">
	<Flashcard katana={randomCharacterSet.katakana} hiragana={randomCharacterSet.hiragana} />

	<p class="text-sky-50 text-xl text-center">Characters already used: {incorrectCharacters}</p>

	<Input bind:value={inputValue} />

	<div class="flex flex-col items-center">
		<p class="text-sky-50 text-xl bg-slate-800 p-4 max-w-72 rounded-2xl">
			Your Answer is: <span class={spanColor}>{answerValue}</span>
		</p>
	</div>

	<Button onclick={onCheckAnswer} />
</div>
