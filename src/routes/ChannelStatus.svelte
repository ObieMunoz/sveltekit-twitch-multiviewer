<script lang="ts">
	export let live: boolean;
</script>

{#if live}
	<p class="live">LIVE</p>
{:else}
	<p class="offline">OFFLINE</p>
{/if}

<style>
	.live {
		padding: 0.2rem;
		background-color: red;
		color: white;
		height: fit-content;
		width: fit-content;
		border-radius: 0.2rem;
		text-transform: uppercase;
		font-weight: 700;
		font-family: Arial, Helvetica, sans-serif;
		letter-spacing: 0.05rem;
		line-height: 19.5px;
		font-size: 13px;
	}

	.offline {
		padding: 0.2rem;
		background-color: black;
		height: fit-content;
		color: white;
		width: fit-content;
		border-radius: 0.2rem;
		text-transform: uppercase;
		font-weight: 700;
		font-family: Arial, Helvetica, sans-serif;
		letter-spacing: 0.05rem;
		line-height: 19.5px;
		font-size: 13px;
	}
</style>
