<script lang="ts">
	import TwitchChannelGrid from '$lib/TwitchChannelGrid/TwitchChannelGrid.svelte';

	let channels = ['theprimeagen', 'teej_dv', 'bashbunni', 'roxcodes'];
</script>

<TwitchChannelGrid {channels} />
