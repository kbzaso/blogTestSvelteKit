<script context="module">
	export const load = async ({ fetch }) => {
		try {
			const res = await fetch('/pages.json');
			const { pages } = await res.json();
			return { props: { pages } };
		} catch (err) {
			console.log('Hubo un error');
		}
	};
</script>

<script>
	import '../app.css';
	import Nav from '../components/Navbar.svelte';

	import { onMount } from 'svelte';
	import { themeChange } from 'theme-change';

	onMount(async () => {
		themeChange(false);
	});

	export let pages;
</script>

<Nav {pages} />
<main class="flex flex-col items-center m-auto">
	<slot />
</main>
