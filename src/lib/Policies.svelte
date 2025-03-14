<script>
    // Define your policy items in a reusable array
    const refundPolicyItems = [
      { number: 1, text: "We will refund 50% of your entry fee until April 1st at 11:59pm." },
      { number: 2, text: "After April 1st, there will be no refunds." },
      { number: 3, text: "We will not do any rollover or transfer of bibs." },
      { 
        number: 4, 
        text: "This is a mountain race. If the race must be cancelled due to fire, severe weather, pandemic, etc, there is no possible way for us to refund or rollover your entry. That money is gone. When you register, consider this issue and either commit or stick to safer races that run in circles."
      },
      { number: 5, text: "If facing personal financial hardship, reach out to us." }
    ];
  </script>
  
  <section class="w-full bg-gray-50 py-20 dark:bg-gray-900 scroll-mt-12" id="policies">
    <div class="container mx-auto max-w-3xl px-6">
      <h2 class="mb-16 text-center font-serif text-4xl font-bold text-gray-800 dark:text-gray-100">
        Race Policies
      </h2>
      
      <div class="space-y-16">
        <!-- Refund Policy Section -->
        <div class="text-center">
          <h3 class="mb-8 font-serif text-2xl font-semibold text-gray-800 dark:text-gray-100 inline-block border-b-2 border-orange-500 dark:border-orange-400 pb-2">
            Refund Policy
          </h3>
          
          <ol class="mx-auto max-w-xl space-y-4 text-gray-700 dark:text-gray-300 text-left list-none">
            {#each refundPolicyItems as item, index}
            <li class="{index < refundPolicyItems.length - 1 ? 'pb-4 border-b border-gray-100 dark:border-gray-800' : 'pt-4'} {index > 0 && index < refundPolicyItems.length - 1 ? 'py-4' : ''} flex">
              <span class="flex-shrink-0 w-8 h-8 mr-3 bg-orange-500 dark:bg-orange-600/50 text-white rounded-full text-center leading-8 font-medium">{item.number}</span>
              <span class="flex-1">{item.text}</span>
            </li>
          {/each}
          </ol>
        </div>
        
        <!-- Dogs Policy Section -->
        <div class="text-center">
          <h3 class="mb-8 font-serif text-2xl font-semibold text-gray-800 dark:text-gray-100 inline-block border-b-2 border-orange-500 dark:border-orange-400 pb-2">
            Dogs Policy
          </h3>
          
          <div class="mx-auto max-w-xl space-y-4 text-gray-700 dark:text-gray-300 text-left">
            <p>
              Dogs are not permitted to run the race with our runners. This is a safety issue. Dogs attract
              other wild animals and the leashes tangle and cause tripping issues.
            </p>
            <p>Leashed and well behaved dogs can enjoy the finish area.</p>
          </div>
        </div>
      </div>
      
      <div class="mt-16 text-center">
        <p class="italic text-gray-600 dark:text-gray-400">
          For any policy questions, please contact us at 
          <span class="text-orange-500 dark:text-orange-300 font-medium md:select-all">jeremy_humphrey@yahoo.com</span>
        </p>
      </div>
    </div>
  </section>