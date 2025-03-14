<script>
	import { onMount } from 'svelte';

	let mapContainer = $state();

	onMount(() => {
		const overlay = document.getElementById('map-overlay');
		const map = document.getElementById('caltopoMap');
		let interactionTimeout;

		// Remove overlay when clicked
		overlay.addEventListener('click', function () {
			overlay.classList.add('hidden');
			map.focus(); // Focus the map for better keyboard control

			// Set a timer to re-enable the overlay after period of inactivity
			clearTimeout(interactionTimeout);
			interactionTimeout = setTimeout(function () {
				overlay.classList.remove('hidden');
			}, 15000); // Re-enable after 30 seconds of inactivity
		});

		// Reset the timer when user interacts with the map
		map.addEventListener('mousemove', function () {
			if (overlay.classList.contains('hidden')) {
				clearTimeout(interactionTimeout);
				interactionTimeout = setTimeout(function () {
					overlay.classList.remove('hidden');
				}, 15000);
			}
		});

		// Create a button to manually re-enable the overlay
		const lockButton = document.createElement('button');
		lockButton.textContent = 'Lock Map';
		lockButton.className =
			'absolute bottom-2 right-2 px-2 py-1 text-sm bg-white dark:bg-gray-700 dark:text-white border border-gray-300 dark:border-gray-600 rounded z-10 cursor-pointer shadow-sm';
		mapContainer.appendChild(lockButton);

		lockButton.addEventListener('click', function () {
			overlay.classList.remove('hidden');
			clearTimeout(interactionTimeout);
		});
	});
</script>

<!-- Container with relative positioning -->
<section id="map" class="scroll-mt-16">
	<div class="relative h-[60vh] w-full" bind:this={mapContainer}>
		<!-- The CalTopo iframe -->
		<iframe
			src="https://caltopo.com/m/3P2011E"
			title="Heavens Gate 20 miler and 15 km race courses"
			class="h-full w-full border-0 dark:brightness-[80%]"
			id="caltopoMap"
		></iframe>

		<!-- Clickable overlay -->
		<div
			id="map-overlay"
			class="absolute inset-0 z-10 flex cursor-pointer items-center justify-center"
		>
			<div
				class="bg-opacity-80 dark:bg-opacity-80 -translate-y-24 rounded-md bg-white px-5 py-3 shadow-md dark:bg-gray-800 dark:text-white"
			>
				Click to interact with map
			</div>
		</div>
	</div>
</section>
