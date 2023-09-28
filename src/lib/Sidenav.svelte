<script>
	import {
		Navbar,
		NavBrand,
		NavHamburger,
		Drawer,
		CloseButton,
		Sidebar,
		SidebarGroup,
		SidebarItem,
		SidebarWrapper,
		NavUl,
		NavLi
	} from 'flowbite-svelte';

	import { sineIn } from 'svelte/easing';
	let hidden1 = true;
	let transitionParams = {
		x: 320,
		duration: 200,
		easing: sineIn
	};

	const dataNav = [
		{ label: 'Profil Saya', href: '/' },
		{ label: 'Portfolio', href: '/portfolio' },
		{ label: 'Contact', href: '/contact' },
		{ label: 'Tes Counter', href: '/counter' },
		{ label: 'Changelog', href: '/changelog' }
	];
</script>

<Navbar navClass="px-2 px-4 py-2.5 mb-2 fixed w-full z-20 top-0 left-0 border-b">
	<NavBrand href="/">
		<span
			class="self-center whitespace-nowrap text-xl font-semibold
      dark:text-white">Galih's Profile!</span
		>
	</NavBrand>
	<NavHamburger on:click={() => (hidden1 = false)} />
	<NavUl>
		{#each dataNav as item}
			<NavLi href={item.href}>{item.label}</NavLi>
		{/each}
	</NavUl>
</Navbar>

<Drawer
	placement="right"
	transitionType="fly"
	{transitionParams}
	bind:hidden={hidden1}
	id="sidebar1"
>
	<div class="flex items-center">
		<CloseButton on:click={() => (hidden1 = true)} class="mb-4" />
	</div>
	<Sidebar color>
		<SidebarWrapper divClass="overflow-y-auto py-4 px-3 rounded">
			<SidebarGroup>
				{#each dataNav as item}
					<SidebarItem label={item.label} href={item.href}></SidebarItem>
				{/each}
			</SidebarGroup>
		</SidebarWrapper>
	</Sidebar>
</Drawer>
