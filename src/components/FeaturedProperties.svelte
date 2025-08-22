<script>
  import { MapPin, Bed, Bath, Maximize } from 'lucide-svelte';
  export let content;
</script>

<section id="properties" class="section bg-secondary">
  <div class="container">
    <div class="section-header">
      <h2 class="section-title">{content.featuredProperties.title}</h2>
      <p class="section-subtitle">{content.featuredProperties.subtitle}</p>
    </div>
    
    <div class="grid grid-cols-3">
      {#each content.featuredProperties.properties as property}
        <div class="card property-card animate-fadeIn">
          <div class="card-image">
            <img src={property.image} alt={property.title} />
            <span class="property-type badge {property.type === 'For Sale' ? 'badge-primary' : 'badge-success'}">
              {property.type}
            </span>
            {#if property.featured}
              <span class="featured-badge badge badge-warning">
                Featured
              </span>
            {/if}
          </div>
          
          <div class="card-body">
            <h3 class="card-title">{property.title}</h3>
            <div class="property-location text-muted">
              <MapPin size={16} />
              <span>{property.location}</span>
            </div>
            
            <div class="property-features">
              <div class="feature-item text-muted">
                <Bed size={18} />
                <span>{property.beds} Beds</span>
              </div>
              <div class="feature-item text-muted">
                <Bath size={18} />
                <span>{property.baths} Baths</span>
              </div>
              <div class="feature-item text-muted">
                <Maximize size={18} />
                <span>{property.area}</span>
              </div>
            </div>
            
            <div class="property-footer">
              <div class="property-price text-primary">{property.price}</div>
              <button class="btn btn-outline">
                View Details
              </button>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .property-card {
    transition: all var(--transition-base);
    position: relative;
    overflow: hidden;
  }

  .property-card:hover {
    transform: translateY(-6px);
    box-shadow: var(--shadow-2xl);
  }

  .property-type {
    position: absolute;
    top: var(--space-lg);
    left: var(--space-lg);
    z-index: 10;
  }

  .featured-badge {
    position: absolute;
    top: var(--space-lg);
    right: var(--space-lg);
    z-index: 10;
  }

  .property-location {
    display: flex;
    align-items: center;
    gap: var(--space-xs);
    font-size: 0.875rem;
    margin-bottom: var(--space-lg);
  }

  .property-features {
    display: flex;
    gap: var(--space-lg);
    padding: var(--space-lg) 0;
    border-top: 1px solid var(--border-color);
    border-bottom: 1px solid var(--border-color);
    margin-bottom: var(--space-lg);
  }

  @media (max-width: 640px) {
    .property-features {
      flex-wrap: wrap;
      gap: var(--space-md);
    }
  }

  .feature-item {
    display: flex;
    align-items: center;
    gap: var(--space-xs);
    font-size: 0.875rem;
    font-weight: 500;
  }

  .property-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: var(--space-md);
  }

  .property-price {
    font-size: 1.5rem;
    font-weight: 800;
    letter-spacing: -0.02em;
  }

  /* Animation delays for staggered effect */
  .property-card:nth-child(1) { animation-delay: 0.1s; }
  .property-card:nth-child(2) { animation-delay: 0.2s; }
  .property-card:nth-child(3) { animation-delay: 0.3s; }
  .property-card:nth-child(4) { animation-delay: 0.4s; }
  .property-card:nth-child(5) { animation-delay: 0.5s; }
  .property-card:nth-child(6) { animation-delay: 0.6s; }

  /* Special hover effect for property images */
  .property-card:hover :global(.card-image img) {
    transform: scale(1.08);
  }

  /* Improved responsive design */
  @media (max-width: 768px) {
    .property-footer {
      flex-direction: column;
      align-items: stretch;
      gap: var(--space-md);
    }

    .property-footer .btn {
      width: 100%;
      justify-content: center;
    }
  }
</style>