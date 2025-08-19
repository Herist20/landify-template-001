<script>
  import { Home, Key, TrendingUp, FileText, Calculator, Users } from 'lucide-svelte';
  export let content;
  
  const iconMap = {
    'Home': Home,
    'Key': Key,
    'TrendingUp': TrendingUp,
    'FileText': FileText,
    'Calculator': Calculator,
    'Users': Users
  };
</script>

<section id="services" class="py-16 bg-white">
  <div class="max-w-7xl mx-auto px-4">
    <h2 class="text-4xl font-bold text-center text-gray-800 mb-2">{content.services.title}</h2>
    <p class="text-lg text-gray-600 text-center mb-12">{content.services.subtitle}</p>
    
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
      {#each content.services.items as service}
        <div class="bg-gray-50 p-8 rounded-xl text-center hover:-translate-y-1 hover:shadow-xl transition-all duration-300 border border-transparent hover:border-blue-600">
          <div class="w-20 h-20 mx-auto mb-6 bg-gradient-to-br from-blue-600 to-blue-700 rounded-full flex items-center justify-center text-white hover:scale-110 transition-transform duration-300">
            <svelte:component this={iconMap[service.icon]} size={32} />
          </div>
          <h3 class="text-xl font-semibold text-gray-800 mb-4">{service.title}</h3>
          <p class="text-gray-600 leading-relaxed">{service.description}</p>
        </div>
      {/each}
    </div>
  </div>
</section>