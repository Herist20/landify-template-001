<script>
  import { Menu, X, Phone, Mail } from 'lucide-svelte';
  export let content;
  
  let mobileMenuOpen = false;
  
  function toggleMobileMenu() {
    mobileMenuOpen = !mobileMenuOpen;
  }
</script>

<header class="sticky top-0 z-50 bg-white shadow-sm">
  <div class="hidden md:block bg-gray-50 border-b border-gray-200 py-2">
    <div class="max-w-7xl mx-auto px-4">
      <div class="flex justify-end">
        <div class="flex gap-8">
          <a href="tel:{content.company.phone}" class="flex items-center gap-2 text-gray-600 text-sm hover:text-blue-600 transition-colors">
            <Phone size={16} />
            <span>{content.company.phone}</span>
          </a>
          <a href="mailto:{content.company.email}" class="flex items-center gap-2 text-gray-600 text-sm hover:text-blue-600 transition-colors">
            <Mail size={16} />
            <span>{content.company.email}</span>
          </a>
        </div>
      </div>
    </div>
  </div>
  
  <nav class="py-4">
    <div class="max-w-7xl mx-auto px-4">
      <div class="flex justify-between items-center">
        <div class="logo">
          <a href="#home">
            <h1 class="text-blue-600 text-2xl font-bold">{content.company.name}</h1>
          </a>
        </div>
        
        <ul class="hidden md:flex list-none gap-8 {mobileMenuOpen ? '' : ''}">
          {#each content.navigation as item}
            <li>
              <a href={item.href} class="text-gray-800 font-medium hover:text-blue-600 transition-colors">
                {item.label}
              </a>
            </li>
          {/each}
        </ul>
        
        <button class="md:hidden text-gray-800" on:click={toggleMobileMenu}>
          {#if mobileMenuOpen}
            <X size={24} />
          {:else}
            <Menu size={24} />
          {/if}
        </button>
      </div>
    </div>
  </nav>
  
  {#if mobileMenuOpen}
    <div class="md:hidden fixed left-0 right-0 top-[60px] bg-white shadow-lg">
      <ul class="flex flex-col p-8 gap-4">
        {#each content.navigation as item}
          <li>
            <a href={item.href} class="text-gray-800 font-medium hover:text-blue-600 transition-colors block py-2" on:click={() => mobileMenuOpen = false}>
              {item.label}
            </a>
          </li>
        {/each}
      </ul>
    </div>
  {/if}
</header>