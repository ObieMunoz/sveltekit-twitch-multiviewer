<script lang="ts">
	import { onMount } from 'svelte';
	import LiveStatus from '../LiveStatus/LiveStatus.svelte';

	export let channel: string;
	export let width = '100%';
	export let height = '100%';
	export let autoplay = true;
	export let muted = true;
	export let parent = 'localhost';
	export let id: string;
	export let live: boolean;

	let player: Twitch.Player;

	onMount(async () => {
		player = new Twitch.Player(`twitch-embed-${id}`, {
			channel,
			width,
			height,
			autoplay,
			muted,
			parent
		});
	});
</script>

<div id={`twitch-embed-${id}`} class="twitch-embed">
	<div class="live-marker">
		<LiveStatus {live} />
	</div>
</div>

<style>
	.twitch-embed {
		width: 500px;
		aspect-ratio: 16/9;
		position: relative;
	}

	.live-marker {
		position: absolute;
		top: 0;
		right: 0.5rem;
		z-index: 1;
	}
</style>
