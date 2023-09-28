<script>
	import { createEventDispatcher } from 'svelte';
	import { Modal, Listgroup, Card, Button } from 'flowbite-svelte';

	export let modalClicked = false;
	export let dataFromId = [];

	const dispatch = createEventDispatcher();

	function handleClick() {
		dispatch('close');
	}
</script>

<Modal title={dataFromId.title ? dataFromId.title : '...'} bind:open={modalClicked} autoclose>
	<Card padding="none" img={dataFromId.img} class="h-1/2 my-6">
		<h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900">
			{dataFromId.title}
		</h5>
		<Listgroup items={dataFromId.data} let:item class="w-48">
			{item}
		</Listgroup>
	</Card>
	<svelte:fragment slot="footer">
		<Button href={dataFromId.url} color="blue"
			>Learn more<i class="ml-2 bi bi-arrow-right"></i></Button
		>
		<Button color="alternative" on:click={handleClick}>Close<i class="ml-2 bi bi-x"></i></Button>
	</svelte:fragment>
</Modal>
