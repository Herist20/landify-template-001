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

<section id="services" class="section bg-primary">
  <div class="container">
    <div class="section-header">
      <h2 class="section-title">{content.services.title}</h2>
      <p class="section-subtitle">{content.services.subtitle}</p>
    </div>
    
    <div class="grid grid-cols-3">
      {#each content.services.items as service}
        <div class="service-card card animate-fadeIn">
          <div class="service-icon">
            <svelte:component this={iconMap[service.icon]} size={32} />
          </div>
          <h3 class="service-title">{service.title}</h3>
          <p class="service-description text-secondary">{service.description}</p>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .service-card {
    padding: var(--space-2xl);
    text-align: center;
    border: 1px solid var(--border-light);
    transition: all var(--transition-base);
    position: relative;
    overflow: hidden;
  }

  .service-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(90deg, var(--primary-color), var(--accent-color));
    transform: scaleX(0);
    transition: transform var(--transition-base);
    transform-origin: left;
  }

  .service-card:hover::before {
    transform: scaleX(1);
  }

  .service-card:hover {
    transform: translateY(-8px);
    box-shadow: var(--shadow-2xl);
    border-color: var(--primary-color);
    background: linear-gradient(135deg, var(--bg-primary) 0%, rgba(37, 99, 235, 0.02) 100%);
  }

  .service-icon {
    width: 5rem;
    height: 5rem;
    margin: 0 auto var(--space-xl) auto;
    background: linear-gradient(135deg, var(--primary-color) 0%, var(--primary-dark) 100%);
    border-radius: var(--radius-full);
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    transition: all var(--transition-base);
    position: relative;
    box-shadow: var(--shadow-lg);
  }

  .service-icon::after {
    content: '';
    position: absolute;
    inset: -4px;
    background: linear-gradient(135deg, var(--primary-color), var(--accent-color));
    border-radius: var(--radius-full);
    z-index: -1;
    opacity: 0;
    transition: opacity var(--transition-base);
  }

  .service-card:hover .service-icon {
    transform: scale(1.15) rotate(5deg);
    box-shadow: var(--shadow-xl);
  }

  .service-card:hover .service-icon::after {
    opacity: 1;
  }

  .service-title {
    font-size: 1.25rem;
    font-weight: 700;
    color: var(--text-primary);
    margin-bottom: var(--space-lg);
    transition: color var(--transition-base);
  }

  .service-card:hover .service-title {
    color: var(--primary-color);
  }

  .service-description {
    line-height: 1.7;
    margin-bottom: 0;
  }

  /* Animation delays for staggered effect */
  .service-card:nth-child(1) { animation-delay: 0.1s; }
  .service-card:nth-child(2) { animation-delay: 0.2s; }
  .service-card:nth-child(3) { animation-delay: 0.3s; }
  .service-card:nth-child(4) { animation-delay: 0.4s; }
  .service-card:nth-child(5) { animation-delay: 0.5s; }
  .service-card:nth-child(6) { animation-delay: 0.6s; }

  /* Responsive adjustments */
  @media (max-width: 768px) {
    .service-card {
      padding: var(--space-xl);
    }
    
    .service-icon {
      width: 4rem;
      height: 4rem;
    }
  }
</style>