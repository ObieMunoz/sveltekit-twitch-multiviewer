<script lang="ts">
	import TwitchMultiMediaViewer from '$lib/TwitchMultiMediaViewer/TwitchMultiMediaViewer.svelte';

	let channels = ['theprimeagen', 'teej_dv', 'bashbunni', 'roxcodes'];
</script>

<TwitchMultiMediaViewer {channels} />
