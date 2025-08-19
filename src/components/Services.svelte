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

<section id="services" class="section bg-light">
  <div class="container">
    <h2 class="section-title">{content.services.title}</h2>
    <p class="section-subtitle">{content.services.subtitle}</p>
    
    <div class="services-grid">
      {#each content.services.items as service}
        <div class="service-card">
          <div class="service-icon">
            <svelte:component this={iconMap[service.icon]} size={32} />
          </div>
          <h3 class="service-title">{service.title}</h3>
          <p class="service-description">{service.description}</p>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .bg-light {
    background: var(--bg-light);
  }
  
  .services-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }
  
  .service-card {
    background: white;
    padding: 2rem;
    border-radius: var(--radius-lg);
    text-align: center;
    transition: all 0.3s ease;
    border: 1px solid transparent;
  }
  
  .service-card:hover {
    transform: translateY(-5px);
    box-shadow: var(--shadow-lg);
    border-color: var(--primary-color);
  }
  
  .service-icon {
    width: 70px;
    height: 70px;
    margin: 0 auto 1.5rem;
    background: linear-gradient(135deg, var(--primary-color), var(--primary-dark));
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    transition: transform 0.3s ease;
  }
  
  .service-card:hover .service-icon {
    transform: scale(1.1);
  }
  
  .service-title {
    font-size: 1.25rem;
    font-weight: 600;
    margin-bottom: 1rem;
    color: var(--text-primary);
  }
  
  .service-description {
    color: var(--text-secondary);
    line-height: 1.6;
  }
  
  @media (max-width: 768px) {
    .services-grid {
      grid-template-columns: 1fr;
    }
  }
</style>