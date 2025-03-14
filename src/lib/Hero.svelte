<script lang="ts">
	import { fade } from 'svelte/transition';
	import { Camera, ExternalLink } from 'lucide-svelte';
	import { onMount } from 'svelte';

	let scrollY = $state(0);

	let videoEnded = $state<string | boolean | null>('false');
	let isMobile = $state(false);
	let navHeight: number = $state(0);

	let showImageInfo = $state(false);
	let modalNode: HTMLDivElement | undefined = $state();
	let buttonNode: HTMLButtonElement | undefined = $state();

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

		const handleClickOutside = (event: MouseEvent) => {
			if (
				showImageInfo &&
				modalNode &&
				buttonNode &&
				!modalNode.contains(event.target as Node) &&
				!buttonNode.contains(event.target as Node)
			) {
				showImageInfo = false;
			}
		};

		document.addEventListener('mousedown', handleClickOutside);

		return () => {
			window.removeEventListener('resize', calculateNavHeight);
			document.removeEventListener('mousedown', handleClickOutside);
		};
	});

	function handleVideoEnd() {
		videoEnded = 'true';
	}
</script>

<svelte:window bind:scrollY />

<section
	class="relative flex w-full shrink-0 flex-col items-center justify-center overflow-hidden"
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
            aria-hidden="true"
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
			<div class="fixed inset-0 h-[110%] w-full overflow-hidden">
				<enhanced:img
					src="/static/hero.jpg"
					alt="The Seven Devils"
					class="h-full w-full object-cover object-center"
                    loading="eager"
                    fetchpriority="high"
				/>
			</div>
			<div
				class="fixed inset-0 z-10 bg-gradient-to-b from-transparent via-black/10 to-black/80"
			></div>
		</div>
		<button
			bind:this={buttonNode}
			class="absolute right-3 bottom-3 z-20 cursor-pointer rounded-full bg-black/30 p-2 transition-colors hover:bg-black/40 sm:right-4 sm:bottom-4"
			onclick={() => (showImageInfo = !showImageInfo)}
			aria-label="Show image information"
		>
			<Camera class="h-5 w-5 text-white" />
		</button>
		{#if showImageInfo}
			<div
				bind:this={modalNode}
				class="absolute right-3 bottom-14 z-20 mx-3 max-w-[calc(100%-24px)] bg-black px-4 py-2 text-sm text-white sm:right-4 sm:bottom-16 sm:mx-4 sm:max-w-md md:bg-black/50"
				transition:fade
			>
				<p class="mb-2">Seven Devils Sunrise</p>
				<a
					href="https://www.flickr.com/photos/194908364@N07/52000492546/in/photolist-2ne77Lj-ZRc1xh-2hj5AAY-2k5PYAu-7aMq4r-2ge1hLV-4MZz3e-2nRkxPQ-pUKKmq-2kHRyRt-2kTenkm-pVRMyd-Jge93F-2mRPgYx-vCSF6-SXnPSb-2gH2xoG-KegTRX-pVZHkD-2gHAL8o-2hFBD6Q-TMWWr3-2iCDG7W-2g51jtH-2hQRmFE-2oaEYvp-2mRpV8r-26CJZCd-2odNrpV-j3URP3-28x57nW-28xsFZH-2nvM4St-rhBppZ-2hDc1VN-2nChk2m-2gM8kUD-2mVmvtz-2nuWdVk-26CJVm7-2jsqer5-2nKwwiN-2mXZVTb-2mYv4uz-2neqMqy-2kGJKdV-2nGapAm-21eZy5X-9Awroe-pVjvy1"
					target="_blank"
					rel="noopener noreferrer"
					class="inline-flex items-center gap-2 border-b border-current hover:text-gray-200"
				>
					Photo by Brian Haagan
					<ExternalLink class="h-4 w-4" />
				</a>
			</div>
		{/if}
	{/if}
	<div
		class="z-20 flex h-full translate-y-24 flex-col items-center justify-center space-y-8 px-8 text-center"
		style="transform: translateY(calc(24px - {scrollY * 0.4}px));"
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
