<script lang="ts">
	import { fade } from 'svelte/transition';
	import { onMount } from 'svelte';

	let { data } = $props();
	let videoEnded = $state<string | boolean | null>('false');
	let isMobile = $state(false);
	// $inspect(videoEnded);
	let navHeight: number = $state(0);

	onMount(() => {
		let navElement: HTMLDivElement = document.getElementById('nav');
		videoEnded = sessionStorage.getItem('visited');
		setTimeout(() => sessionStorage.setItem('visited', 'true'), 2000);

		function calculateNavHeight() {
			if (navElement) {
				navHeight = navElement.offsetHeight;
			}
		}

		function checkMobile() {
			isMobile = window.innerWidth < 768;
		}

		calculateNavHeight();
		checkMobile();

		window.addEventListener('resize', () => {
			calculateNavHeight();
			checkMobile();
		});

		return () => {
			window.removeEventListener('resize', calculateNavHeight);
		};
	});

	function handleVideoEnd() {
		videoEnded = 'true';
	}
</script>

<section
	class="relative flex w-full shrink-0 flex-col items-center justify-center"
	style="height: calc(90vh - {navHeight}px)"
>
	<div class="absolute inset-0 -z-10 h-full w-full bg-black object-cover"></div>
	{#if videoEnded === 'false' || videoEnded === null}
		<div class="absolute inset-0 z-10 h-full w-full bg-black/20 object-cover"></div>
		<video
			class="absolute inset-0 -z-10 h-full w-full object-cover"
			muted
			autoplay
			playsinline
			disablepictureinpicture
			poster="/still.avif"
			onended={handleVideoEnd}
		>
			{#if isMobile}
				<source src="/hero_mobile.webm" type="video/webm" />
				<source src="/hero_mobile.mp4" type="video/mp4" />
			{:else}
				<source src="/hero.webm" type="video/webm" />
				<source src="/hero.mp4" type="video/mp4" />
			{/if}
		</video>
	{:else}
		<div class="absolute inset-0 -z-10" transition:fade={{ duration: 1500 }}>
			<enhanced:img
				src="/static/hero.jpg"
				alt="The Seven Devils"
				class="h-full w-full object-cover object-center"
			/>
			<div
				class="absolute inset-0 z-0 bg-gradient-to-b from-transparent via-black/10 to-black/80 dark:to-black/40"
			></div>
		</div>
	{/if}
	<div
		class="z-20 flex h-full translate-y-24 flex-col items-center justify-center space-y-8 px-8 text-center"
	>
		<h1
			class="font-[Bangers] text-4xl font-semibold tracking-wider text-gray-100 drop-shadow-xl md:text-8xl"
		>
			Run Heavens Gate
		</h1>
		<h2 class="pt-8 font-serif text-xl text-gray-100 drop-shadow-lg md:text-4xl">
			In Idaho's Seven Devils Mountains
		</h2>
		<a
			href="https://ultrasignup.com/register.aspx?did=122883"
			target="_blank"
			rel="noopener noreferrer"
			class="mt-8 inline-block border-2 border-gray-200 bg-orange-400/40 px-10 py-3 text-xl font-semibold text-gray-100 drop-shadow backdrop-blur-xl transition-all duration-600 hover:bg-orange-400/60 hover:shadow-lg hover:shadow-orange-300/20 md:text-2xl"
		>
			Register Now
		</a>
		<p class="py-16 font-mono text-xl text-gray-200 drop-shadow-lg md:text-3xl">
			Saturday 3 May 2025
		</p>
	</div>
</section>
