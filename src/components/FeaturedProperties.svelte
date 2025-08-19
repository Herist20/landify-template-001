<script>
  import { MapPin, Bed, Bath, Maximize } from 'lucide-svelte';
  export let content;
</script>

<section id="properties" class="py-16 bg-gray-50">
  <div class="max-w-7xl mx-auto px-4">
    <h2 class="text-4xl font-bold text-center text-gray-800 mb-2">{content.featuredProperties.title}</h2>
    <p class="text-lg text-gray-600 text-center mb-12">{content.featuredProperties.subtitle}</p>
    
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
      {#each content.featuredProperties.properties as property}
        <div class="bg-white rounded-xl overflow-hidden shadow-lg hover:shadow-2xl transform hover:-translate-y-1 transition-all duration-300">
          <div class="relative h-64 overflow-hidden">
            <img src={property.image} alt={property.title} class="w-full h-full object-cover hover:scale-110 transition-transform duration-300" />
            <span class="absolute top-4 left-4 px-3 py-1 text-white text-sm font-medium rounded-md {property.type === 'For Sale' ? 'bg-blue-600' : 'bg-green-600'}">
              {property.type}
            </span>
            {#if property.featured}
              <span class="absolute top-4 right-4 px-3 py-1 bg-amber-500 text-white text-sm font-medium rounded-md">
                Featured
              </span>
            {/if}
          </div>
          
          <div class="p-6">
            <h3 class="text-xl font-semibold text-gray-800 mb-2">{property.title}</h3>
            <div class="flex items-center gap-2 text-gray-600 text-sm mb-4">
              <MapPin size={16} />
              <span>{property.location}</span>
            </div>
            
            <div class="flex gap-6 py-4 border-t border-b border-gray-200 mb-4">
              <div class="flex items-center gap-2 text-gray-600 text-sm">
                <Bed size={18} />
                <span>{property.beds} Beds</span>
              </div>
              <div class="flex items-center gap-2 text-gray-600 text-sm">
                <Bath size={18} />
                <span>{property.baths} Baths</span>
              </div>
              <div class="flex items-center gap-2 text-gray-600 text-sm">
                <Maximize size={18} />
                <span>{property.area}</span>
              </div>
            </div>
            
            <div class="flex justify-between items-center">
              <div class="text-2xl font-bold text-blue-600">{property.price}</div>
              <button class="px-4 py-2 border border-blue-600 text-blue-600 rounded-lg hover:bg-blue-600 hover:text-white transition-colors duration-300 font-medium">
                View Details
              </button>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>