<script>
  import { ArrowRight, Search } from 'lucide-svelte';
  export let content;
</script>

<section id="home" class="py-20 bg-gradient-to-br from-indigo-600 via-purple-600 to-pink-500 relative overflow-hidden">
  <div class="absolute inset-0 bg-black opacity-20"></div>
  <div class="max-w-7xl mx-auto px-4 relative z-10">
    <div class="grid lg:grid-cols-2 gap-16 items-center">
      <div class="text-white">
        <h1 class="text-5xl lg:text-6xl font-bold mb-4 leading-tight">{content.hero.title}</h1>
        <p class="text-xl mb-8 opacity-95">{content.hero.subtitle}</p>
        
        <div class="flex flex-col sm:flex-row gap-4 mb-12">
          <a href={content.hero.primaryButton.href} class="inline-flex items-center justify-center gap-2 px-6 py-3 bg-white text-indigo-600 rounded-lg font-semibold hover:bg-gray-100 transform hover:-translate-y-0.5 transition-all duration-300 shadow-lg">
            {content.hero.primaryButton.text}
            <ArrowRight size={20} />
          </a>
          <a href={content.hero.secondaryButton.href} class="inline-flex items-center justify-center px-6 py-3 border-2 border-white text-white rounded-lg font-semibold hover:bg-white hover:text-indigo-600 transition-all duration-300">
            {content.hero.secondaryButton.text}
          </a>
        </div>
        
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8 p-8 bg-white bg-opacity-10 backdrop-blur-md rounded-xl">
          {#each content.hero.stats as stat}
            <div class="text-center">
              <div class="text-3xl font-bold mb-1">{stat.value}</div>
              <div class="text-sm opacity-90">{stat.label}</div>
            </div>
          {/each}
        </div>
      </div>
      
      <div class="hidden lg:block">
        <img src="https://images.unsplash.com/photo-1600585154340-be6161a56a0c?w=800&h=600&fit=crop" alt="Luxury Property" class="w-full h-auto rounded-xl shadow-2xl" />
      </div>
    </div>
  </div>
  
  <div class="absolute bottom-0 left-0 right-0">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320" class="w-full h-auto">
      <path fill="#ffffff" fill-opacity="0.1" d="M0,192L48,197.3C96,203,192,213,288,229.3C384,245,480,267,576,250.7C672,235,768,181,864,181.3C960,181,1056,235,1152,234.7C1248,235,1344,181,1392,154.7L1440,128L1440,320L1392,320C1344,320,1248,320,1152,320C1056,320,960,320,864,320C768,320,672,320,576,320C480,320,384,320,288,320C192,320,96,320,48,320L0,320Z"></path>
    </svg>
  </div>
</section>