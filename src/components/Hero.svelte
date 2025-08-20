<script>
  import { ArrowRight, Search } from 'lucide-svelte';
  export let content;
</script>

<section id="home" class="hero-section">
  <div class="hero-overlay"></div>
  <div class="hero-container">
    <div class="hero-grid">
      <div class="hero-content">
        <h1 class="hero-title">{content.hero.title}</h1>
        <p class="hero-subtitle">{content.hero.subtitle}</p>
        
        <div class="hero-buttons">
          <a href={content.hero.primaryButton.href} class="btn-primary">
            {content.hero.primaryButton.text}
            <ArrowRight size={20} />
          </a>
          <a href={content.hero.secondaryButton.href} class="btn-secondary">
            {content.hero.secondaryButton.text}
          </a>
        </div>
        
        <div class="hero-stats">
          {#each content.hero.stats as stat}
            <div class="stat-item">
              <div class="stat-value">{stat.value}</div>
              <div class="stat-label">{stat.label}</div>
            </div>
          {/each}
        </div>
      </div>
      
      <div class="hero-image">
        <img src="https://images.unsplash.com/photo-1600585154340-be6161a56a0c?w=800&h=600&fit=crop" alt="Luxury Property" class="property-image" />
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
    padding: 5rem 0;
    background: linear-gradient(135deg, #4f46e5 0%, #9333ea 50%, #ec4899 100%);
    position: relative;
    overflow: hidden;
  }

  .hero-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.2);
  }

  .hero-container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 1rem;
    position: relative;
    z-index: 10;
  }

  .hero-grid {
    display: grid;
    gap: 4rem;
    align-items: center;
  }

  @media (min-width: 1024px) {
    .hero-grid {
      grid-template-columns: 1fr 1fr;
    }
  }

  .hero-content {
    color: white;
  }

  .hero-title {
    font-size: 3rem;
    font-weight: bold;
    margin-bottom: 1rem;
    line-height: 1.1;
  }

  @media (min-width: 1024px) {
    .hero-title {
      font-size: 3.75rem;
    }
  }

  .hero-subtitle {
    font-size: 1.25rem;
    margin-bottom: 2rem;
    opacity: 0.95;
  }

  .hero-buttons {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    margin-bottom: 3rem;
  }

  @media (min-width: 640px) {
    .hero-buttons {
      flex-direction: row;
    }
  }

  .btn-primary {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
    padding: 0.75rem 1.5rem;
    background-color: white;
    color: #4f46e5;
    border-radius: 0.5rem;
    font-weight: 600;
    text-decoration: none;
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
    transition: all 0.3s ease;
  }

  .btn-primary:hover {
    background-color: #f3f4f6;
    transform: translateY(-2px);
  }

  .btn-secondary {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    padding: 0.75rem 1.5rem;
    border: 2px solid white;
    color: white;
    border-radius: 0.5rem;
    font-weight: 600;
    text-decoration: none;
    transition: all 0.3s ease;
  }

  .btn-secondary:hover {
    background-color: white;
    color: #4f46e5;
  }

  .hero-stats {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
    padding: 2rem;
    background-color: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(12px);
    border-radius: 0.75rem;
  }

  @media (min-width: 768px) {
    .hero-stats {
      grid-template-columns: repeat(4, 1fr);
    }
  }

  .stat-item {
    text-align: center;
  }

  .stat-value {
    font-size: 1.875rem;
    font-weight: bold;
    margin-bottom: 0.25rem;
  }

  .stat-label {
    font-size: 0.875rem;
    opacity: 0.9;
  }

  .hero-image {
    display: none;
  }

  @media (min-width: 1024px) {
    .hero-image {
      display: block;
    }
  }

  .property-image {
    width: 100%;
    height: auto;
    border-radius: 0.75rem;
    box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
  }

  .hero-wave {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
  }

  .wave-svg {
    width: 100%;
    height: auto;
  }
</style>