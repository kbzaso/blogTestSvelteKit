<script>
	export let pages;
</script>

<div class="navbar m-10 mb-2 shadow-lg bg-neutral text-neutral-content rounded-box">
	<div class="px-2 mx-2 navbar-start">
		<a href="/" class="text-lg font-bold"> SP Blog</a>
	</div>

	<div class="mx-2 px-2 navbar-end" />
	<div class="flex items-stretch">
		<a href="/" class="btn btn-ghost btn-sm rounded-btn"> Home </a>
		{#each pages as { title, slug }}
			<a href={`/${slug}`} class="btn btn-ghost btn-sm rounded-btn"> {title} </a>
		{/each}
	</div>
</div>
