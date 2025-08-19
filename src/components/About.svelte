<script>
  import { Check } from 'lucide-svelte';
  export let content;
</script>

<section id="about" class="section">
  <div class="container">
    <h2 class="section-title">{content.about.title}</h2>
    <p class="section-subtitle">{content.about.subtitle}</p>
    
    <div class="about-grid">
      <div class="about-content">
        <p class="about-description">{content.about.description}</p>
        
        <div class="features-list">
          {#each content.about.features as feature}
            <div class="feature-item">
              <div class="feature-icon">
                <Check size={20} />
              </div>
              <div>
                <h4 class="feature-title">{feature.title}</h4>
                <p class="feature-text">{feature.description}</p>
              </div>
            </div>
          {/each}
        </div>
      </div>
      
      <div class="about-image">
        <img src={content.about.image} alt="About Us" />
        <div class="experience-badge">
          <div class="badge-number">15+</div>
          <div class="badge-text">Years of Excellence</div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: center;
  }
  
  .about-description {
    font-size: 1.125rem;
    color: var(--text-secondary);
    line-height: 1.8;
    margin-bottom: 2rem;
  }
  
  .features-list {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }
  
  .feature-item {
    display: flex;
    gap: 1rem;
    align-items: flex-start;
  }
  
  .feature-icon {
    flex-shrink: 0;
    width: 40px;
    height: 40px;
    background: linear-gradient(135deg, #10b981, #059669);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
  }
  
  .feature-title {
    font-size: 1.125rem;
    font-weight: 600;
    color: var(--text-primary);
    margin-bottom: 0.25rem;
  }
  
  .feature-text {
    color: var(--text-secondary);
    font-size: 0.875rem;
  }
  
  .about-image {
    position: relative;
  }
  
  .about-image img {
    width: 100%;
    height: auto;
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow-xl);
  }
  
  .experience-badge {
    position: absolute;
    bottom: 2rem;
    right: 2rem;
    background: white;
    padding: 1.5rem;
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow-xl);
    text-align: center;
  }
  
  .badge-number {
    font-size: 2.5rem;
    font-weight: 700;
    color: var(--primary-color);
    margin-bottom: 0.25rem;
  }
  
  .badge-text {
    font-size: 0.875rem;
    color: var(--text-secondary);
  }
  
  @media (max-width: 768px) {
    .about-grid {
      grid-template-columns: 1fr;
      gap: 2rem;
    }
    
    .about-image {
      order: -1;
    }
  }
</style>