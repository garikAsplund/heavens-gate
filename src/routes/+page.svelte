<script lang="ts">
	import Countdown from '$lib/Countdown.svelte';
	import Course from '$lib/Map.svelte';
	import Hero from '$lib/Hero.svelte';
	import Info from '$lib/Info.svelte';
	import Policies from '$lib/Policies.svelte';
	import Shoutouts from '$lib/Shoutouts.svelte';
</script>

<Hero />
<Countdown />
<Info />
<Course />
<Policies />
<Shoutouts />
<enhanced:img
	src="/static/569.jpg?w=original;1500;500"
	alt="Above the Rapid River Fish Hatchery"
	class="h-[500px] w-full object-cover object-center"
	loading="lazy"
/>
