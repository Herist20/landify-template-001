<script>
  import { Menu, X, Phone, Mail } from 'lucide-svelte';
  export let content;
  
  let mobileMenuOpen = false;
  
  function toggleMobileMenu() {
    mobileMenuOpen = !mobileMenuOpen;
  }
</script>

<header class="header animate-fadeIn">
  <div class="top-bar bg-secondary">
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
  
  <nav class="navbar bg-primary">
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
        
        <button class="mobile-menu-btn btn-ghost" on:click={toggleMobileMenu}>
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
    <div class="mobile-menu bg-primary animate-slideInLeft">
      <div class="container">
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
    </div>
  {/if}
</header>

<style>
  .header {
    position: sticky;
    top: 0;
    z-index: 50;
    box-shadow: var(--shadow-sm);
    backdrop-filter: blur(12px);
  }

  .top-bar {
    display: none;
    padding: var(--space-xs) 0;
    border-bottom: 1px solid var(--border-light);
  }

  @media (min-width: 768px) {
    .top-bar {
      display: block;
    }
  }

  .contact-info {
    display: flex;
    justify-content: flex-end;
    gap: var(--space-xl);
  }

  .contact-link {
    display: flex;
    align-items: center;
    gap: var(--space-xs);
    color: var(--text-muted);
    font-size: 0.875rem;
    font-weight: 500;
    transition: all var(--transition-base);
    text-decoration: none;
  }

  .contact-link:hover {
    color: var(--primary-color);
    transform: translateY(-1px);
  }

  .navbar {
    padding: var(--space-lg) 0;
    position: relative;
  }

  .nav-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .logo h1 {
    color: var(--primary-color);
    font-size: 1.75rem;
    font-weight: 700;
    margin: 0;
    letter-spacing: -0.01em;
    transition: color var(--transition-base);
  }

  .logo a:hover h1 {
    color: var(--primary-dark);
  }

  .nav-menu {
    display: none;
    list-style: none;
    gap: var(--space-xl);
    margin: 0;
    padding: 0;
    align-items: center;
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
    color: var(--text-primary);
    font-weight: 600;
    font-size: 0.9rem;
    text-decoration: none;
    padding: var(--space-sm) var(--space-md);
    border-radius: var(--radius-md);
    transition: all var(--transition-base);
    position: relative;
  }

  .nav-link:hover {
    color: var(--primary-color);
    background-color: rgba(37, 99, 235, 0.08);
    transform: translateY(-1px);
  }

  .mobile-menu-btn {
    display: block;
    color: var(--text-primary);
    border-radius: var(--radius-md);
    padding: var(--space-sm);
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
    top: calc(100% + 1px);
    box-shadow: var(--shadow-xl);
    backdrop-filter: blur(12px);
    border-radius: 0 0 var(--radius-lg) var(--radius-lg);
    border-top: 1px solid var(--border-light);
  }

  @media (min-width: 768px) {
    .mobile-menu {
      display: none;
    }
  }

  .mobile-menu ul {
    list-style: none;
    padding: var(--space-xl);
    margin: 0;
    display: flex;
    flex-direction: column;
    gap: var(--space-sm);
  }

  .mobile-menu li {
    padding: 0;
  }

  .mobile-menu .nav-link {
    display: block;
    padding: var(--space-md) var(--space-lg);
    border-radius: var(--radius-md);
    font-size: 1rem;
  }
</style>