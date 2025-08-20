<script>
  import { Star, Quote } from 'lucide-svelte';
  export let content;
</script>

<section id="testimonials" class="testimonials-section">
  <div class="testimonials-container">
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
            <div class="author-info">
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
  .testimonials-section {
    padding: 4rem 0;
    background-color: white;
  }

  .testimonials-container {
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

  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 2rem;
  }

  @media (min-width: 768px) {
    .testimonials-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (min-width: 1024px) {
    .testimonials-grid {
      grid-template-columns: repeat(3, 1fr);
    }
  }

  .testimonial-card {
    background-color: #f9fafb;
    padding: 2rem;
    border-radius: 0.75rem;
    position: relative;
    transition: all 0.3s ease;
  }

  .testimonial-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
  }

  .quote-icon {
    position: absolute;
    top: 1.5rem;
    right: 1.5rem;
    color: #2563eb;
    opacity: 0.2;
  }

  .rating {
    display: flex;
    gap: 0.25rem;
    color: #fbbf24;
    margin-bottom: 1rem;
  }

  .testimonial-content {
    color: #4b5563;
    line-height: 1.6;
    margin-bottom: 1.5rem;
    font-style: italic;
  }

  .testimonial-author {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding-top: 1.5rem;
    border-top: 1px solid #e5e7eb;
  }

  .author-image {
    width: 3rem;
    height: 3rem;
    border-radius: 50%;
    object-fit: cover;
  }

  .author-name {
    font-weight: 600;
    color: #1f2937;
  }

  .author-role {
    font-size: 0.875rem;
    color: #4b5563;
  }
</style>