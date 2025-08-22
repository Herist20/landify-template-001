<script>
  import { Star, Quote } from 'lucide-svelte';
  export let content;
</script>

<section id="testimonials" class="section bg-primary">
  <div class="container">
    <div class="section-header">
      <h2 class="section-title">{content.testimonials.title}</h2>
      <p class="section-subtitle">{content.testimonials.subtitle}</p>
    </div>
    
    <div class="grid grid-cols-3">
      {#each content.testimonials.items as testimonial}
        <div class="testimonial-card card animate-fadeIn">
          <div class="quote-icon">
            <Quote size={24} />
          </div>
          
          <div class="rating">
            {#each Array(testimonial.rating) as _}
              <Star size={18} fill="currentColor" />
            {/each}
          </div>
          
          <p class="testimonial-content card-text">{testimonial.content}</p>
          
          <div class="testimonial-author">
            <img src={testimonial.image} alt={testimonial.name} class="author-image rounded-full shadow-md" />
            <div class="author-info">
              <div class="author-name">{testimonial.name}</div>
              <div class="author-role text-muted">{testimonial.role}</div>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .testimonial-card {
    padding: var(--space-2xl);
    position: relative;
    border: 1px solid var(--border-light);
    transition: all var(--transition-base);
    background: linear-gradient(135deg, var(--bg-primary) 0%, rgba(248, 250, 252, 0.8) 100%);
  }

  .testimonial-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(90deg, var(--primary-color), var(--accent-color), #f59e0b);
    opacity: 0;
    transition: opacity var(--transition-base);
  }

  .testimonial-card:hover::before {
    opacity: 1;
  }

  .testimonial-card:hover {
    transform: translateY(-8px) scale(1.02);
    box-shadow: var(--shadow-2xl);
    border-color: var(--primary-color);
    background: linear-gradient(135deg, var(--bg-primary) 0%, rgba(37, 99, 235, 0.02) 100%);
  }

  .quote-icon {
    position: absolute;
    top: var(--space-lg);
    right: var(--space-lg);
    color: var(--primary-color);
    opacity: 0.15;
    transition: all var(--transition-base);
  }

  .testimonial-card:hover .quote-icon {
    opacity: 0.3;
    transform: scale(1.1);
  }

  .rating {
    display: flex;
    gap: var(--space-xs);
    color: #fbbf24;
    margin-bottom: var(--space-lg);
  }

  .rating svg {
    transition: transform var(--transition-fast);
  }

  .testimonial-card:hover .rating svg {
    transform: scale(1.1);
  }

  .testimonial-content {
    line-height: 1.7;
    margin-bottom: var(--space-xl);
    font-style: italic;
    font-size: 0.95rem;
    position: relative;
  }

  .testimonial-content::before {
    content: '"';
    position: absolute;
    left: -0.5rem;
    top: -0.25rem;
    font-size: 3rem;
    color: var(--primary-color);
    opacity: 0.2;
    font-family: Georgia, serif;
  }

  .testimonial-author {
    display: flex;
    align-items: center;
    gap: var(--space-lg);
    padding-top: var(--space-xl);
    border-top: 1px solid var(--border-color);
  }

  .author-image {
    width: 3.5rem;
    height: 3.5rem;
    object-fit: cover;
    transition: all var(--transition-base);
    border: 2px solid transparent;
  }

  .testimonial-card:hover .author-image {
    border-color: var(--primary-color);
    transform: scale(1.1);
  }

  .author-info {
    flex: 1;
  }

  .author-name {
    font-weight: 700;
    color: var(--text-primary);
    font-size: 1rem;
    margin-bottom: var(--space-xs);
  }

  .author-role {
    font-size: 0.875rem;
    font-weight: 500;
  }

  /* Animation delays for staggered effect */
  .testimonial-card:nth-child(1) { animation-delay: 0.1s; }
  .testimonial-card:nth-child(2) { animation-delay: 0.2s; }
  .testimonial-card:nth-child(3) { animation-delay: 0.3s; }
  .testimonial-card:nth-child(4) { animation-delay: 0.4s; }
  .testimonial-card:nth-child(5) { animation-delay: 0.5s; }
  .testimonial-card:nth-child(6) { animation-delay: 0.6s; }

  /* Mobile responsiveness */
  @media (max-width: 768px) {
    .testimonial-card {
      padding: var(--space-xl);
    }

    .author-image {
      width: 3rem;
      height: 3rem;
    }

    .testimonial-content::before {
      font-size: 2.5rem;
      left: -0.4rem;
      top: -0.2rem;
    }
  }
</style>