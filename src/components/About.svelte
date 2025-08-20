<script>
  import { Check } from 'lucide-svelte';
  export let content;
</script>

<section id="about" class="about-section">
  <div class="about-container">
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
              <div class="feature-content">
                <h4 class="feature-title">{feature.title}</h4>
                <p class="feature-description">{feature.description}</p>
              </div>
            </div>
          {/each}
        </div>
      </div>
      
      <div class="about-image-container">
        <img src={content.about.image} alt="About Us" class="about-image" />
        <div class="experience-badge">
          <div class="badge-number">15+</div>
          <div class="badge-text">Years of Excellence</div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .about-section {
    padding: 4rem 0;
    background-color: #f9fafb;
  }

  .about-container {
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

  .about-grid {
    display: grid;
    gap: 4rem;
    align-items: center;
  }

  @media (min-width: 1024px) {
    .about-grid {
      grid-template-columns: 1fr 1fr;
    }
  }

  .about-description {
    font-size: 1.125rem;
    color: #4b5563;
    line-height: 1.6;
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
  }

  .feature-icon {
    flex-shrink: 0;
    width: 2.5rem;
    height: 2.5rem;
    background: linear-gradient(135deg, #10b981 0%, #059669 100%);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
  }

  .feature-content {
    flex: 1;
  }

  .feature-title {
    font-size: 1.125rem;
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 0.25rem;
  }

  .feature-description {
    font-size: 0.875rem;
    color: #4b5563;
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
    border-radius: 0.75rem;
    box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
  }

  .experience-badge {
    position: absolute;
    bottom: 2rem;
    right: 2rem;
    background-color: white;
    padding: 1.5rem;
    border-radius: 0.75rem;
    box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
    text-align: center;
  }

  .badge-number {
    font-size: 2.25rem;
    font-weight: bold;
    color: #2563eb;
    margin-bottom: 0.25rem;
  }

  .badge-text {
    font-size: 0.875rem;
    color: #4b5563;
  }
</style>