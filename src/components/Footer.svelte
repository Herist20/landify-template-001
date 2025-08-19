<script>
  import { Facebook, Twitter, Linkedin, Instagram, ArrowUp } from 'lucide-svelte';
  export let content;
  
  const iconMap = {
    'Facebook': Facebook,
    'Twitter': Twitter,
    'LinkedIn': Linkedin,
    'Instagram': Instagram
  };
  
  function scrollToTop() {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }
</script>

<footer class="footer">
  <div class="container">
    <div class="footer-content">
      <div class="footer-section">
        <h3 class="footer-logo">{content.company.name}</h3>
        <p class="footer-description">{content.footer.description}</p>
        <div class="social-links">
          {#each content.footer.socialLinks as social}
            <a href={social.url} target="_blank" rel="noopener noreferrer" class="social-link">
              <svelte:component this={iconMap[social.platform]} size={20} />
            </a>
          {/each}
        </div>
      </div>
      
      <div class="footer-section">
        <h4 class="footer-title">Quick Links</h4>
        <ul class="footer-links">
          {#each content.footer.quickLinks as link}
            <li>
              <a href={link.href}>{link.label}</a>
            </li>
          {/each}
        </ul>
      </div>
      
      <div class="footer-section">
        <h4 class="footer-title">Contact Info</h4>
        <ul class="footer-contact">
          <li>{content.company.phone}</li>
          <li>{content.company.email}</li>
          <li>{content.company.address}</li>
        </ul>
      </div>
      
      <div class="footer-section">
        <h4 class="footer-title">Newsletter</h4>
        <p class="newsletter-text">Subscribe to get the latest property updates</p>
        <form class="newsletter-form">
          <input type="email" placeholder="Your email" class="newsletter-input" />
          <button type="submit" class="newsletter-button">Subscribe</button>
        </form>
      </div>
    </div>
    
    <div class="footer-bottom">
      <p>{content.footer.copyright}</p>
      <button class="scroll-top" on:click={scrollToTop}>
        <ArrowUp size={20} />
      </button>
    </div>
  </div>
</footer>

<style>
  .footer {
    background: linear-gradient(135deg, #1e3a8a, #1e40af);
    color: white;
    padding: 4rem 0 2rem;
  }
  
  .footer-content {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 2fr;
    gap: 3rem;
    margin-bottom: 3rem;
  }
  
  .footer-logo {
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 1rem;
  }
  
  .footer-description {
    line-height: 1.6;
    opacity: 0.9;
    margin-bottom: 1.5rem;
  }
  
  .social-links {
    display: flex;
    gap: 1rem;
  }
  
  .social-link {
    width: 40px;
    height: 40px;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    transition: all 0.3s ease;
  }
  
  .social-link:hover {
    background: rgba(255, 255, 255, 0.2);
    transform: translateY(-3px);
  }
  
  .footer-title {
    font-size: 1.125rem;
    font-weight: 600;
    margin-bottom: 1.5rem;
  }
  
  .footer-links,
  .footer-contact {
    list-style: none;
  }
  
  .footer-links li,
  .footer-contact li {
    margin-bottom: 0.75rem;
    opacity: 0.9;
  }
  
  .footer-links a {
    color: white;
    text-decoration: none;
    transition: opacity 0.3s ease;
  }
  
  .footer-links a:hover {
    opacity: 0.7;
  }
  
  .newsletter-text {
    margin-bottom: 1rem;
    opacity: 0.9;
  }
  
  .newsletter-form {
    display: flex;
    gap: 0.5rem;
  }
  
  .newsletter-input {
    flex: 1;
    padding: 0.75rem;
    border: none;
    border-radius: var(--radius-sm);
    background: rgba(255, 255, 255, 0.1);
    color: white;
  }
  
  .newsletter-input::placeholder {
    color: rgba(255, 255, 255, 0.6);
  }
  
  .newsletter-button {
    padding: 0.75rem 1.5rem;
    background: var(--secondary-color);
    color: white;
    border: none;
    border-radius: var(--radius-sm);
    font-weight: 500;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  
  .newsletter-button:hover {
    background: #059669;
  }
  
  .footer-bottom {
    padding-top: 2rem;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .scroll-top {
    width: 40px;
    height: 40px;
    background: rgba(255, 255, 255, 0.1);
    border: none;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  
  .scroll-top:hover {
    background: rgba(255, 255, 255, 0.2);
    transform: translateY(-3px);
  }
  
  @media (max-width: 768px) {
    .footer-content {
      grid-template-columns: 1fr;
      gap: 2rem;
    }
    
    .newsletter-form {
      flex-direction: column;
    }
  }
</style>