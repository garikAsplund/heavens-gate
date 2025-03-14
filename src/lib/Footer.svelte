<script lang="ts">
	import Watermark from '$lib/Watermark.svelte';

	let { scrollY } = $props();
</script>

<div
	class="fixed inset-0 -z-5 bg-white transition-opacity duration-300"
	style="opacity: {scrollY > 1000 ? '1' : '0'}"
></div>

<footer class="flex w-full flex-col bg-white">
	<div class="absolute start-0 bottom-0 pl-2">
		<enhanced:img
			src="/static/do.png"
			alt="Not that Heaven's Gate"
			class="h-24 w-auto opacity-50"
			loading="lazy"
		/>
	</div>
	<div class="absolute end-0 bottom-0">
		<enhanced:img
			src="/static/nikes.webp?w=200;100"
			alt="Not that Heaven's Gate"
			class="h-24 w-auto opacity-80"
			loading="lazy"
		/>
	</div>
	<Watermark />
</footer>
