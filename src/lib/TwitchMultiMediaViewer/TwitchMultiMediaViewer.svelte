<script lang="ts">
	import { onMount } from 'svelte';
	import { checkLive } from '$lib/TwitchUtils';
	import TwitchFrame from '$lib/TwitchFrame/TwitchFrame.svelte';

	export let channels: Array<string> = [];

	const liveStatus: Array<boolean> = [];

	onMount(async () => {
		const promises = channels.map(checkLive);
		const results = await Promise.allSettled(promises);
		results.forEach((result, i) => {
			if (result.status === 'fulfilled') {
				liveStatus[i] = result.value;
			} else {
				liveStatus[i] = false;
			}
		});
	});
</script>

{#each channels as channel, i}
	{#if typeof liveStatus[i] !== 'undefined'}
		<div>
			{channel}
			<TwitchFrame {channel} id={i.toString()} live={liveStatus[i]} />
		</div>
	{/if}
{/each}

<style>
	div,
	h2,
	p {
		margin: 0;
	}

	div {
		display: inline-flex;
		flex-direction: column;
		align-items: center;
		margin: 1rem;
	}
</style>
