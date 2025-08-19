<script>
  import { ArrowRight, Search } from 'lucide-svelte';
  export let content;
</script>

<section id="home" class="hero">
  <div class="container">
    <div class="hero-content">
      <h1 class="hero-title">{content.hero.title}</h1>
      <p class="hero-subtitle">{content.hero.subtitle}</p>
      
      <div class="hero-buttons">
        <a href={content.hero.primaryButton.href} class="btn btn-primary">
          {content.hero.primaryButton.text}
          <ArrowRight size={20} />
        </a>
        <a href={content.hero.secondaryButton.href} class="btn btn-secondary">
          {content.hero.secondaryButton.text}
        </a>
      </div>
      
      <div class="stats-grid">
        {#each content.hero.stats as stat}
          <div class="stat-item">
            <div class="stat-value">{stat.value}</div>
            <div class="stat-label">{stat.label}</div>
          </div>
        {/each}
      </div>
    </div>
    
    <div class="hero-image">
      <img src="https://images.unsplash.com/photo-1600585154340-be6161a56a0c?w=800&h=600&fit=crop" alt="Luxury Property" />
    </div>
  </div>
</section>

<style>
  .hero {
    padding: 5rem 0;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    position: relative;
    overflow: hidden;
  }
  
  .hero::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320"><path fill="%23ffffff" fill-opacity="0.1" d="M0,192L48,197.3C96,203,192,213,288,229.3C384,245,480,267,576,250.7C672,235,768,181,864,181.3C960,181,1056,235,1152,234.7C1248,235,1344,181,1392,154.7L1440,128L1440,320L1392,320C1344,320,1248,320,1152,320C1056,320,960,320,864,320C768,320,672,320,576,320C480,320,384,320,288,320C192,320,96,320,48,320L0,320Z"></path></svg>') no-repeat bottom;
    background-size: cover;
  }
  
  .hero .container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: center;
    position: relative;
    z-index: 1;
  }
  
  .hero-content {
    color: white;
  }
  
  .hero-title {
    font-size: 3.5rem;
    font-weight: 700;
    margin-bottom: 1rem;
    line-height: 1.2;
  }
  
  .hero-subtitle {
    font-size: 1.25rem;
    margin-bottom: 2rem;
    opacity: 0.95;
  }
  
  .hero-buttons {
    display: flex;
    gap: 1rem;
    margin-bottom: 3rem;
  }
  
  .hero-buttons .btn {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
  }
  
  .hero-buttons .btn-primary {
    background: white;
    color: var(--primary-color);
  }
  
  .hero-buttons .btn-secondary {
    border-color: white;
    color: white;
  }
  
  .hero-buttons .btn-secondary:hover {
    background: white;
    color: var(--primary-color);
  }
  
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 2rem;
    padding: 2rem;
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    border-radius: var(--radius-lg);
  }
  
  .stat-item {
    text-align: center;
  }
  
  .stat-value {
    font-size: 2rem;
    font-weight: 700;
    margin-bottom: 0.25rem;
  }
  
  .stat-label {
    font-size: 0.875rem;
    opacity: 0.9;
  }
  
  .hero-image {
    position: relative;
  }
  
  .hero-image img {
    width: 100%;
    height: auto;
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow-xl);
  }
  
  @media (max-width: 768px) {
    .hero .container {
      grid-template-columns: 1fr;
    }
    
    .hero-title {
      font-size: 2.5rem;
    }
    
    .hero-buttons {
      flex-direction: column;
    }
    
    .stats-grid {
      grid-template-columns: repeat(2, 1fr);
    }
    
    .hero-image {
      display: none;
    }
  }
</style>