<!-- Countdown.svelte -->
<script>
    // Svelte 5 syntax using $props
    const { 
      raceDate = new Date('2025-05-03T00:00:00'),
      title = "Countdown to Race Day!",
      sponsor = "", // Optional sponsor name
      sponsorLabel = "Official Timekeeper" // Label for sponsor
    } = $props();
    
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
  
  <div class="w-full bg-black text-white p-6 pb-24">
    <h2 class="text-center text-3xl mb-8 font-bold italic">{title}</h2>
    
    <div class="flex flex-wrap justify-center gap-4 md:gap-8">
      <!-- Days -->
      <div class="relative">
        <div class="w-24 h-24 md:w-32 md:h-32 rounded-full bg-black border-4 border-white flex items-center justify-center">
          <span class="text-4xl md:text-5xl font-bold">{days}</span>
        </div>
        <svg class="absolute top-0 left-0 w-24 h-24 md:w-32 md:h-32" viewBox="0 0 100 100">
          <circle 
            cx="50" cy="50" r="45" 
            fill="none" 
            stroke="white" 
            stroke-width="10" 
            stroke-dasharray={`${Math.min(days/365, 1) * 283} 283`} 
            stroke-dashoffset="0" 
            transform="rotate(-90 50 50)"
          />
        </svg>
        <p class="text-center mt-2 text-xl">DAYS</p>
      </div>
      
      <!-- Hours -->
      <div class="relative">
        <div class="w-24 h-24 md:w-32 md:h-32 rounded-full bg-black border-4 border-white flex items-center justify-center">
          <span class="text-4xl md:text-5xl font-bold">{hours}</span>
        </div>
        <svg class="absolute top-0 left-0 w-24 h-24 md:w-32 md:h-32" viewBox="0 0 100 100">
          <circle 
            cx="50" cy="50" r="45" 
            fill="none" 
            stroke="white" 
            stroke-width="10" 
            stroke-dasharray={`${hours/24 * 283} 283`} 
            stroke-dashoffset="0" 
            transform="rotate(-90 50 50)"
          />
        </svg>
        <p class="text-center mt-2 text-xl">HOURS</p>
      </div>
      
      <!-- Minutes -->
      <div class="relative">
        <div class="w-24 h-24 md:w-32 md:h-32 rounded-full bg-black border-4 border-white flex items-center justify-center">
          <span class="text-4xl md:text-5xl font-bold">{minutes}</span>
        </div>
        <svg class="absolute top-0 left-0 w-24 h-24 md:w-32 md:h-32" viewBox="0 0 100 100">
          <circle 
            cx="50" cy="50" r="45" 
            fill="none" 
            stroke="white" 
            stroke-width="10" 
            stroke-dasharray={`${minutes/60 * 283} 283`} 
            stroke-dashoffset="0" 
            transform="rotate(-90 50 50)"
          />
        </svg>
        <p class="text-center mt-2 text-xl">MINUTES</p>
      </div>
      
      <!-- Seconds -->
      <div class="relative">
        <div class="w-24 h-24 md:w-32 md:h-32 rounded-full bg-black border-4 border-white flex items-center justify-center">
          <span class="text-4xl md:text-5xl font-bold">{seconds}</span>
        </div>
        <svg class="absolute top-0 left-0 w-24 h-24 md:w-32 md:h-32" viewBox="0 0 100 100">
          <circle 
            cx="50" cy="50" r="45" 
            fill="none" 
            stroke="white" 
            stroke-width="10" 
            stroke-dasharray={`${seconds/60 * 283} 283`} 
            stroke-dashoffset="0" 
            transform="rotate(-90 50 50)"
          />
        </svg>
        <p class="text-center mt-2 text-xl">SECONDS</p>
      </div>
    </div>
    
    {#if sponsor}
      <div class="mt-12 flex flex-col items-center">
        <p class="text-xl text-center">{sponsorLabel}</p>
        <div class="mt-2 bg-white text-black px-4 py-2 inline-block">
          <p class="text-2xl font-bold">{sponsor}</p>
        </div>
      </div>
    {/if}
  </div>