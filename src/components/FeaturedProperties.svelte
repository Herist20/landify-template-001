<script>
  import { MapPin, Bed, Bath, Maximize } from 'lucide-svelte';
  export let content;
</script>

<section id="properties" class="section">
  <div class="container">
    <h2 class="section-title">{content.featuredProperties.title}</h2>
    <p class="section-subtitle">{content.featuredProperties.subtitle}</p>
    
    <div class="properties-grid">
      {#each content.featuredProperties.properties as property}
        <div class="property-card card">
          <div class="property-image">
            <img src={property.image} alt={property.title} />
            <span class="property-badge" class:sale={property.type === 'For Sale'}>
              {property.type}
            </span>
            {#if property.featured}
              <span class="featured-badge">Featured</span>
            {/if}
          </div>
          
          <div class="property-content">
            <h3 class="property-title">{property.title}</h3>
            <div class="property-location">
              <MapPin size={16} />
              <span>{property.location}</span>
            </div>
            
            <div class="property-features">
              <div class="feature">
                <Bed size={18} />
                <span>{property.beds} Beds</span>
              </div>
              <div class="feature">
                <Bath size={18} />
                <span>{property.baths} Baths</span>
              </div>
              <div class="feature">
                <Maximize size={18} />
                <span>{property.area}</span>
              </div>
            </div>
            
            <div class="property-footer">
              <div class="property-price">{property.price}</div>
              <button class="btn-view">View Details</button>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .properties-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
    gap: 2rem;
  }
  
  .property-card {
    transition: transform 0.3s ease;
  }
  
  .property-card:hover {
    transform: translateY(-5px);
  }
  
  .property-image {
    position: relative;
    height: 250px;
    overflow: hidden;
  }
  
  .property-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
  }
  
  .property-card:hover .property-image img {
    transform: scale(1.1);
  }
  
  .property-badge {
    position: absolute;
    top: 1rem;
    left: 1rem;
    padding: 0.25rem 0.75rem;
    background: var(--secondary-color);
    color: white;
    border-radius: var(--radius-sm);
    font-size: 0.875rem;
    font-weight: 500;
  }
  
  .property-badge.sale {
    background: var(--primary-color);
  }
  
  .featured-badge {
    position: absolute;
    top: 1rem;
    right: 1rem;
    padding: 0.25rem 0.75rem;
    background: #f59e0b;
    color: white;
    border-radius: var(--radius-sm);
    font-size: 0.875rem;
    font-weight: 500;
  }
  
  .property-content {
    padding: 1.5rem;
  }
  
  .property-title {
    font-size: 1.25rem;
    font-weight: 600;
    margin-bottom: 0.5rem;
    color: var(--text-primary);
  }
  
  .property-location {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    color: var(--text-secondary);
    font-size: 0.875rem;
    margin-bottom: 1rem;
  }
  
  .property-features {
    display: flex;
    gap: 1.5rem;
    padding: 1rem 0;
    border-top: 1px solid var(--border-color);
    border-bottom: 1px solid var(--border-color);
    margin-bottom: 1rem;
  }
  
  .feature {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    color: var(--text-secondary);
    font-size: 0.875rem;
  }
  
  .property-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .property-price {
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--primary-color);
  }
  
  .btn-view {
    padding: 0.5rem 1rem;
    background: transparent;
    color: var(--primary-color);
    border: 1px solid var(--primary-color);
    border-radius: var(--radius-sm);
    cursor: pointer;
    transition: all 0.3s ease;
    font-weight: 500;
  }
  
  .btn-view:hover {
    background: var(--primary-color);
    color: white;
  }
  
  @media (max-width: 768px) {
    .properties-grid {
      grid-template-columns: 1fr;
    }
  }
</style>