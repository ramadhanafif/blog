<script lang="ts">
	import { page } from '$app/stores';

	// In a real app, this would fetch from Directus based on the slug
	const post = {
		id: $page.params.slug,
		title: 'Getting Started with SvelteKit and Directus',
		content: `
			<p>Building modern web applications requires the right tools and frameworks. In this comprehensive guide, we'll explore how to create a powerful blog using SvelteKit as our frontend framework and Directus as our headless CMS.</p>
			
			<h2>Why SvelteKit?</h2>
			<p>SvelteKit offers several advantages for modern web development:</p>
			<ul>
				<li>Minimal runtime overhead</li>
				<li>Excellent developer experience</li>
				<li>Built-in SSR and static generation</li>
				<li>File-based routing</li>
			</ul>
			
			<h2>Setting Up Directus</h2>
			<p>Directus provides a user-friendly interface for content management while offering powerful APIs for developers. Here's how to get started:</p>
			
			<ol>
				<li>Install Directus locally or use their cloud service</li>
				<li>Configure your content collections</li>
				<li>Set up authentication and permissions</li>
				<li>Create your first content items</li>
			</ol>
			
			<h2>Connecting SvelteKit to Directus</h2>
			<p>The integration between SvelteKit and Directus is straightforward using the Directus SDK. This allows for seamless data fetching and real-time updates.</p>
			
			<h2>Conclusion</h2>
			<p>This combination of SvelteKit and Directus provides a robust foundation for building modern, scalable web applications. The developer experience is excellent, and the performance benefits are significant.</p>
		`,
		publishedAt: '2024-01-15',
		author: 'John Doe',
		tags: ['SvelteKit', 'Directus', 'Tutorial'],
		readTime: '8 min'
	};

	function formatDate(dateString: string) {
		return new Date(dateString).toLocaleDateString('en-US', {
			year: 'numeric',
			month: 'long',
			day: 'numeric'
		});
	}
</script>

<svelte:head>
	<title>{post.title} - My Blog</title>
	<meta
		name="description"
		content="Learn how to build a modern blog using SvelteKit as the frontend framework and Directus as a headless CMS."
	/>
</svelte:head>

<article class="container mx-auto px-4 py-12 max-w-4xl">
	<!-- Article Header -->
	<header class="text-center mb-12">
		<h1 class="text-4xl lg:text-5xl font-bold text-base-content mb-6 leading-tight">
			{post.title}
		</h1>

		<div class="flex flex-wrap justify-center items-center gap-4 text-base-content opacity-70 mb-6">
			<span>By {post.author}</span>
			<span class="hidden sm:inline">•</span>
			<span>{formatDate(post.publishedAt)}</span>
			<span class="hidden sm:inline">•</span>
			<span>{post.readTime} read</span>
		</div>

		<div class="flex flex-wrap justify-center gap-2">
			{#each post.tags as tag}
				<span class="badge badge-primary badge-outline">{tag}</span>
			{/each}
		</div>
	</header>

	<!-- Article Content -->
	<div class="prose prose-lg max-w-none mx-auto">
		{@html post.content}
	</div>

	<!-- Article Footer -->
	<footer class="mt-16 pt-8 border-t border-base-300">
		<div class="flex flex-col lg:flex-row justify-between items-start lg:items-center gap-6">
			<div class="flex items-center gap-4">
				<div class="avatar placeholder">
					<div class="bg-neutral text-neutral-content rounded-full w-12">
						<span class="text-lg">{post.author.charAt(0)}</span>
					</div>
				</div>
				<div>
					<h3 class="font-semibold text-base-content">{post.author}</h3>
					<p class="text-sm text-base-content opacity-60">Content Creator & Developer</p>
				</div>
			</div>

			<div class="flex gap-2">
				<button class="btn btn-outline btn-sm">
					<svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
						<path
							d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"
						/>
					</svg>
					Share
				</button>
				<button class="btn btn-outline btn-sm">
					<svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"
						></path>
					</svg>
					Like
				</button>
			</div>
		</div>
	</footer>

	<!-- Navigation to other posts -->
	<nav class="mt-16 pt-8 border-t border-base-300">
		<div class="flex flex-col lg:flex-row justify-between gap-6">
			<a href="/blog/2" class="btn btn-outline flex-1 justify-start">
				<svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"
					></path>
				</svg>
				Previous: Styling with TailwindCSS
			</a>

			<a href="/blog" class="btn btn-primary"> All Posts </a>

			<a href="/blog/3" class="btn btn-outline flex-1 justify-end">
				Next: Building Responsive Layouts
				<svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"
					></path>
				</svg>
			</a>
		</div>
	</nav>
</article>
