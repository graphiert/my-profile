<script>
	import { onMount } from 'svelte';
	import { Button, Card, Alert } from 'flowbite-svelte';

	import Modal from '../utils/modal.svelte';
	import InputText from '../utils/input-text.svelte';

	let status = 0;
	// -1 = Data not found (arr.length == 0)
	// 0 = Loading data
	// 1 = Data found (arr.length >= 1)

	let datas = [] || {};
	onMount(async () => {
		const req = await fetch('https://api.jikan.moe/v4/anime');
		const res = await req.json();
		datas = res.data;
		status = 1;
	});

	const handleSearch = async (data) => {
		status = 0;
		datas = [];
		const req = await fetch(`https://api.jikan.moe/v4/anime?q=${data.input}`);
		const res = await req.json();
		datas = res.data;

		status = datas.length == 0 ? -1 : 1;
		if (status == -1) {
			setTimeout(async () => {
				const req = await fetch('https://api.jikan.moe/v4/anime');
				const res = await req.json();
				datas = res.data;
				status = 1;
			}, 4000);
		}
	};

	let modalClicked = false;
	let dataFromId = [] || {};
	const handleReqFromId = async (id) => {
		dataFromId = {};
		const req = await fetch(`https://api.jikan.moe/v4/anime/${id}`);
		const res = await req.json();
		let stud = [];
		res.data.studios.forEach((el) => stud.push(el.name));
		dataFromId = {
			img: res.data.images.jpg.image_url,
			title: res.data.title,
			data: [
				res.data.score == null ? 'Score: Not rated yet' : `Score: ${res.data.score}`,
				`${res.data.type}, ${res.data.episodes} ep(s)`,
				`Duration: ${res.data.duration}`,
				stud.length == 0 ? 'Studio: Unknown' : 'Studio: ' + stud.join(', ')
			],
			url: res.data.url
		};
	};
</script>

<InputText title="Search" on:submit={(e) => handleSearch(e.detail)} />

<div class="mt-3 md:3/4">
	{#if status != 1}
		<Alert color={status == 0 ? 'blue' : 'red'}>
			{#if status == 0}
				Memuat data...
			{:else}
				Yang kamu cari tidak ditemukan.
			{/if}
		</Alert>
	{/if}
</div>

<div class="flex justify-center">
	<div class="mt-3 gap-3 grid grid-cols-1 md:grid-cols-3 md:3/4">
		{#each datas as data}
			<div class="h-1/4">
				<Card size="xs" img={data.images.jpg.image_url} class="mb-4">
					<h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900">
						{data.title}
					</h5>
					<p class="mb-3 font-normal text-gray-700 leading-tight">
						{data.year == null ? 'Unknown' : data.year}
					</p>
					<Button
						type="button"
						color="blue"
						on:click={() => {
							handleReqFromId(data.mal_id);
							modalClicked = true;
						}}>Read more<i class="ml-2 bi bi-arrow-right"></i></Button
					>
				</Card>
			</div>
		{/each}
	</div>
</div>
<!-- Main modal -->
<Modal on:close={() => (modalClicked = false)} {dataFromId} {modalClicked} />
