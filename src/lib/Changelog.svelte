<script>
	import { onMount } from 'svelte';
	let data,
		olders = [];

	onMount(async () => {
		const req = await fetch(
			'https://raw.githubusercontent.com/graphiert/Code-Sample/notes/changelog.json'
		);
		const res = await req.json();
		data = res;
		olders = data.map((x) => x);
		olders.shift();
	});
</script>

<div class="container">
	<section>
		{#if data === undefined}
			<p>Tunggu sebentar, lagi diproses...</p>
		{:else}
			<h2 class="text-2xl my-2 font-bold">
				Website ini sekarang sedang dalam versi {data[0].version}!
			</h2>
			<h3 class="text-xl my-2 font-semibold">Konten apa saja yang baru disini? Ini dia~</h3>
			<ul class="list-disc">
				{#each data[0].features as feature}
					<li class="ml-6">{feature}</li>
				{/each}
			</ul>
		{/if}
	</section>
	<br />
	<section>
		{#if data !== undefined}
			<h2 class="text-xl my-2 font-bold">Versi Sebelumnya</h2>
			{#each olders as older}
				<div class="my-3">
					<h3 class="text-md font-semibold">Versi {older.version}</h3>
					<ul class="list-disc">
						{#each older.features as feature}
							<li class="ml-6">{feature}</li>
						{/each}
					</ul>
				</div>
			{/each}
		{/if}
	</section>
</div>

<!--<main>-->
<!--  <section>-->
<!--    {#if data.length == 0}-->
<!--      <h1>Gak ada</h1>-->
<!--      <div></div>-->
<!--    {/if}-->
<!--  </section>-->
<!--</main>-->
<!--
  data[0] ? data[0].version : ''
  feature ? feature : ''
-->
