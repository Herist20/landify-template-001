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

<section id="services" class="services-section">
  <div class="services-container">
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
  .services-section {
    padding: 4rem 0;
    background-color: white;
  }

  .services-container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 1rem;
  }

  .section-title {
    font-size: 2.25rem;
    font-weight: bold;
    text-align: center;
    color: #1f2937;
    margin-bottom: 0.5rem;
  }

  .section-subtitle {
    font-size: 1.125rem;
    color: #4b5563;
    text-align: center;
    margin-bottom: 3rem;
  }

  .services-grid {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 2rem;
  }

  @media (min-width: 768px) {
    .services-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (min-width: 1024px) {
    .services-grid {
      grid-template-columns: repeat(3, 1fr);
    }
  }

  .service-card {
    background-color: #f9fafb;
    padding: 2rem;
    border-radius: 0.75rem;
    text-align: center;
    border: 1px solid transparent;
    transition: all 0.3s ease;
  }

  .service-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
    border-color: #2563eb;
  }

  .service-icon {
    width: 5rem;
    height: 5rem;
    margin: 0 auto 1.5rem auto;
    background: linear-gradient(135deg, #2563eb 0%, #1d4ed8 100%);
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
    color: #1f2937;
    margin-bottom: 1rem;
  }

  .service-description {
    color: #4b5563;
    line-height: 1.6;
  }
</style>