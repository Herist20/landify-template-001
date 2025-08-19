<script>
  import { Menu, X, Phone, Mail } from 'lucide-svelte';
  export let content;
  
  let mobileMenuOpen = false;
  
  function toggleMobileMenu() {
    mobileMenuOpen = !mobileMenuOpen;
  }
</script>

<header class="header">
  <div class="top-bar">
    <div class="container">
      <div class="top-bar-content">
        <div class="contact-info">
          <a href="tel:{content.company.phone}" class="contact-item">
            <Phone size={16} />
            <span>{content.company.phone}</span>
          </a>
          <a href="mailto:{content.company.email}" class="contact-item">
            <Mail size={16} />
            <span>{content.company.email}</span>
          </a>
        </div>
      </div>
    </div>
  </div>
  
  <nav class="navbar">
    <div class="container">
      <div class="nav-content">
        <div class="logo">
          <a href="#home">
            <h1>{content.company.name}</h1>
          </a>
        </div>
        
        <ul class="nav-menu" class:active={mobileMenuOpen}>
          {#each content.navigation as item}
            <li class="nav-item">
              <a href={item.href} class="nav-link" on:click={() => mobileMenuOpen = false}>
                {item.label}
              </a>
            </li>
          {/each}
        </ul>
        
        <button class="mobile-toggle" on:click={toggleMobileMenu}>
          {#if mobileMenuOpen}
            <X size={24} />
          {:else}
            <Menu size={24} />
          {/if}
        </button>
      </div>
    </div>
  </nav>
</header>

<style>
  .header {
    position: sticky;
    top: 0;
    z-index: 1000;
    background: white;
    box-shadow: var(--shadow-sm);
  }
  
  .top-bar {
    background: var(--bg-light);
    border-bottom: 1px solid var(--border-color);
    padding: 0.5rem 0;
  }
  
  .top-bar-content {
    display: flex;
    justify-content: flex-end;
  }
  
  .contact-info {
    display: flex;
    gap: 2rem;
  }
  
  .contact-item {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    color: var(--text-secondary);
    text-decoration: none;
    font-size: 0.875rem;
    transition: color 0.3s;
  }
  
  .contact-item:hover {
    color: var(--primary-color);
  }
  
  .navbar {
    padding: 1rem 0;
  }
  
  .nav-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .logo a {
    text-decoration: none;
  }
  
  .logo h1 {
    color: var(--primary-color);
    font-size: 1.75rem;
    font-weight: 700;
  }
  
  .nav-menu {
    display: flex;
    list-style: none;
    gap: 2rem;
  }
  
  .nav-link {
    color: var(--text-primary);
    text-decoration: none;
    font-weight: 500;
    transition: color 0.3s;
  }
  
  .nav-link:hover {
    color: var(--primary-color);
  }
  
  .mobile-toggle {
    display: none;
    background: none;
    border: none;
    cursor: pointer;
    color: var(--text-primary);
  }
  
  @media (max-width: 768px) {
    .top-bar {
      display: none;
    }
    
    .mobile-toggle {
      display: block;
    }
    
    .nav-menu {
      position: fixed;
      left: -100%;
      top: 70px;
      flex-direction: column;
      background-color: white;
      width: 100%;
      padding: 2rem;
      box-shadow: var(--shadow-lg);
      transition: 0.3s;
    }
    
    .nav-menu.active {
      left: 0;
    }
  }
</style>