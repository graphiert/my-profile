<script>
	import { createEventDispatcher } from 'svelte';
	import { Input, Label, Button } from 'flowbite-svelte';

	export let title;

	const dispatch = createEventDispatcher();
	let input = '';

	function handleSubmit(e) {
		dispatch('submit', {
			input,
			reset: e.target.reset()
		});
	}
</script>

<form on:submit|preventDefault={(e) => handleSubmit(e)}>
	<Label for="title" class="block mb-2">{title}</Label>
	<Input type="text" id="title" bind:value={input} placeholder={title} size="lg">
		<Button slot="right" color="blue" size="sm" type="submit"
			>{title}<i class="ml-2 bi bi-arrow-right"></i></Button
		>
	</Input>
</form>
