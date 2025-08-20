<script>
  import { MapPin, Bed, Bath, Maximize } from 'lucide-svelte';
  export let content;
</script>

<section id="properties" class="properties-section">
  <div class="properties-container">
    <h2 class="section-title">{content.featuredProperties.title}</h2>
    <p class="section-subtitle">{content.featuredProperties.subtitle}</p>
    
    <div class="properties-grid">
      {#each content.featuredProperties.properties as property}
        <div class="property-card">
          <div class="property-image-container">
            <img src={property.image} alt={property.title} class="property-image" />
            <span class="property-type {property.type === 'For Sale' ? 'for-sale' : 'for-rent'}">
              {property.type}
            </span>
            {#if property.featured}
              <span class="featured-badge">
                Featured
              </span>
            {/if}
          </div>
          
          <div class="property-content">
            <h3 class="property-title">{property.title}</h3>
            <div class="property-location">
              <MapPin size={16} />
              <span>{property.location}</span>
            </div>
            
            <div class="property-features">
              <div class="feature-item">
                <Bed size={18} />
                <span>{property.beds} Beds</span>
              </div>
              <div class="feature-item">
                <Bath size={18} />
                <span>{property.baths} Baths</span>
              </div>
              <div class="feature-item">
                <Maximize size={18} />
                <span>{property.area}</span>
              </div>
            </div>
            
            <div class="property-footer">
              <div class="property-price">{property.price}</div>
              <button class="view-details-btn">
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
  .properties-section {
    padding: 4rem 0;
    background-color: #f9fafb;
  }

  .properties-container {
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

  .properties-grid {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 2rem;
  }

  @media (min-width: 768px) {
    .properties-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (min-width: 1024px) {
    .properties-grid {
      grid-template-columns: repeat(3, 1fr);
    }
  }

  .property-card {
    background-color: white;
    border-radius: 0.75rem;
    overflow: hidden;
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
    transition: all 0.3s ease;
  }

  .property-card:hover {
    box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
    transform: translateY(-4px);
  }

  .property-image-container {
    position: relative;
    height: 16rem;
    overflow: hidden;
  }

  .property-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
  }

  .property-card:hover .property-image {
    transform: scale(1.1);
  }

  .property-type {
    position: absolute;
    top: 1rem;
    left: 1rem;
    padding: 0.25rem 0.75rem;
    color: white;
    font-size: 0.875rem;
    font-weight: 500;
    border-radius: 0.375rem;
  }

  .for-sale {
    background-color: #2563eb;
  }

  .for-rent {
    background-color: #059669;
  }

  .featured-badge {
    position: absolute;
    top: 1rem;
    right: 1rem;
    padding: 0.25rem 0.75rem;
    background-color: #f59e0b;
    color: white;
    font-size: 0.875rem;
    font-weight: 500;
    border-radius: 0.375rem;
  }

  .property-content {
    padding: 1.5rem;
  }

  .property-title {
    font-size: 1.25rem;
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 0.5rem;
  }

  .property-location {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    color: #4b5563;
    font-size: 0.875rem;
    margin-bottom: 1rem;
  }

  .property-features {
    display: flex;
    gap: 1.5rem;
    padding: 1rem 0;
    border-top: 1px solid #e5e7eb;
    border-bottom: 1px solid #e5e7eb;
    margin-bottom: 1rem;
  }

  .feature-item {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    color: #4b5563;
    font-size: 0.875rem;
  }

  .property-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .property-price {
    font-size: 1.5rem;
    font-weight: bold;
    color: #2563eb;
  }

  .view-details-btn {
    padding: 0.5rem 1rem;
    border: 1px solid #2563eb;
    color: #2563eb;
    border-radius: 0.5rem;
    font-weight: 500;
    background-color: transparent;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .view-details-btn:hover {
    background-color: #2563eb;
    color: white;
  }
</style>