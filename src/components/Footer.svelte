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
      <div class="footer-brand">
        <h3 class="brand-name text-primary">{content.company.name}</h3>
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
          <input type="email" placeholder="Your email" class="newsletter-input form-input" />
          <button type="submit" class="btn btn-primary">
            Subscribe
          </button>
        </form>
      </div>
    </div>
    
    <div class="footer-bottom">
      <p class="copyright">{content.footer.copyright}</p>
      <button class="scroll-to-top btn-ghost rounded-full" on:click={scrollToTop}>
        <ArrowUp size={20} />
      </button>
    </div>
  </div>
</footer>

<style>
  .footer {
    background: linear-gradient(135deg, var(--text-primary) 0%, #1e293b 100%);
    color: white;
    padding-top: var(--space-4xl);
    padding-bottom: var(--space-xl);
    position: relative;
    overflow: hidden;
  }

  .footer::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(37, 99, 235, 0.5), transparent);
  }

  .footer-content {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: var(--space-2xl);
    margin-bottom: var(--space-2xl);
  }

  @media (min-width: 768px) {
    .footer-content {
      grid-template-columns: repeat(2, 1fr);
      gap: var(--space-3xl);
    }
  }

  @media (min-width: 1024px) {
    .footer-content {
      grid-template-columns: 1.5fr 1fr 1fr 1.2fr;
    }
  }

  .footer-brand {
    grid-column: span 1;
  }

  @media (min-width: 768px) and (max-width: 1023px) {
    .footer-brand {
      grid-column: span 2;
    }
  }

  .brand-name {
    font-size: 1.75rem;
    font-weight: 800;
    margin-bottom: var(--space-lg);
    letter-spacing: -0.01em;
  }

  .brand-description {
    line-height: 1.7;
    opacity: 0.9;
    margin-bottom: var(--space-xl);
    max-width: 20rem;
    color: rgba(255, 255, 255, 0.85);
  }

  .social-links {
    display: flex;
    gap: var(--space-md);
  }

  .social-link {
    width: 2.75rem;
    height: 2.75rem;
    background: rgba(37, 99, 235, 0.15);
    border: 1px solid rgba(37, 99, 235, 0.3);
    border-radius: var(--radius-lg);
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all var(--transition-base);
    text-decoration: none;
    color: white;
    backdrop-filter: blur(8px);
  }

  .social-link:hover {
    background: var(--primary-color);
    border-color: var(--primary-color);
    transform: translateY(-4px) scale(1.05);
    box-shadow: var(--shadow-lg);
  }

  .footer-section {
    display: flex;
    flex-direction: column;
  }

  .section-title {
    font-size: 1.125rem;
    font-weight: 700;
    margin-bottom: var(--space-lg);
    color: white;
    position: relative;
  }

  .section-title::after {
    content: '';
    position: absolute;
    bottom: -0.5rem;
    left: 0;
    width: 2rem;
    height: 2px;
    background: linear-gradient(90deg, var(--primary-color), var(--accent-color));
    border-radius: var(--radius-full);
  }

  .link-list {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
    gap: var(--space-sm);
  }

  .link-item {
    margin: 0;
  }

  .footer-link {
    color: rgba(255, 255, 255, 0.85);
    transition: all var(--transition-base);
    text-decoration: none;
    font-weight: 500;
    padding: var(--space-xs) 0;
    display: inline-block;
    position: relative;
  }

  .footer-link::before {
    content: '';
    position: absolute;
    left: 0;
    bottom: 0;
    width: 0;
    height: 1px;
    background: var(--primary-color);
    transition: width var(--transition-base);
  }

  .footer-link:hover {
    color: white;
    transform: translateX(4px);
  }

  .footer-link:hover::before {
    width: 100%;
  }

  .contact-list {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
    gap: var(--space-sm);
  }

  .contact-item {
    margin: 0;
    color: rgba(255, 255, 255, 0.85);
    font-weight: 500;
    padding: var(--space-xs) 0;
  }

  .newsletter-text {
    color: rgba(255, 255, 255, 0.85);
    margin-bottom: var(--space-lg);
    line-height: 1.6;
  }

  .newsletter-form {
    display: flex;
    flex-direction: column;
    gap: var(--space-md);
  }

  @media (min-width: 640px) {
    .newsletter-form {
      flex-direction: row;
    }
  }

  .newsletter-input {
    flex: 1;
    background: rgba(255, 255, 255, 0.08);
    border: 1px solid rgba(255, 255, 255, 0.2);
    color: white;
    backdrop-filter: blur(8px);
  }

  .newsletter-input::placeholder {
    color: rgba(255, 255, 255, 0.6);
  }

  .newsletter-input:focus {
    background: rgba(255, 255, 255, 0.12);
    border-color: var(--primary-color);
  }

  .newsletter-form .btn {
    white-space: nowrap;
  }

  .footer-bottom {
    padding-top: var(--space-xl);
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--space-lg);
  }

  @media (min-width: 640px) {
    .footer-bottom {
      flex-direction: row;
      justify-content: space-between;
    }
  }

  .copyright {
    color: rgba(255, 255, 255, 0.8);
    margin: 0;
    font-size: 0.9rem;
    font-weight: 500;
  }

  .scroll-to-top {
    width: 2.75rem;
    height: 2.75rem;
    background: rgba(37, 99, 235, 0.15);
    border: 1px solid rgba(37, 99, 235, 0.3);
    color: white;
    backdrop-filter: blur(8px);
    transition: all var(--transition-base);
  }

  .scroll-to-top:hover {
    background: var(--primary-color);
    border-color: var(--primary-color);
    transform: translateY(-4px);
    box-shadow: var(--shadow-lg);
  }

  /* Mobile responsive adjustments */
  @media (max-width: 768px) {
    .footer {
      padding-top: var(--space-3xl);
    }

    .footer-content {
      gap: var(--space-xl);
    }

    .social-links {
      justify-content: center;
    }

    .footer-section {
      text-align: center;
    }

    .section-title::after {
      left: 50%;
      transform: translateX(-50%);
    }
  }
</style>