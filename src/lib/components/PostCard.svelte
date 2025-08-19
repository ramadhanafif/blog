<script lang="ts">
	interface Post {
		id: string;
		title: string;
		excerpt: string;
		publishedAt: string;
		author: string;
		tags: string[];
		readTime?: string;
	}

	let { post }: { post: Post } = $props();

	function formatDate(dateString: string) {
		return new Date(dateString).toLocaleDateString('en-US', {
			year: 'numeric',
			month: 'long',
			day: 'numeric'
		});
	}
</script>

<article class="card bg-base-100 shadow-md hover:shadow-lg transition-shadow duration-300">
	<div class="card-body">
		<h2 class="card-title text-xl mb-3">
			<a href="/blog/{post.id}" class="link link-hover">{post.title}</a>
		</h2>

		<p class="text-base-content opacity-80 mb-4 line-clamp-3">
			{post.excerpt}
		</p>

		<div class="flex flex-wrap gap-2 mb-4">
			{#each post.tags as tag}
				<span class="badge badge-outline badge-sm">{tag}</span>
			{/each}
		</div>

		<div class="card-actions justify-between items-center">
			<div class="text-sm text-base-content opacity-60">
				<span>By {post.author}</span>
				<span class="mx-2">•</span>
				<span>{formatDate(post.publishedAt)}</span>
				{#if post.readTime}
					<span class="mx-2">•</span>
					<span>{post.readTime} read</span>
				{/if}
			</div>

			<a href="/blog/{post.id}" class="btn btn-primary btn-sm"> Read More </a>
		</div>
	</div>
</article>
