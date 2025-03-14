<script lang="ts">
	// Add any imports or props here if needed
</script>

<section class="w-full bg-gradient-to-b from-gray-100 to-gray-200 py-16 dark:from-gray-800 dark:to-gray-900 scroll-mt-16" id="info">
	<div class="container mx-auto max-w-6xl px-4">
		<h2 class="mb-10 text-center font-serif text-3xl font-bold text-gray-800 dark:text-gray-100 md:text-4xl">
			Course Information
		</h2>

		<div class="grid gap-8 md:grid-cols-2">
			<!-- 20 Mile Course Card -->
			<div class="relative overflow-hidden rounded-lg bg-white shadow-xl dark:bg-gray-800">
				<div class="absolute -right-10 -top-10 h-40 w-40 rounded-full bg-orange-500/20"></div>
				<div class="relative flex flex-col h-full z-10 p-6">
					<div class="mb-4 flex items-center justify-between">
						<div>
							<h3 class="font-serif text-2xl font-bold text-gray-800 dark:text-gray-100">20 Mile Course</h3>
							<span class="text-sm font-medium text-orange-600 dark:text-orange-400">Start Time: 8:00 <span class="text-xs uppercase tracking-wide">AM MDT</span></span>
						</div>
						<span class="rounded-full bg-orange-100 px-4 py-1 text-sm font-semibold text-orange-800 dark:bg-orange-900 dark:text-orange-200">
							7,500 ft. Elevation Gain
						</span>
					</div>
					<div class="mb-4 h-64 w-full overflow-hidden rounded-lg bg-gray-200 dark:bg-gray-700">
						<enhanced:img
							src="/static/20.jpg"
							alt="20 Mile Course Elevation Profile"
							class="h-full w-full object-cover"
						/>
					</div>
					<div class="space-y-3 text-gray-700 dark:text-gray-300">
						<p class="font-medium">
							Count on the most beautiful and pristine canyon trails you have ever seen with giant vertical gain.
						</p>
						<p>
							Launch into the open country alpine realm of Cannonball Mountain. This is a very serious
							mountain race with more climbing than many 50-100 mile races.
						</p>
						<p>
							There is actually plenty of flat to rolling terrain, which means the actual hills are
							even steeper than it sounds. Be ready for real mountain racing!
						</p>
					</div>
                    <div class="mt-auto w-full overflow-hidden rounded-lg bg-gray-200 dark:bg-gray-700">
						<enhanced:img
							src="/static/20.png"
							alt="20M Course Elevation Profile"
							class="h-full w-full object-contain"
						/>
					</div>
				</div>
			</div>

			<!-- 15K Course Card -->
			<div class="relative overflow-hidden  rounded-lg bg-white shadow-xl dark:bg-gray-800">
				<div class="absolute -right-10 -top-10 h-40 w-40 rounded-full bg-green-500/20"></div>
				<div class="relative z-10 p-6 flex flex-col h-full">
					<div class="mb-4 flex items-center justify-between">
						<div>
							<h3 class="font-serif text-2xl font-bold text-gray-800 dark:text-gray-100">15K Course</h3>
							<span class="text-sm font-medium text-orange-600 dark:text-orange-400">Start Time: 9:00 AM MDT</span>
						</div>
						<span class="rounded-full bg-orange-100 px-4 py-1 text-sm font-semibold text-orange-800 dark:bg-orange-900 dark:text-orange-200">
							4,000 ft. Elevation Gain
						</span>
					</div>
					<div class="mb-4 h-64 w-full overflow-hidden rounded-lg bg-gray-200 dark:bg-gray-700">
						<enhanced:img
							src="/static/15.jpg"
							alt="15K Course Elevation Profile"
							class="h-full w-full object-cover object-top"
						/>
					</div>
					<div class="space-y-3 text-gray-700 dark:text-gray-300">
						<p class="font-medium">
							Experience jaw-dropping views and unforgettable mountain running terrain on this challenging course.
						</p>
						<p>
							While shorter than the 20-mile option, the 15K still packs serious vertical gain in a
							compact distance.
						</p>
						<p>
							This course offers abundant wildlife viewing opportunities and access to pristine trails 
							rarely seen by the general public.
						</p>
					</div>
                    <div class="mt-auto w-full overflow-hidden rounded-lg bg-gray-200 dark:bg-gray-700">
						<enhanced:img
							src="/static/15.png"
							alt="15K Course Elevation Profile"
							class="h-full w-full object-contain"
						/>
					</div>
				</div>
			</div>
		</div>
	</div>
    <a href="https://maps.app.goo.gl/JNntjqmwrhEKNmyJ6">Directions</a>
</section>