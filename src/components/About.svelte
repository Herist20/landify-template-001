<script>
  import { Check } from 'lucide-svelte';
  export let content;
</script>

<section id="about" class="section bg-secondary">
  <div class="container">
    <div class="section-header">
      <h2 class="section-title">{content.about.title}</h2>
      <p class="section-subtitle">{content.about.subtitle}</p>
    </div>
    
    <div class="about-grid">
      <div class="about-content animate-slideInLeft">
        <p class="about-description lead">{content.about.description}</p>
        
        <div class="features-list">
          {#each content.about.features as feature}
            <div class="feature-item">
              <div class="feature-icon">
                <Check size={20} />
              </div>
              <div class="feature-content">
                <h4 class="feature-title">{feature.title}</h4>
                <p class="feature-description text-secondary">{feature.description}</p>
              </div>
            </div>
          {/each}
        </div>
      </div>
      
      <div class="about-image-container animate-slideInRight">
        <img src={content.about.image} alt="About Us" class="about-image rounded-xl shadow-2xl" />
        <div class="experience-badge card shadow-xl">
          <div class="badge-number text-primary">15+</div>
          <div class="badge-text text-muted">Years of Excellence</div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .about-grid {
    display: grid;
    gap: var(--space-4xl);
    align-items: center;
  }

  @media (min-width: 1024px) {
    .about-grid {
      grid-template-columns: 1.1fr 1fr;
      gap: var(--space-3xl);
    }
  }

  .about-description {
    margin-bottom: var(--space-2xl);
    max-width: 36rem;
  }

  .features-list {
    display: flex;
    flex-direction: column;
    gap: var(--space-xl);
  }

  .feature-item {
    display: flex;
    gap: var(--space-lg);
    padding: var(--space-lg);
    background: var(--bg-primary);
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow-sm);
    border: 1px solid var(--border-light);
    transition: all var(--transition-base);
  }

  .feature-item:hover {
    transform: translateX(8px);
    box-shadow: var(--shadow-lg);
    border-color: var(--accent-color);
  }

  .feature-icon {
    flex-shrink: 0;
    width: 3rem;
    height: 3rem;
    background: linear-gradient(135deg, var(--accent-color) 0%, #059669 100%);
    border-radius: var(--radius-full);
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    box-shadow: var(--shadow-md);
    transition: all var(--transition-base);
  }

  .feature-item:hover .feature-icon {
    transform: scale(1.1);
    box-shadow: var(--shadow-lg);
  }

  .feature-content {
    flex: 1;
  }

  .feature-title {
    font-size: 1.125rem;
    font-weight: 700;
    color: var(--text-primary);
    margin-bottom: var(--space-xs);
  }

  .feature-description {
    font-size: 0.9rem;
    line-height: 1.6;
  }

  .about-image-container {
    position: relative;
    order: -1;
  }

  @media (min-width: 1024px) {
    .about-image-container {
      order: 1;
    }
  }

  .about-image {
    width: 100%;
    height: auto;
    transition: transform var(--transition-slow);
  }

  .about-image:hover {
    transform: scale(1.02);
  }

  .experience-badge {
    position: absolute;
    bottom: var(--space-xl);
    right: var(--space-xl);
    padding: var(--space-xl);
    text-align: center;
    backdrop-filter: blur(12px);
    border: 1px solid rgba(255, 255, 255, 0.2);
    transition: all var(--transition-base);
  }

  .experience-badge:hover {
    transform: scale(1.05);
    box-shadow: var(--shadow-2xl);
  }

  .badge-number {
    font-size: clamp(2rem, 5vw, 2.5rem);
    font-weight: 900;
    margin-bottom: var(--space-xs);
    letter-spacing: -0.02em;
  }

  .badge-text {
    font-size: 0.875rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  /* Staggered animations */
  .feature-item:nth-child(1) { animation-delay: 0.1s; }
  .feature-item:nth-child(2) { animation-delay: 0.2s; }
  .feature-item:nth-child(3) { animation-delay: 0.3s; }
  .feature-item:nth-child(4) { animation-delay: 0.4s; }

  /* Mobile responsiveness */
  @media (max-width: 768px) {
    .experience-badge {
      bottom: var(--space-lg);
      right: var(--space-lg);
      padding: var(--space-lg);
    }

    .feature-item {
      padding: var(--space-md);
    }

    .feature-icon {
      width: 2.5rem;
      height: 2.5rem;
    }
  }
</style>