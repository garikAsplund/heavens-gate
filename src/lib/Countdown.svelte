<!-- Countdown.svelte -->
<script>
	const { raceDate = new Date('2025-05-03T00:00:00'), title = 'Countdown to Race Day!' } = $props();

	let days = $state(0);
	let hours = $state(0);
	let minutes = $state(0);
	let seconds = $state(0);
	let intervalId;

	function updateCountdown() {
		const now = new Date();
		const difference = raceDate - now;

		if (difference > 0) {
			days = Math.floor(difference / (1000 * 60 * 60 * 24));
			hours = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
			minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
			seconds = Math.floor((difference % (1000 * 60)) / 1000);
		} else {
			// Race day has arrived
			days = 0;
			hours = 0;
			minutes = 0;
			seconds = 0;
		}
	}

	$effect(() => {
		// Initial calculation
		updateCountdown();

		// Update every second
		intervalId = setInterval(updateCountdown, 1000);

		return () => {
			if (intervalId) clearInterval(intervalId);
		};
	});
</script>

<div class="w-full bg-black p-6 pb-24 text-white">
	<h2 class="mb-8 text-center text-3xl font-bold italic">{title}</h2>

	<!-- 2x2 Grid Layout -->
	<div class="mx-auto grid max-w-2xl grid-cols-2 gap-6 md:grid-cols-4 md:gap-8">
		<!-- Days -->
		<div class="relative flex flex-col items-center">
			<div
				class="flex h-24 w-24 items-center justify-center rounded-full border-4 border-white bg-black md:h-32 md:w-32"
			>
				<span class="text-4xl font-bold md:text-5xl">{days}</span>
			</div>
			<svg
				class="absolute top-0 left-1/2 h-24 w-24 -translate-x-1/2 md:h-32 md:w-32"
				viewBox="0 0 100 100"
			>
				<circle
					cx="50"
					cy="50"
					r="45"
					fill="none"
					stroke="white"
					stroke-width="10"
					stroke-dasharray={`${Math.min(days / 365, 1) * 283} 283`}
					stroke-dashoffset="0"
					transform="rotate(-90 50 50)"
				/>
			</svg>
			<p class="mt-2 text-center text-xl">DAYS</p>
		</div>

		<!-- Hours -->
		<div class="relative flex flex-col items-center">
			<div
				class="flex h-24 w-24 items-center justify-center rounded-full border-4 border-white bg-black md:h-32 md:w-32"
			>
				<span class="text-4xl font-bold md:text-5xl">{hours}</span>
			</div>
			<svg
				class="absolute top-0 left-1/2 h-24 w-24 -translate-x-1/2 md:h-32 md:w-32"
				viewBox="0 0 100 100"
			>
				<circle
					cx="50"
					cy="50"
					r="45"
					fill="none"
					stroke="white"
					stroke-width="10"
					stroke-dasharray={`${(hours / 24) * 283} 283`}
					stroke-dashoffset="0"
					transform="rotate(-90 50 50)"
				/>
			</svg>
			<p class="mt-2 text-center text-xl">HOURS</p>
		</div>

		<!-- Minutes -->
		<div class="relative flex flex-col items-center">
			<div
				class="flex h-24 w-24 items-center justify-center rounded-full border-4 border-white bg-black md:h-32 md:w-32"
			>
				<span class="text-4xl font-bold md:text-5xl">{minutes}</span>
			</div>
			<svg
				class="absolute top-0 left-1/2 h-24 w-24 -translate-x-1/2 md:h-32 md:w-32"
				viewBox="0 0 100 100"
			>
				<circle
					cx="50"
					cy="50"
					r="45"
					fill="none"
					stroke="white"
					stroke-width="10"
					stroke-dasharray={`${(minutes / 60) * 283} 283`}
					stroke-dashoffset="0"
					transform="rotate(-90 50 50)"
				/>
			</svg>
			<p class="mt-2 text-center text-xl">MINUTES</p>
		</div>

		<!-- Seconds -->
		<div class="relative flex flex-col items-center">
			<div
				class="flex h-24 w-24 items-center justify-center rounded-full border-4 border-white bg-black md:h-32 md:w-32"
			>
				<span class="text-4xl font-bold md:text-5xl">{seconds}</span>
			</div>
			<svg
				class="absolute top-0 left-1/2 h-24 w-24 -translate-x-1/2 md:h-32 md:w-32"
				viewBox="0 0 100 100"
			>
				<circle
					cx="50"
					cy="50"
					r="45"
					fill="none"
					stroke="white"
					stroke-width="10"
					stroke-dasharray={`${(seconds / 60) * 283} 283`}
					stroke-dashoffset="0"
					transform="rotate(-90 50 50)"
				/>
			</svg>
			<p class="mt-2 text-center text-xl">SECONDS</p>
		</div>
	</div>

	<!-- Sponsor Section: Clean and Classy Design -->
    <div class="mt-12 flex flex-col items-center">
        <p class="text-lg text-gray-300 uppercase tracking-wider mb-4">Presented By</p>
        <a 
          href="https://idahorunningcompany.com/" 
          target="_blank" 
          rel="noopener noreferrer" 
          class="group transition-all duration-300"
        >
          <div class="bg-white rounded-lg px-8 py-4 hover:bg-gray-100 transition-all duration-300 shadow-lg">
            <p class="text-2xl md:text-3xl font-bold text-black text-center">
              Shu's Idaho Running Company
              <span class="block h-0.5 w-0 group-hover:w-full bg-orange-600 transition-all duration-500"></span>
            </p>
          </div>
        </a>
      </div>
</div>
