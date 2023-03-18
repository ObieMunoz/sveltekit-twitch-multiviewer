<script lang="ts">
	import { onMount } from 'svelte';
	import { isChannelLive } from '$lib/TwitchUtils';
	import TwitchChannelEmbed from '$lib/TwitchChannelEmbed/TwitchChannelEmbed.svelte';

	export let channels: Array<string> = [];

	const liveStatus: Array<boolean> = [];

	onMount(async () => {
		const promises = channels.map(isChannelLive);
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
			<TwitchChannelEmbed {channel} id={i.toString()} live={liveStatus[i]} />
		</div>
	{/if}
{/each}

<style>
	div {
		display: inline-flex;
		flex-direction: column;
		align-items: center;
		margin: 1rem;
	}
</style>
