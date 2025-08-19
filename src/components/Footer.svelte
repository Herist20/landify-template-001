<script>
  import { Facebook, Twitter, Linkedin, Instagram, ArrowUp } from 'lucide-svelte';
  export let content;
  
  const iconMap = {
    'Facebook': Facebook,
    'Twitter': Twitter,
    'LinkedIn': Linkedin,
    'Instagram': Instagram
  };
  
  function scrollToTop() {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }
</script>

<footer class="bg-gradient-to-br from-blue-900 to-blue-800 text-white pt-16 pb-8">
  <div class="max-w-7xl mx-auto px-4">
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-12 mb-12">
      <div class="lg:col-span-1">
        <h3 class="text-2xl font-bold mb-4">{content.company.name}</h3>
        <p class="leading-relaxed opacity-90 mb-6">{content.footer.description}</p>
        <div class="flex gap-4">
          {#each content.footer.socialLinks as social}
            <a href={social.url} target="_blank" rel="noopener noreferrer" class="w-10 h-10 bg-white bg-opacity-10 rounded-full flex items-center justify-center hover:bg-opacity-20 hover:-translate-y-1 transition-all duration-300">
              <svelte:component this={iconMap[social.platform]} size={20} />
            </a>
          {/each}
        </div>
      </div>
      
      <div>
        <h4 class="text-lg font-semibold mb-6">Quick Links</h4>
        <ul class="space-y-3">
          {#each content.footer.quickLinks as link}
            <li>
              <a href={link.href} class="opacity-90 hover:opacity-70 transition-opacity">{link.label}</a>
            </li>
          {/each}
        </ul>
      </div>
      
      <div>
        <h4 class="text-lg font-semibold mb-6">Contact Info</h4>
        <ul class="space-y-3 opacity-90">
          <li>{content.company.phone}</li>
          <li>{content.company.email}</li>
          <li>{content.company.address}</li>
        </ul>
      </div>
      
      <div>
        <h4 class="text-lg font-semibold mb-6">Newsletter</h4>
        <p class="opacity-90 mb-4">Subscribe to get the latest property updates</p>
        <form class="flex flex-col gap-2">
          <input type="email" placeholder="Your email" class="px-4 py-3 rounded-lg bg-white bg-opacity-10 text-white placeholder-gray-300 focus:outline-none focus:bg-opacity-20 transition-all" />
          <button type="submit" class="px-6 py-3 bg-green-600 rounded-lg font-medium hover:bg-green-700 transition-colors">
            Subscribe
          </button>
        </form>
      </div>
    </div>
    
    <div class="pt-8 border-t border-white border-opacity-10 flex flex-col sm:flex-row justify-between items-center gap-4">
      <p class="opacity-90">{content.footer.copyright}</p>
      <button class="w-10 h-10 bg-white bg-opacity-10 rounded-full flex items-center justify-center hover:bg-opacity-20 hover:-translate-y-1 transition-all duration-300" on:click={scrollToTop}>
        <ArrowUp size={20} />
      </button>
    </div>
  </div>
</footer>