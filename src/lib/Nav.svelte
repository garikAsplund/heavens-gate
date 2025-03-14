<script lang="ts">
	let { scrollY } = $props();
	let scrolled = $derived(scrollY > 50);
</script>

<svelte:window bind:scrollY />

<nav
	class="fixed top-0 z-50 w-full {scrolled
		? 'bg-white/30 shadow-sm backdrop-blur-md transition-all duration-800'
		: 'bg-transparent md:transition-all md:duration-800'}"
>
	<div class="container mx-auto px-4 py-4 md:px-6">
		<div class="relative flex items-center justify-center">
			<!-- Left Navigation Links -->
			<div class="flex items-center gap-4 md:space-x-10">
				<a
					href="#top"
					class="text-sm font-normal text-gray-900 transition hover:text-gray-600 md:text-lg md:font-bold"
					>Register</a
				><a
					href="#info"
					class="text-sm font-normal whitespace-nowrap text-gray-900 transition hover:text-gray-600 md:text-lg md:font-bold"
					>Race Info</a
				><a
					href="#map"
					class="text-sm font-normal text-gray-900 transition hover:text-gray-600 md:text-lg md:font-bold"
					>Course Map</a
				>
				<a
					href="#policies"
					class="text-sm font-normal whitespace-nowrap text-gray-900 transition hover:text-gray-600 md:text-lg md:font-bold"
					>Policies</a
				>
				<a
					href="https://www.facebook.com/groups/404550189608504"
					target="_blank"
					rel="noopener noreferrer"
					class="text-gray-800 transition hover:opacity-80"
					aria-label="Facebook"
				>
					<svg
						aria-label="IMTUF 100 on Facebook"
						fill="currentColor"
						height="24"
						role="img"
						viewBox="0 0 24 24"
						width="24"
						><title>IMTUF 100 on Facebook</title><circle
							cx="12"
							cy="12"
							fill="none"
							r="11.25"
							stroke="currentColor"
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="1.5"
						></circle><path
							d="M16.671 15.469 17.203 12h-3.328V9.749a1.734 1.734 0 0 1 1.956-1.874h1.513V4.922a18.452 18.452 0 0 0-2.686-.234c-2.741 0-4.533 1.66-4.533 4.668V12H7.078v3.469h3.047v7.885a12.125 12.125 0 0 0 3.75 0V15.47Z"
							fill-rule="evenodd"
						></path></svg
					>
				</a>
			</div>
		</div>
	</div>
</nav>
