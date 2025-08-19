<script>
  import { Check } from 'lucide-svelte';
  export let content;
</script>

<section id="about" class="py-16 bg-gray-50">
  <div class="max-w-7xl mx-auto px-4">
    <h2 class="text-4xl font-bold text-center text-gray-800 mb-2">{content.about.title}</h2>
    <p class="text-lg text-gray-600 text-center mb-12">{content.about.subtitle}</p>
    
    <div class="grid lg:grid-cols-2 gap-16 items-center">
      <div>
        <p class="text-lg text-gray-600 leading-relaxed mb-8">{content.about.description}</p>
        
        <div class="space-y-6">
          {#each content.about.features as feature}
            <div class="flex gap-4">
              <div class="flex-shrink-0 w-10 h-10 bg-gradient-to-br from-green-500 to-green-600 rounded-full flex items-center justify-center text-white">
                <Check size={20} />
              </div>
              <div>
                <h4 class="text-lg font-semibold text-gray-800 mb-1">{feature.title}</h4>
                <p class="text-sm text-gray-600">{feature.description}</p>
              </div>
            </div>
          {/each}
        </div>
      </div>
      
      <div class="relative order-first lg:order-last">
        <img src={content.about.image} alt="About Us" class="w-full h-auto rounded-xl shadow-2xl" />
        <div class="absolute bottom-8 right-8 bg-white p-6 rounded-xl shadow-xl text-center">
          <div class="text-4xl font-bold text-blue-600 mb-1">15+</div>
          <div class="text-sm text-gray-600">Years of Excellence</div>
        </div>
      </div>
    </div>
  </div>
</section>