<script>
  import { ArrowRight, Search } from 'lucide-svelte';
  export let content;
</script>

<section id="home" class="section hero-section">
  <div class="hero-overlay"></div>
  <div class="container">
    <div class="hero-grid">
      <div class="hero-content animate-slideInLeft">
        <h1 class="hero-title">{content.hero.title}</h1>
        <p class="hero-subtitle lead">{content.hero.subtitle}</p>
        
        <div class="hero-buttons">
          <a href={content.hero.primaryButton.href} class="btn btn-primary btn-lg btn-icon">
            {content.hero.primaryButton.text}
            <ArrowRight size={20} />
          </a>
          <a href={content.hero.secondaryButton.href} class="btn btn-outline btn-lg">
            {content.hero.secondaryButton.text}
          </a>
        </div>
        
        <div class="hero-stats card">
          {#each content.hero.stats as stat}
            <div class="stat-item text-center">
              <div class="stat-value text-primary">{stat.value}</div>
              <div class="stat-label text-muted">{stat.label}</div>
            </div>
          {/each}
        </div>
      </div>
      
      <div class="hero-image animate-slideInRight">
        <img src="https://images.unsplash.com/photo-1600585154340-be6161a56a0c?w=800&h=600&fit=crop" alt="Luxury Property" class="property-image rounded-xl shadow-2xl" />
      </div>
    </div>
  </div>
  
  <div class="hero-wave">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320" class="wave-svg">
      <path fill="#ffffff" fill-opacity="0.1" d="M0,192L48,197.3C96,203,192,213,288,229.3C384,245,480,267,576,250.7C672,235,768,181,864,181.3C960,181,1056,235,1152,234.7C1248,235,1344,181,1392,154.7L1440,128L1440,320L1392,320C1344,320,1248,320,1152,320C1056,320,960,320,864,320C768,320,672,320,576,320C480,320,384,320,288,320C192,320,96,320,48,320L0,320Z"></path>
    </svg>
  </div>
</section>

<style>
  .hero-section {
    background: linear-gradient(135deg, var(--primary-color) 0%, var(--primary-dark) 50%, #9333ea 100%);
    position: relative;
    overflow: hidden;
    color: white;
    padding: var(--space-4xl) 0 calc(var(--space-4xl) * 1.5) 0;
  }

  @media (min-width: 768px) {
    .hero-section {
      padding: calc(var(--space-4xl) * 1.5) 0 calc(var(--space-4xl) * 2) 0;
    }
  }

  .hero-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(135deg, rgba(37, 99, 235, 0.1) 0%, rgba(30, 64, 175, 0.2) 100%);
    backdrop-filter: blur(1px);
  }

  .hero-grid {
    display: grid;
    gap: var(--space-4xl);
    align-items: center;
    position: relative;
    z-index: 10;
  }

  @media (min-width: 1024px) {
    .hero-grid {
      grid-template-columns: 1.2fr 1fr;
      gap: var(--space-3xl);
    }
  }

  .hero-content {
    position: relative;
    z-index: 20;
  }

  .hero-title {
    margin-bottom: var(--space-lg);
    color: white;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .hero-subtitle {
    color: rgba(255, 255, 255, 0.95);
    margin-bottom: var(--space-2xl);
    max-width: 32rem;
  }

  .hero-buttons {
    display: flex;
    flex-direction: column;
    gap: var(--space-lg);
    margin-bottom: var(--space-3xl);
  }

  @media (min-width: 640px) {
    .hero-buttons {
      flex-direction: row;
      gap: var(--space-xl);
    }
  }

  .hero-stats {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: var(--space-lg);
    padding: var(--space-xl);
    background: rgba(255, 255, 255, 0.15);
    backdrop-filter: blur(16px);
    border: 1px solid rgba(255, 255, 255, 0.2);
    box-shadow: var(--shadow-xl);
    transition: all var(--transition-base);
  }

  .hero-stats:hover {
    background: rgba(255, 255, 255, 0.2);
    transform: translateY(-2px);
  }

  @media (min-width: 768px) {
    .hero-stats {
      grid-template-columns: repeat(4, 1fr);
    }
  }

  .stat-item {
    position: relative;
  }

  .stat-value {
    font-size: clamp(1.5rem, 4vw, 2rem);
    font-weight: 800;
    margin-bottom: var(--space-xs);
    color: white;
  }

  .stat-label {
    font-size: 0.875rem;
    font-weight: 500;
    color: rgba(255, 255, 255, 0.9);
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .hero-image {
    display: none;
    position: relative;
    z-index: 10;
  }

  @media (min-width: 1024px) {
    .hero-image {
      display: block;
    }
  }

  .property-image {
    width: 100%;
    height: auto;
    transition: transform var(--transition-slow);
  }

  .property-image:hover {
    transform: scale(1.02);
  }

  .hero-wave {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 5;
  }

  .wave-svg {
    width: 100%;
    height: auto;
    display: block;
  }
</style>