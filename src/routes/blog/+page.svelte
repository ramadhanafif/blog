<script lang="ts">
	import PostCard from '$lib/components/PostCard.svelte';

	// Sample blog posts data (in a real app, this would come from Directus)
	const allPosts = [
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
		},
		{
			id: '4',
			title: 'Modern JavaScript ES2024 Features',
			excerpt:
				"Explore the latest JavaScript features that are changing how we write code. From pattern matching to pipeline operators, discover what's coming next.",
			publishedAt: '2024-01-03',
			author: 'Sarah Wilson',
			tags: ['JavaScript', 'ES2024', 'Features'],
			readTime: '12 min'
		},
		{
			id: '5',
			title: 'Optimizing Web Performance in 2024',
			excerpt:
				'Comprehensive guide to web performance optimization covering Core Web Vitals, lazy loading, and modern performance measurement techniques.',
			publishedAt: '2024-01-01',
			author: 'Alex Brown',
			tags: ['Performance', 'Web Vitals', 'Optimization'],
			readTime: '15 min'
		},
		{
			id: '6',
			title: 'Accessibility Best Practices for Modern Web Apps',
			excerpt:
				'Essential accessibility guidelines and techniques to make your web applications usable by everyone. Learn about ARIA, semantic HTML, and testing strategies.',
			publishedAt: '2023-12-28',
			author: 'Emily Davis',
			tags: ['Accessibility', 'ARIA', 'UX'],
			readTime: '11 min'
		}
	];

	// Filter and sort functionality
	let searchQuery = $state('');
	let selectedTag = $state('');

	// Get unique tags
	const allTags = [...new Set(allPosts.flatMap((post) => post.tags))].sort();

	// Filter posts based on search and tag
	const filteredPosts = $derived(() => {
		let posts = allPosts;

		if (searchQuery) {
			posts = posts.filter(
				(post) =>
					post.title.toLowerCase().includes(searchQuery.toLowerCase()) ||
					post.excerpt.toLowerCase().includes(searchQuery.toLowerCase()) ||
					post.author.toLowerCase().includes(searchQuery.toLowerCase())
			);
		}

		if (selectedTag) {
			posts = posts.filter((post) => post.tags.includes(selectedTag));
		}

		return posts;
	});
</script>

<svelte:head>
	<title>Blog Posts - My Blog</title>
	<meta
		name="description"
		content="Browse all blog posts covering web development, design, and technology topics."
	/>
</svelte:head>

<div class="container mx-auto px-4 py-12">
	<!-- Page Header -->
	<div class="text-center mb-12">
		<h1 class="text-4xl font-bold text-base-content mb-4">Blog Posts</h1>
		<p class="text-lg text-base-content opacity-70 max-w-2xl mx-auto">
			Explore articles on web development, design trends, and technology insights.
		</p>
	</div>

	<!-- Search and Filter Section -->
	<div class="flex flex-col lg:flex-row gap-4 mb-12 max-w-4xl mx-auto">
		<div class="flex-1">
			<input
				type="text"
				placeholder="Search posts..."
				class="input input-bordered w-full"
				bind:value={searchQuery}
			/>
		</div>

		<div class="lg:w-64">
			<select class="select select-bordered w-full" bind:value={selectedTag}>
				<option value="">All Categories</option>
				{#each allTags as tag}
					<option value={tag}>{tag}</option>
				{/each}
			</select>
		</div>
	</div>

	<!-- Results Count -->
	<div class="text-center mb-8">
		<p class="text-base-content opacity-60">
			{filteredPosts().length}
			{filteredPosts().length === 1 ? 'post' : 'posts'} found
		</p>
	</div>

	<!-- Posts Grid -->
	{#if filteredPosts().length > 0}
		<div class="grid gap-8 md:grid-cols-2 lg:grid-cols-3">
			{#each filteredPosts() as post}
				<PostCard {post} />
			{/each}
		</div>
	{:else}
		<div class="text-center py-16">
			<div class="text-6xl mb-4">📝</div>
			<h3 class="text-xl font-semibold text-base-content mb-2">No posts found</h3>
			<p class="text-base-content opacity-60 mb-6">
				Try adjusting your search terms or removing filters.
			</p>
			<button
				class="btn btn-primary"
				onclick={() => {
					searchQuery = '';
					selectedTag = '';
				}}
			>
				Clear Filters
			</button>
		</div>
	{/if}

	<!-- Load More Button (placeholder for pagination) -->
	{#if filteredPosts().length > 0}
		<div class="text-center mt-16">
			<button class="btn btn-outline btn-lg" disabled>
				Load More Posts
				<span class="badge badge-sm">Coming Soon</span>
			</button>
		</div>
	{/if}
</div>
