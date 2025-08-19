<script lang="ts">
	import PostCard from '$lib/components/PostCard.svelte';

	// Sample blog posts data (in a real app, this would come from Directus)
	const featuredPosts = [
		{
			id: '1',
			title: 'Getting Started with SvelteKit and Directus',
			excerpt:
				'Learn how to build a modern blog using SvelteKit as the frontend framework and Directus as a headless CMS. This comprehensive guide covers setup, configuration, and best practices.',
			publishedAt: '2024-01-15',
			author: 'John Doe',
			tags: ['SvelteKit', 'Directus', 'Tutorial'],
			readTime: '8 min'
		},
		{
			id: '2',
			title: 'Styling with TailwindCSS and DaisyUI',
			excerpt:
				'Discover the power of utility-first CSS with TailwindCSS and the beautiful components provided by DaisyUI. Perfect for rapid prototyping and consistent design systems.',
			publishedAt: '2024-01-10',
			author: 'Jane Smith',
			tags: ['CSS', 'TailwindCSS', 'DaisyUI', 'Design'],
			readTime: '6 min'
		},
		{
			id: '3',
			title: 'Building Responsive Layouts in 2024',
			excerpt:
				'Modern techniques for creating responsive web layouts that work seamlessly across all devices. From mobile-first design to advanced CSS Grid layouts.',
			publishedAt: '2024-01-05',
			author: 'Mike Johnson',
			tags: ['Responsive Design', 'CSS Grid', 'Mobile'],
			readTime: '10 min'
		}
	];
</script>

<svelte:head>
	<title>My Blog - Welcome</title>
	<meta
		name="description"
		content="Welcome to my blog where I share insights about web development, design, and technology."
	/>
</svelte:head>

<!-- Hero Section -->
<section class="hero min-h-[60vh] bg-gradient-to-br from-primary/10 to-secondary/10">
	<div class="hero-content text-center">
		<div class="max-w-md">
			<h1 class="text-5xl font-bold text-base-content">Welcome to My Blog</h1>
			<p class="py-6 text-lg text-base-content opacity-80">
				Discover insights, tutorials, and thoughts on web development, design, and technology. Join
				me on this journey of continuous learning and sharing.
			</p>
			<div class="flex gap-4 justify-center">
				<a href="/blog" class="btn btn-primary">Read Blog Posts</a>
				<a href="/about" class="btn btn-outline">About Me</a>
			</div>
		</div>
	</div>
</section>

<!-- Featured Posts Section -->
<section class="container mx-auto px-4 py-16">
	<div class="text-center mb-12">
		<h2 class="text-3xl font-bold text-base-content mb-4">Featured Posts</h2>
		<p class="text-lg text-base-content opacity-70 max-w-2xl mx-auto">
			Check out some of my latest and most popular blog posts covering various topics in web
			development and design.
		</p>
	</div>

	<div class="grid gap-8 md:grid-cols-2 lg:grid-cols-3">
		{#each featuredPosts as post}
			<PostCard {post} />
		{/each}
	</div>

	<div class="text-center mt-12">
		<a href="/blog" class="btn btn-primary btn-lg">
			View All Posts
			<svg class="w-5 h-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
				<path
					stroke-linecap="round"
					stroke-linejoin="round"
					stroke-width="2"
					d="M13 7l5 5m0 0l-5 5m5-5H6"
				></path>
			</svg>
		</a>
	</div>
</section>

<!-- Newsletter Section -->
<section class="bg-base-200 py-16">
	<div class="container mx-auto px-4 text-center">
		<h2 class="text-3xl font-bold text-base-content mb-4">Stay Updated</h2>
		<p class="text-lg text-base-content opacity-70 mb-8 max-w-2xl mx-auto">
			Subscribe to my newsletter to get the latest posts delivered directly to your inbox.
		</p>

		<div class="flex flex-col sm:flex-row gap-4 justify-center max-w-md mx-auto">
			<input type="email" placeholder="Enter your email" class="input input-bordered flex-1" />
			<button class="btn btn-primary">Subscribe</button>
		</div>

		<p class="text-sm text-base-content opacity-60 mt-4">No spam, unsubscribe at any time.</p>
	</div>
</section>
