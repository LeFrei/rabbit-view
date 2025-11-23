<script>
	import { pb } from '$lib/store.svelte';
	let { rabbithole } = $props();
	let id = $state();
	let rabbitholes = $state([]);

	$effect(async () => {
		rabbitholes = await pb.collection('rabbitholes').getFullList();
	});
</script>

<div>
	<label for="name">Hasenbau</label>
	<select class="select" bind:value={id} onchange={() => rabbithole(id)}>
		{#each rabbitholes as rabbithole (rabbithole.id)}
			<option value={rabbithole.id}>{rabbithole.name}</option>
		{/each}
	</select>
</div>
