<script>
  import { Star, Quote } from 'lucide-svelte';
  export let content;
</script>

<section id="testimonials" class="section bg-light">
  <div class="container">
    <h2 class="section-title">{content.testimonials.title}</h2>
    <p class="section-subtitle">{content.testimonials.subtitle}</p>
    
    <div class="testimonials-grid">
      {#each content.testimonials.items as testimonial}
        <div class="testimonial-card">
          <div class="quote-icon">
            <Quote size={24} />
          </div>
          
          <div class="rating">
            {#each Array(testimonial.rating) as _}
              <Star size={18} fill="currentColor" />
            {/each}
          </div>
          
          <p class="testimonial-content">{testimonial.content}</p>
          
          <div class="testimonial-author">
            <img src={testimonial.image} alt={testimonial.name} class="author-image" />
            <div>
              <div class="author-name">{testimonial.name}</div>
              <div class="author-role">{testimonial.role}</div>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .bg-light {
    background: var(--bg-light);
  }
  
  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    gap: 2rem;
  }
  
  .testimonial-card {
    background: white;
    padding: 2rem;
    border-radius: var(--radius-lg);
    position: relative;
    transition: all 0.3s ease;
  }
  
  .testimonial-card:hover {
    transform: translateY(-5px);
    box-shadow: var(--shadow-lg);
  }
  
  .quote-icon {
    position: absolute;
    top: 1.5rem;
    right: 1.5rem;
    color: var(--primary-color);
    opacity: 0.2;
  }
  
  .rating {
    display: flex;
    gap: 0.25rem;
    color: #fbbf24;
    margin-bottom: 1rem;
  }
  
  .testimonial-content {
    color: var(--text-secondary);
    line-height: 1.8;
    margin-bottom: 1.5rem;
    font-style: italic;
  }
  
  .testimonial-author {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding-top: 1.5rem;
    border-top: 1px solid var(--border-color);
  }
  
  .author-image {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    object-fit: cover;
  }
  
  .author-name {
    font-weight: 600;
    color: var(--text-primary);
    margin-bottom: 0.25rem;
  }
  
  .author-role {
    font-size: 0.875rem;
    color: var(--text-secondary);
  }
  
  @media (max-width: 768px) {
    .testimonials-grid {
      grid-template-columns: 1fr;
    }
  }
</style>