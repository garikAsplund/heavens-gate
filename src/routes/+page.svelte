<script lang="ts">
	import Countdown from '$lib/Countdown.svelte';
	import Course from '$lib/Map.svelte';
	import Hero from '$lib/Hero.svelte';
	import Info from '$lib/Info.svelte';
	import Policies from '$lib/Policies.svelte';
</script>

<Hero />
<Countdown sponsor="Shu's Idaho Running Company" />
<Info />
<Course />
<Policies />
<enhanced:img src="/static/569.jpg" alt="Above the Rapid River Fish Hatchery" class="h-[500px] w-full object-cover object-center"/>