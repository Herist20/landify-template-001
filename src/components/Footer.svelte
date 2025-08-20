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
  <div class="footer-container">
    <div class="footer-content">
      <div class="footer-brand">
        <h3 class="brand-name">{content.company.name}</h3>
        <p class="brand-description">{content.footer.description}</p>
        <div class="social-links">
          {#each content.footer.socialLinks as social}
            <a href={social.url} target="_blank" rel="noopener noreferrer" class="social-link">
              <svelte:component this={iconMap[social.platform]} size={20} />
            </a>
          {/each}
        </div>
      </div>
      
      <div class="footer-section">
        <h4 class="section-title">Quick Links</h4>
        <ul class="link-list">
          {#each content.footer.quickLinks as link}
            <li class="link-item">
              <a href={link.href} class="footer-link">{link.label}</a>
            </li>
          {/each}
        </ul>
      </div>
      
      <div class="footer-section">
        <h4 class="section-title">Contact Info</h4>
        <ul class="contact-list">
          <li class="contact-item">{content.company.phone}</li>
          <li class="contact-item">{content.company.email}</li>
          <li class="contact-item">{content.company.address}</li>
        </ul>
      </div>
      
      <div class="footer-section">
        <h4 class="section-title">Newsletter</h4>
        <p class="newsletter-text">Subscribe to get the latest property updates</p>
        <form class="newsletter-form">
          <input type="email" placeholder="Your email" class="newsletter-input" />
          <button type="submit" class="newsletter-button">
            Subscribe
          </button>
        </form>
      </div>
    </div>
    
    <div class="footer-bottom">
      <p class="copyright">{content.footer.copyright}</p>
      <button class="scroll-to-top" on:click={scrollToTop}>
        <ArrowUp size={20} />
      </button>
    </div>
  </div>
</footer>

<style>
  .footer {
    background: linear-gradient(135deg, #1e3a8a 0%, #1e40af 100%);
    color: white;
    padding-top: 4rem;
    padding-bottom: 2rem;
  }

  .footer-container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 1rem;
  }

  .footer-content {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 3rem;
    margin-bottom: 3rem;
  }

  @media (min-width: 768px) {
    .footer-content {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (min-width: 1024px) {
    .footer-content {
      grid-template-columns: repeat(4, 1fr);
    }
  }

  .footer-brand {
    grid-column: span 1;
  }

  @media (min-width: 1024px) {
    .footer-brand {
      grid-column: span 1;
    }
  }

  .brand-name {
    font-size: 1.5rem;
    font-weight: bold;
    margin-bottom: 1rem;
  }

  .brand-description {
    line-height: 1.6;
    opacity: 0.9;
    margin-bottom: 1.5rem;
  }

  .social-links {
    display: flex;
    gap: 1rem;
  }

  .social-link {
    width: 2.5rem;
    height: 2.5rem;
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;
    text-decoration: none;
    color: inherit;
  }

  .social-link:hover {
    background-color: rgba(255, 255, 255, 0.2);
    transform: translateY(-4px);
  }

  .footer-section {
    display: flex;
    flex-direction: column;
  }

  .section-title {
    font-size: 1.125rem;
    font-weight: 600;
    margin-bottom: 1.5rem;
  }

  .link-list {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
  }

  .link-item {
    margin: 0;
  }

  .footer-link {
    opacity: 0.9;
    transition: opacity 0.2s ease;
    text-decoration: none;
    color: inherit;
  }

  .footer-link:hover {
    opacity: 0.7;
  }

  .contact-list {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
    opacity: 0.9;
  }

  .contact-item {
    margin: 0;
  }

  .newsletter-text {
    opacity: 0.9;
    margin-bottom: 1rem;
  }

  .newsletter-form {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .newsletter-input {
    padding: 0.75rem 1rem;
    border-radius: 0.5rem;
    background-color: rgba(255, 255, 255, 0.1);
    border: none;
    color: white;
    font-size: 1rem;
    transition: all 0.2s ease;
  }

  .newsletter-input::placeholder {
    color: rgba(255, 255, 255, 0.7);
  }

  .newsletter-input:focus {
    outline: none;
    background-color: rgba(255, 255, 255, 0.2);
  }

  .newsletter-button {
    padding: 0.75rem 1.5rem;
    background-color: #16a34a;
    color: white;
    border: none;
    border-radius: 0.5rem;
    font-weight: 500;
    cursor: pointer;
    transition: background-color 0.2s ease;
  }

  .newsletter-button:hover {
    background-color: #15803d;
  }

  .footer-bottom {
    padding-top: 2rem;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
  }

  @media (min-width: 640px) {
    .footer-bottom {
      flex-direction: row;
      justify-content: space-between;
    }
  }

  .copyright {
    opacity: 0.9;
    margin: 0;
  }

  .scroll-to-top {
    width: 2.5rem;
    height: 2.5rem;
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 50%;
    border: none;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .scroll-to-top:hover {
    background-color: rgba(255, 255, 255, 0.2);
    transform: translateY(-4px);
  }
</style>