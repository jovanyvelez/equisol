<script lang="ts">
	import { goto } from '$app/navigation';
    import { superForm } from 'sveltekit-superforms/client';
	import SuperDebug from 'sveltekit-superforms/client/SuperDebug.svelte';
	export let data;
	const { form, errors, enhance } = superForm(data.form);
    async function changePage (){
        goto('/register')
    }
</script>


<h1 class="text-center">Ingreso</h1>

<!--SuperDebug data={$form}/-->
<div class="px-4 pt-8 flex flex-col w-full place-items-center">
	<form action="?/login" method="post" use:enhance>
		<div>
			<label for="email" class="label">Email</label>
			<input
				id="email"
				name="email"
				type="text"
				bind:value={$form.email}
				class="input input-md input-warning input-bordered rounded-md w-full max-w-xs"
			/>
		</div>

		{#if $errors.email}
			<small class="text-red-500">{$errors.email}</small>
		{/if}

		<div>
			<label for="password" class="label">Password</label>
			<input
				id="password"
				name="password"
				type="password"
				bind:value={$form.password}
				class="input input-warning input-bordered w-full max-w-xs"
			/>
		</div>

		{#if $errors.password}
			<small class="text-red-500">{$errors.password}</small>
		{/if}

		<div class="w-full flex justify-center">
			<button type="submit" class="btn btn-xs w-full mt-4">Ingresar</button>
		</div>
	</form>

	<div class="px-4 pt-8 flex flex-col w-full place-items-center">
		<p class="m-2">--------- O ---------</p>
		<div class="w-full flex justify-center h-15">
			<button class="btn btn-outline btn-wide btn-warning btn- btn-xs mt-4"
                    on:click={()=>changePage()}>Regitrarse</button>
		</div>
	</div>
</div>