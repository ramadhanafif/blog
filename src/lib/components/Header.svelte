<script lang="ts">
	// Navigation component for the blog
</script>

<header class="navbar bg-base-100 shadow-sm border-b border-base-300">
	<div class="container mx-auto">
		<div class="navbar-start">
			<div class="dropdown lg:hidden">
				<div tabindex="0" role="button" class="btn btn-ghost">
					<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M4 6h16M4 12h16M4 18h16"
						></path>
					</svg>
				</div>
				<ul
					class="menu menu-sm dropdown-content mt-3 z-[1] p-2 shadow bg-base-100 rounded-box w-52"
				>
					<li><a href="/">Home</a></li>
					<li><a href="/blog">Blog</a></li>
					<li><a href="/about">About</a></li>
					<li><a href="/contact">Contact</a></li>
				</ul>
			</div>
			<a href="/" class="btn btn-ghost text-xl font-bold">My Blog</a>
		</div>

		<div class="navbar-center hidden lg:flex">
			<ul class="menu menu-horizontal px-1">
				<li><a href="/" class="btn btn-ghost">Home</a></li>
				<li><a href="/blog" class="btn btn-ghost">Blog</a></li>
				<li><a href="/about" class="btn btn-ghost">About</a></li>
				<li><a href="/contact" class="btn btn-ghost">Contact</a></li>
			</ul>
		</div>

		<div class="navbar-end">
			<a href="/login" class="btn btn-primary btn-sm">Login</a>
		</div>
	</div>
</header>
