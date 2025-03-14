<script lang="ts">
	import USFS from '$lib/USFS.svelte';
</script>

<div class="w-full bg-gray-100 p-6 dark:bg-gray-800 py-24">
	<div class="mx-auto max-w-3xl text-center flex flex-col items-center">
		<div class="mb-6">
			<a 
				href="https://www.fs.usda.gov/nezperceclearwater" 
				class="inline-block transition-transform duration-300 hover:scale-[1.02] focus:outline-none focus:ring-2 focus:ring-blue-400 rounded-lg" 
				aria-label="Visit Nez-Perce Clearwater National Forest website"
				rel="noopener noreferrer"
				target="_blank"
			>
				<USFS />
			</a>
		</div>
		<p class="mb-3 text-lg font-medium text-gray-800 dark:text-gray-200">
			Our race is held under a special use permit granted by the <br />
			<a 
				href="https://www.fs.usda.gov/nezperceclearwater" 
				class="text-orange-600 hover:text-orange-700 dark:text-orange-300 dark:hover:text-orange-200 underline underline-offset-2 focus:outline-none focus:ring-2 focus:ring-orange-400 rounded-sm" 
				rel="noopener noreferrer"
				target="_blank"
			>
				Nez-Perce Clearwater National Forest
			</a>.
		</p>
		<p class="text-lg text-gray-700 italic dark:text-gray-300">
			Tread lightly on this beautiful land.
		</p>
	</div>
</div>