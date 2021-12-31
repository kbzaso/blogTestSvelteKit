<script context="module">
	export const load = async ({ fetch }) => {
		try {
			const res = await fetch('/posts.json');
			const { posts } = await res.json();
			return { props: { posts } };
		} catch (err) {
			console.log('Hubo un error');
		}
	};
</script>

<script>
	export let posts;
</script>

<svelte:head>
	<title>Blog | Bienvenido</title>
</svelte:head>

<div class="container w-10/12 mx-auto flex flex-col items-center">
	<h1 class="text-4xl mb-5 mt-10 font-extrabold">Welcome to SvelteKit</h1>
	<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

	<div class="py-4 mt-10 flex flex-wrap gap-4">
		{#each posts as { title, coverImage, excerpt, tags, slug, author }}
			<div class="card card-bordered grow w-96 ">
				<figure>
					<img src={coverImage.url} alt={title} />
				</figure>
				<div class="card-body relative">
					<div class="badge mb-2 badge-secondary">{tags}</div>
					<h2 class="card-title">
						{title}
					</h2>
					<p class="mb-16">{excerpt}</p>

					<div class="avatar absolute bottom-6 left-6">
						<div class=" rounded-full w-10 h-10">
							<img src={author.picture.url} alt={title} />
						</div>
						<p class="ml-2 mt-1">{author.name}</p>
					</div>

					<div class="justify-end card-actions absolute bottom-6 right-6">
						<a href={`/posts/${slug}`} class="btn btn-secondary">More info</a>
					</div>
				</div>
			</div>
		{/each}
	</div>
</div>
