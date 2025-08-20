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
      <div class="contact-info">
        <a href="tel:{content.company.phone}" class="contact-link">
          <Phone size={16} />
          <span>{content.company.phone}</span>
        </a>
        <a href="mailto:{content.company.email}" class="contact-link">
          <Mail size={16} />
          <span>{content.company.email}</span>
        </a>
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
        
        <ul class="nav-menu desktop-menu">
          {#each content.navigation as item}
            <li>
              <a href={item.href} class="nav-link">
                {item.label}
              </a>
            </li>
          {/each}
        </ul>
        
        <button class="mobile-menu-btn" on:click={toggleMobileMenu}>
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
    <div class="mobile-menu">
      <ul>
        {#each content.navigation as item}
          <li>
            <a href={item.href} class="nav-link" on:click={() => mobileMenuOpen = false}>
              {item.label}
            </a>
          </li>
        {/each}
      </ul>
    </div>
  {/if}
</header>

<style>
  .header {
    position: sticky;
    top: 0;
    z-index: 50;
    background-color: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  .top-bar {
    display: none;
    background-color: #f9fafb;
    border-bottom: 1px solid #e5e7eb;
    padding: 0.5rem 0;
  }

  @media (min-width: 768px) {
    .top-bar {
      display: block;
    }
  }

  .contact-info {
    display: flex;
    justify-content: flex-end;
    gap: 2rem;
  }

  .contact-link {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    color: #6b7280;
    font-size: 0.875rem;
    transition: color 0.3s ease;
  }

  .contact-link:hover {
    color: #3b82f6;
  }

  .navbar {
    padding: 1rem 0;
  }

  .nav-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .logo h1 {
    color: #3b82f6;
    font-size: 1.5rem;
    font-weight: bold;
    margin: 0;
  }

  .nav-menu {
    display: none;
    list-style: none;
    gap: 2rem;
    margin: 0;
    padding: 0;
  }

  .desktop-menu {
    display: none;
  }

  @media (min-width: 768px) {
    .desktop-menu {
      display: flex;
    }
  }

  .nav-link {
    color: #1f2937;
    font-weight: 500;
    transition: color 0.3s ease;
  }

  .nav-link:hover {
    color: #3b82f6;
  }

  .mobile-menu-btn {
    display: block;
    background: none;
    border: none;
    color: #1f2937;
    cursor: pointer;
    padding: 0.5rem;
  }

  @media (min-width: 768px) {
    .mobile-menu-btn {
      display: none;
    }
  }

  .mobile-menu {
    position: fixed;
    left: 0;
    right: 0;
    top: 60px;
    background-color: white;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
  }

  @media (min-width: 768px) {
    .mobile-menu {
      display: none;
    }
  }

  .mobile-menu ul {
    list-style: none;
    padding: 2rem;
    margin: 0;
  }

  .mobile-menu li {
    padding: 0.5rem 0;
  }

  .mobile-menu .nav-link {
    display: block;
    padding: 0.5rem 0;
  }
</style>