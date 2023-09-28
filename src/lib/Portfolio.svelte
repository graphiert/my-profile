<script>
	import { onMount } from 'svelte';
	import { Card } from 'flowbite-svelte';

	let portfolios = [];
	onMount(() => {
		portfolios = [
			{
				name: 'Anime Searcher',
				description: 'The website used to search anime, uses the Jikan API v4.',
				img: '/assets/portfolios/1.png',
				href: '/portfolio/anime-searcher'
			},
			{
				name: 'Todo List',
				description: 'Simple Todo List management.',
				img: '/assets/portfolios/2.jpg',
				href: '/portfolio/todolist'
			},
			{
				name: 'Contact Manager',
				description: 'Simple Contact management, using Django Python.',
				img: '/assets/portfolios/3.png',
				href: 'https://github.com/graphiert/contact-app'
			}
		];
	});
</script>

<h2 class="text-2xl my-2 font-bold">My Portfolio</h2>

<div class="flex justify-center">
	<div class="my-3 gap-3 grid grid-cols-1 md:grid-cols-3 md:3/4">
		{#each portfolios as portfolio}
			<Card img={portfolio.img} href={portfolio.href}>
				<h5
					class="mb-2 text-2xl font-bold tracking-tight text-gray-900
	dark:text-white"
				>
					{portfolio.name}
				</h5>
				<p
					class="mb-3 font-normal text-gray-700 dark:text-gray-400
	leading-tight"
				>
					{portfolio.description}
				</p>
			</Card>
		{/each}
	</div>
</div>
