<script lang="ts">
	import { directus } from '$lib';

	let authState: 'Idle' | 'Pending' | 'Success' | 'Error' = $state('Idle');

	async function handleSubmit(event: SubmitEvent) {
		event.preventDefault();

		try {
			const formData = new FormData(event.target as HTMLFormElement);
			const email = (formData.get('email') as string) ?? '';
			const password = (formData.get('password') as string) ?? '';

			authState = 'Pending';
			const res = await directus.login({ email, password });
			$inspect(res);

			authState = 'Success';
		} catch (err) {
			console.log(err);
			authState = 'Error';
		}
	}
</script>

<div class="bg-base-100 flex justify-center items-center min-h-screen">
	<div class="p-8 bg-base-200 rounded-lg shadow-md w-full max-w-sm">
		<h2 class=" text-2xl font-bold text-center mb-6 text-base-content">Login</h2>
		<form onsubmit={handleSubmit}>
			<fieldset class="mb-4 fieldset">
				<legend class="text-sm font-semibold mb-2 block">Email</legend>
				<input type="email" name="email" class="input" />
			</fieldset>

			<fieldset class="mb-4 fieldset">
				<legend class="text-sm font-semibold mb-2 block">Password</legend>
				<input type="password" name="password" class="input" />
			</fieldset>

			<button type="submit" class="btn btn-primary btn-block mb-2">
				{#if authState === 'Pending'}
					<span class="loading loading-spinner mx-2"></span>
					Login
				{:else if authState === 'Success'}
					Logged in!
				{:else}
					Login
				{/if}
			</button>
		</form>
		<div class="">
			<p class="text-sm text-error">
				&nbsp;
				{#if authState === 'Error'}
					Invalid username or password!
				{/if}
			</p>
		</div>
	</div>
</div>
